Jira link: https://tericsoft.atlassian.net/jira/software/projects/BMB/boards/537

full page loader at last step of onboarding.
after band onboarding, a flash of the band onboarding is coming again.

whatsapp has a document with the latest call and what needs to be done.

the online call we had for an hour is not added to the allocation


To Discuss
- [ ] any restrictions on number of times the username can be changed?
- [ ] login with SMS creds
- [ ] login only through phone number? or both? then if they change the number then what to do? we need their actual number. and if they change their number or email and log out, then they won't be able to log in.
- [ ] can they send verification only once in 'x' months?
- [ ] is there an expiry for the verification request?
- [ ] can fan send a connection request to a club?
- [ ] The first 15 bands to accept a public lead will use their credits to connect with the fan. needs more clarity
- [ ] can club send a public inquiry to bands?
- [ ] Lead conversation history will be available for a limited time (e.g., 10 days) before becoming defunct. How should this be done? Will the request itself be invalid? Will they have to send the request again?

To Do
- [ ] is the band name coming correctly? in profile and what i give in oboarding.
- [ ] margin from top header block
- [ ] is the credit costs being taken from the database?
- [ ] get list of where all images are being uploaded and then set the rules accordingly
- [ ] setup cron job (once a day) 0 3 * * * cd /path/to/BookMyBand-Admin-API && /usr/bin/env python -m app.workers.gig_cleanup_job >> /var/log/gig_cleanup.log 2>&1
- [ ] verification expires after year from acceptance
- [ ] run the verification flow on the club portal
- [ ] if rejected or accpeted, a notifcation has to be sent.
- [ ] what if the promotion is accepted after the start date (edge case. start should be the next day. and once the day has passed, need a cron job to set the promotion request to expired)
- [ ] liked bands and recommended bands need a differenciation in UI
- [ ] Zoho invoice is not being created
- [ ] resolution and upload limit for all photos