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
- [ ] Able to verify srfax and SharePoint even though we are giving wrong credentials and path.


{"cost": {"currency": "USD", "ocr_cost": 0.01, "total_cost": 0.0192375, "llm_input_cost": 0.0068175, "llm_total_cost": 0.0092375, "llm_output_cost": 0.00242}, "usage": {"total_tokens": 2969, "prompt_tokens": 2727, "completion_tokens": 242}, "summary": "Physician order for a cardiology exam (EKG with interpretation) for Jeffrey Loomis, issued by Lisa Lehr NP on 03/02/2026. The procedure is preprocedural cardiovascular examination, with ICD code Z01.810.", "provider": "azure", "model_name": "gpt-4o", "patient_name": "LOOMIS, JEFFREY", "document_type": "Physician Orders", "classification": "Physician Orders", "clinician_name": "LISA LEHR NP", "encounter_type": "Cardiology Exam Order", "key_highlights": ["Cardiology exam order for EKG with interpretation.", "Procedure code: 93000.", "ICD code: Z01.810 - Encounter for preprocedural cardiovascular examination.", "Ordered by Lisa Lehr NP, NPI: 1508465048.", "Patient facility: ONCARE PALLIATIVE LLC, Omaha, NE."], "date_of_service": "03/02/2026", "invocation_type": "classification", "confidence_score": 98, "mrn_chart_number": "15614699", "received_date_time": "03/16/2026 05:33"}