Jira link: https://tericsoft.atlassian.net/jira/software/projects/BMB/boards/537

full page loader at last step of onboarding.

the online call we had for an hour is not added to the allocation

Ask Sahil
- [ ] login with SMS creds -> Yes need to provide, check with Sai for access  
- [ ] make sure all the workers are hosted
- [ ] Lead conversation history will be available for a limited time (e.g., 10 days) before becoming defunct. How should this be done? Will the request itself be invalid? Will they have to send the request again? -> Yes, they'll have to send again
- [ ] in production, check if the upload is taking a lot of time, after the server location has been changed
- [ ] does bands and clubs also need the liked/recommendations split?


- [x] Zoho invoice is not being created (refresh token got invalidated)


curl -H "Content-Type: application/data" -X POST https://accounts.zoho.com/oauth/v2/token?code=1000.802f04345a168653ad43328999db74ba.1f2be5f732102b3430b1700a33f8c150&client_id=1000.OAV9R04U9WDTAP9F4V565555VWGO8B&client_secret=5ee07b0a36ab1da320f5ec7895f6c1f69546613716&redirect_uri=http://www.zoho.com/books&grant_type=offline

https://accounts.zoho.com/oauth/v2/auth?scope=ZohoBooks.invoices.CREATE,ZohoBooks.invoices.READ,ZohoBooks.invoices.UPDATE,ZohoBooks.invoices.DELETE&client_id=1000.OAV9R04U9WDTAP9F4V565555VWGO8B&state=testing&response_type=code&redirect_uri=https://bookmyband.teric.services/&access_type=offline&prompt=consent

https://bookmyband.teric.services/?state=testing&code=1000.802f04345a168653ad43328999db74ba.1f2be5f732102b3430b1700a33f8c150&location=in&accounts-server=https%3A%2F%2Faccounts.zoho.in