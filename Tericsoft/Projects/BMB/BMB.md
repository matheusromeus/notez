Jira link: https://tericsoft.atlassian.net/jira/software/projects/BMB/boards/537

full page loader at last step of onboarding.
after band onboarding, a flash of the band onboarding is coming again.

whatsapp has a document with the latest call and what needs to be done.

the online call we had for an hour is not added to the allocation

To Do
- [ ] is the band name coming correctly? in profile and what i give in oboarding.
- [ ] margin from top header block
- [ ] get list of where all images are being uploaded and then set the rules accordingly
- [ ] setup cron job (once a day) 0 3 * * * cd /path/to/BookMyBand-Admin-API && /usr/bin/env python -m app.workers.gig_cleanup_job >> /var/log/gig_cleanup.log 2>&1
- [ ] make sure all the workers are hosted
- [ ] verification expires after year from acceptance
- [ ] run the verification flow on the club portal
- [ ] if rejected or accpeted, a notifcation has to be sent.
- [ ] what if the promotion is accepted after the start date (edge case. start should be the next day. and once the day has passed, need a cron job to set the promotion request to expired)
- [ ] liked bands and recommended bands need a differenciation in UI
- [ ] Zoho invoice is not being created
- [ ] resolution and upload limit for all photos


- [ ] login with SMS creds -> Yes need to provide, check with Sai for access  
- [ ] can they send verification only once in 'x' months? -> nope  
- [ ] a band can send a request to another band, same with clubs
- [ ] The first 15 bands to accept a public lead will use their credits to connect with the fan. needs more clarity -> Yes, credits should be consumed  
- [ ] can club send a public inquiry to bands? -> No, it needs to be private for now   
- [ ] Lead conversation history will be available for a limited time (e.g., 10 days) before becoming defunct. How should this be done? Will the request itself be invalid? Will they have to send the request again? -> Yes, they'll have to send again