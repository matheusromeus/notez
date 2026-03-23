
dev frontend URL - https://heritage-dev.varshealth.com/
prod frontend URL - https://admin.heritage-communities.com/

main components in the architecture
- dashboard UI
- dashboard API
- data pipeline
- relational database (common)

https://danieldonbavand.com/2022/03/08/what-is-a-control-and-data-plane-architecture/

## data pipeline

### function A

what function A does
- Load all active communities from the DB
For each community
- Resolve SRFax credentials via Key Vault
- Periodically poll SRFax API (every x minutes)
- Detect new faxes only
- Normalise each fax into **one logical item**
- Emit one event per fax
- Each fax is placed **individually** into an Azure queue.

```
FAX_RECEIVED
{
  fax_id,
  received_at,
  source = "srfax",
  pdf_location (temporary or blob),
  checksum
}
```

**problem no.1 - it is not possible to detect whether the fax is unprocess until function B** because function A is a timer trigger which is not horizontally scalable, so we need to keep the run time to a minimum. it will stop execution if the next run starts.

we'll create a ingestion_run entry -> to find out how long the fetching took, and how many faxes were fetched, and if any errors, log it, store it. 

doubt - how can i emit an event from the function app?

extra - what are the failure points here?
- Retry with backoff
- 

we are fetching only unread faxes in that current day.

```
INGESTION_RUN_STARTED
{
  run_id,
  started_at,
  poll_window_start,
  poll_window_end
}
```

after fetch
```
INGESTION_RUN_COMPLETED
{
  run_id,
  ended_at,
  faxes_seen_count,
  faxes_enqueued_count,
  api_latency_ms,
  errors_count,
  partial_failure = true|false
}
```
### function B

triggered by 
- Queue message (`FAX_RECEIVED`)

what function B does
- validate PDF (size, corruption, format)
- check for duplicate pdfs
- upload to Sharepoint

On Success:
```
FAX_VALIDATED
FAX_UPLOADED
{
  fax_id,
  sharepoint_url,
  validation_metrics,
  upload_latency_ms
}
```

On Failure:
```
FAX_REJECTED
{
  fax_id,
  reason,
  failure_stage = "validation|upload"
}
```

Doubt 
- do we need a DLQ here?
- who is consuming the different events?

extra - need to confirm what all the final contents of the queue message is

### function C - AI

Triggered by:
- Queue message with SharePoint URL

what function C does
- fetch the document
- do OCR
- call the LLM
- classify into a community

```
LLM_CALL_STARTED
LLM_CALL_COMPLETED
FAX_CLASSIFIED
{
  fax_id,
  community_id,
  model_name,
  token_usage,
  latency_ms,
  confidence
}
```

Failures
```
LLM_CALL_FAILED
FAX_CLASSIFICATION_FAILED
```

Capture actual token usage from the provider response




what are we gonna use the db for?
- store the faxes we got
- ingestion runs
- classification results


Do NOT store API keys directly in the database.
community_srfax_config
{
  community_id
  srfax_account_id
  key_vault_secret_ref
  polling_window_minutes
  is_active
}
The DB stores **references**, not secrets.

# DB Schema

## ingestion_run ✅
- id (PK)
- started_at
- completed_at
- fetched_count
- status
- error_details
- created_at
Index on `(status, started_at DESC)`
## community ✅
- id (PK)
- name
- fax_number
- access_id_secret_ref
- password_secret_ref
- sharepoint_base_folder
- is_active
- notification_frequency
- email_is_enabled
- created_at
- updated_at
- is_deleted (soft delete)
## fax_document ✅
- id (PK)
- ingestion_run_id (FK → ingestion_run.id)
- community_id (FK → community.id)
- srfax_id
- file_path
- page_count
- received_at
- created_at
Index(community_id, received_at DESC)
## workflow ✅
- id (PK)
- fax_document_id (FK → fax_document.id)
- status
- started_at
- completed_at
- error_details
- sharepoint_url
- is_manual
- created_at
- updated_at
Index(status, created_at DESC)
## workflow_trail ✅
- id (PK)
- workflow_id (FK)
- status
- updated_at
- error_details
Index:
- `(workflow_id, updated_at DESC)`
## model ✅
- id (PK)
- provider
- model_name
- display_name
- description
- is_active
- updated_at
## model_pricing ✅
- id (PK)
- model_id (FK → model.id)
- input_cost_per_million
- output_cost_per_million
- currency
- effective_from
Index(model_id, effective_from DESC)
## provider_credential ✅
API key abstraction.
- id (PK)
- provider
- secret_ref
- is_active
- created_at
Index(provider, is_active)
## model_invocation
- id (PK)
- workflow_id (FK → workflow.id)
- model_id (FK → model.id)
- provider_credential_id (FK → provider_credential.id)
- invocation_type (ocr, classification, extraction)
- input_tokens_used
- input_tokens_cost
- output_tokens_used
- output_tokens_cost
- result_json (JSONB)
- total_cost
- error_details
- created_at
Index(workflow_id)
Index(created_at DESC)
## community_notification_recipient ✅
- id (PK)
- community_id (FK → community.id)
- email
- name (optional)
- is_active
- created_at
- updated_at

