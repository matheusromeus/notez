
frontend URL - https://heritage-dev.varshealth.com/

main components in the architecture
- frontend
- backend
- data pipeline
- storage + messaging (db & queues)

if the data pipeline is a monorepo, the db access and other code can be shared.

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



todos
- [ ] sharepoint verification
- [ ] srfax verification
- [ ] monorepo function deployment
- [ ] email rnd
- [ ] we are not showing the final fax folder
- [ ] is the data pipeline taking from the database? 
	- [ ] community (SRFax)
	- [ ] model
	- [ ] 
- [ ] should keep the cost also part of the same table
