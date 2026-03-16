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