## Add unique constraints:
- fax_document.srfax_id → UNIQUE
- model_pricing (model_id, effective_from) → UNIQUE
- community_notification_recipient (community_id, email) → UNIQUE




1. first create the ingestion run
2. update the ingestion run with how many faxes were fetched and status
3. for each fax returned, insert into fax document and put it in queue

in process fax,
4. for each fax, a workflow record will be created.
5. add to workflow trail too for the same workflow record
6. update the sharepoint url

ai 
6. call models and insert into model_invocation
	1. if failed, populate error_details
	2. move workflow & workflow_trail to failed




data-pipeline
- [x] not saving page count, remote id and callerid in fax_document
	- [x] have to send the pages along with the queue message
- [x] update the final url in the data pipeline
- [x] is the data pipeline taking from the database?
	- [x] community (SRFax)
- [x] updating workfow status to manual or success or failed
	- classified -> success
	- exception -> failed
	- is_manual is True? -> manual
- [x] multi community picking up
	- [x] add the new srfax account aditya@tericsoft.com, theimm0rtal$2026
- [x] email summary engine
	- [x] summary is stored for dev purposes now. result_json wont have the summary in prod
- [x] add back the duplicate check for faxes
- [x] check if search is working

control plane
- [x] no horizontal scrolling for document management screen
- [x] add more filters like in the super engineer screen
- [x] Fix the workflow status, which is currently showing as zero. manual and success. and failed
- [x] remove srfaxid
- [x] flag option in document management - flag a classification as incorrect and can be updated. with optional remarks.
- [x] on changing the flag, file should be moved from one folder to the new one
- [x] email frequency control
	- [x] per_fax
	- [x] value of 'x' hours
- [x] add From Fax# / Remote ID

- [x] what is the manual folder path? - Other & Uncategorized
- [x] completed (change to classified) - classified & is_manual = false
- [x] change manual to override (red)
- [x] while adding model, input token cost is not needed
- [x] configured ai models no horizontal scroll
- [x] model verification
- [x] env issue, navan take from dinesh



- [x] only use text models
- [x] check the second community
- [x] manual custom hours
- [ ] learn about how the email triggering and filtering by sessions work?
- [ ] do the exceptions go back in the queue?
- [x] login screen
- [x] set is_manual to true when the classification is Other & Uncategorised
- [x] from fax/remote id add to detailed view
- [ ] mismatch between provider selected model, active status etc
- [ ] monorepo function deployment


- [x] implement the password protection (need to change AUTH-enabled to  prod)
- [ ] sharepoint verification
- [x] not able to manually override the fax (only change the name) (graph api permissions)
- [x] no multiple folders, only one folders
- [x] new filename has to be changed when manual overriden
- [x] 1.UI change in login page
- [x] 2.redirecting to login page once session is ended..

ssr + csr if we can

verify llm, azure should take extra params
1. email fix

2.sharepoint path hard coded,able to add from ui.

3.while editing community, we are asking srfax credentials again.

4. Able to verify srfax and SharePoint even though we are giving wrong credentials and path.


until ai-fax, hard code it.

renaming is not working

[[sharepoint_env]]

#

