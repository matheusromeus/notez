sharepoint creds are constant
- client id, client secret, password, tenant_id, username


1. fetch-fax-inbox
2. process-fax
3. ai-process
4. ai-subscriber

2.

**process-fax-v2**
```
SHAREPOINT_FOLDER_PATH - AI Fax/Heritage Ridge (HR)/Processing
SHAREPOINT_SITE_URL - https://hmscare.sharepoint.com/sites/AIFax
```

**process-fax-dev**

```
SHAREPOINT_FOLDER_PATH - /Operations Library/AI Fax/Heritage Ridge (HR)/Processing
SHAREPOINT_SITE_URL - https://hmscare.sharepoint.com
```


ai-process-v2
```
SHAREPOINT_FOLDER_PATH - AI Fax/Heritage Ridge (HR)/Processing
SHAREPOINT_BASE_URL - https://hmscare.sharepoint.com/sites/AIFax
```

ai-process-dev
```
SHAREPOINT_FOLDER_PATH - Operations Library/AI Fax/Heritage Ridge (HR)/Manual Review
SHAREPOINT_SITE_URL - https://hmscare.sharepoint.com
```


ai-subscriber-v2
```
SHAREPOINT_BASE_FOLDER_PATH - /Shared Documents/AI Fax/Heritage Ridge (HR)
SHAREPOINT_SITE_URL - https://hmscare.sharepoint.com/sites/AIFax
SOURCE_FOLDER - /processing
COMPLETED_FOLDER - /Completed
FAILED_FOLDER - /Failed
```

ai-subscriber-dev
```
SHAREPOINT_BASE_FOLDER_PATH - /Operations Library/AI Fax/Heritage Ridge (HR)
SHAREPOINT_SITE_URL - https://hmscare.sharepoint.com
SOURCE_FOLDER - /processing-dev
COMPLETED_FOLDER - /Completed-dev
FAILED_FOLDER - /Failed-dev
```


Available Drives - Documents

Skol2025

Login OTP Template
Your BookMyBand account login OTP is {#var#}. Do not share this OTP with anyone.- BookMyBand

Signup OTP Template
Dear {#var#}, your BookMyBand signup OTP is {#var#}. It is valid for {#var#} minutes. Do not share this OTP with anyone. - Team BookMyBand

(833) 635-7711
theimm0rtaL$2026

- [x] email fix
- [x] while editing community, we are asking srfax credentials again.
- [x] renameing the files and new files should exist outside of processing folder.
- [ ] sharepoint path hard coded,able to add from ui.
- [x] Able to verify srfax 
- [x] SharePoint verification

{"cost": {"currency": "USD", "ocr_cost": 0.01, "total_cost": 0.01936, "llm_input_cost": 0.00682, "llm_total_cost": 0.00936, "llm_output_cost": 0.00254}, "usage": {"total_tokens": 2982, "prompt_tokens": 2728, "completion_tokens": 254}, "summary": "Physician order for an EKG with interpretation for Jeffrey Loomis, issued by Lisa Lehr NP on 03/02/2026 at OnCare Palliative LLC. The encounter is for a preprocedural cardiovascular examination.", "provider": "azure", "model_name": "gpt-4o", "patient_name": "LOOMIS, JEFFREY", "document_type": "Physician Orders", "classification": "Physician Orders", "clinician_name": "LISA LEHR NP", "encounter_type": "EKG W/ INTERPRETATION", "key_highlights": ["Patient name: LOOMIS, JEFFREY", "DOB: 04/26/1947, Gender: M", "Facility: ONCARE PALLIATIVE LLC, Omaha, NE", "Ordered by: LISA LEHR NP, NPI: 1508465048", "Procedure: EKG W/ INTERPRETATION, ICD Code: Z01.810"], "date_of_service": "03/02/2026", "invocation_type": "classification", "confidence_score": 95, "mrn_chart_number": "15614699", "received_date_time": "03/17/2026 03:37"}