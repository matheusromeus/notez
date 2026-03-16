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


Skol2025