Here’s what’s causing the latency and how to improve it.

---

## Why the app feels slow

### 1. **Double round-trip when opening the app (/)**

- You hit `/` → server runs `isAuthenticated()` → **one request** to backend `GET /auth/me` (and DB).
- Then `redirect("/dashboard")` → **second request** to load `/dashboard` → **another request** to backend `GET /api/dashboard`.

So a single “open app” flow does **two full server round-trips** (auth then dashboard), and the user waits for both before seeing the dashboard.

### 2. **Backend: many sequential DB queries**

In `heritage-backend/app/api/dashboard.py`, `GET /api/dashboard` does everything one after the other:

```165:167:heritage-backend/app/api/dashboard.py
    communities = await list_communities(db=db)
    metrics = await get_dashboard_metrics(community_id=community_id, db=db)
    system_overview = await get_system_overview(db=db)
```

- `list_communities` → 1 query  
- `get_dashboard_metrics` → **6 queries** (doc count, workflow counts, failed, cost, OCR avg, classification avg), all `await`ed in sequence  
- `get_system_overview` → 2 queries  

So the backend does **9+ sequential DB round-trips** per dashboard load. That adds up quickly (e.g. 9 × 5–20 ms each).

### 3. **No streaming**

- The dashboard page waits for the **entire** server render and backend response before sending HTML.
- `loading.tsx` shows a spinner, but the first byte of real content is delayed until all data is ready.

### 4. **No caching**

- `force-dynamic` on every route → no static or cached HTML.
- Auth is checked with a live `/auth/me` call when you hit `/`.
- No `fetch` caching or short-lived cache for dashboard data, so every navigation can trigger full backend work again.

### 5. **Server-side `cookies()` on every request**

- Each server-side `apiGet` (and similar) calls `getServerCookieHeader()` → `cookies()`, which in Next.js is async and adds a bit of overhead on every request.

---

## Changes that will help most

1. **Backend: run dashboard work in parallel**  
   In `get_dashboard` run the three pieces in parallel, e.g. `asyncio.gather(list_communities(...), get_dashboard_metrics(...), get_system_overview(...))`, so you get one “round” of DB work instead of 3 sequential steps. Optionally parallelize the 6 queries inside `get_dashboard_metrics` where safe (e.g. with `gather` or a small helper).

2. **Avoid the double round-trip from `/`**  
   - Either: make `/` immediately redirect to `/dashboard` (or login) **without** calling the backend (e.g. redirect in middleware or a very light page that only reads the cookie and redirects), and do the real auth check only on `/dashboard` (and other protected routes).  
   - Or: if you keep auth on `/`, at least ensure `/dashboard` doesn’t redundantly re-validate in a way that blocks first paint (e.g. auth in layout vs page, or do auth in parallel with data).

3. **Use streaming where possible**  
   Send the shell (layout + loading state) immediately and stream in the dashboard data (e.g. Suspense + async component or a route that streams the slow part). That way the user sees the app and a loading state instead of a blank wait.

4. **Optional: short-lived cache for dashboard data**  
   For example cache `getDashboardData` (or the backend response) for 10–30 seconds so repeat visits or refreshes don’t always hit the backend and all 9 queries.

5. **Keep an eye on DB**  
   Add indexes for the columns used in dashboard filters/aggregations (e.g. `community_id`, status, `invocation_type`, JSON keys used in `result_json`) so each of those 9 queries stays fast.

If you tell me whether you prefer to optimize the backend first, the frontend first, or both, I can suggest concrete code changes (e.g. exact `asyncio.gather` and route/middleware edits) next.

# to do

- [x] time inside the detail page was in IST
- [x] rename pdf along with timestamp
- [x] change folder path in email
- [x] add from address in the email.

- [ ] some are still not renamed, just need to add seconds
- [ ] the folder shows 404
- [ ] attach file
- [ ] all are set to is_manual

https://hmscare.sharepoint.com/sites/AIFax/Shared Documents/AI%20Fax/Ridgewood%20(RW)


![[Pasted image 20260323125239.png]]


- [ ] new classifications and prompt CRUD


https://hmscare.sharepoint.com/sites/AIFax/Documents/AI%20Fax/Ridgewood%20(RW)