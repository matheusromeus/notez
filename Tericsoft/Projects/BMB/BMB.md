Jira link: https://tericsoft.atlassian.net/jira/software/projects/BMB/boards/537

full page loader at last step of onboarding.
after band onboarding, a flash of the band onboarding is coming again.

whatsapp has a document with the latest call and what needs to be done.

the online call we had for an hour is not added to the allocation


- any restrictions on number of times the username can be changed?
- login only through phone number? or both? then if they change the number then what to do? we need their actual number.
- show the members in their public profile
- is the band name coming correctly? in profile and what i give in oboarding.
- margin from top header block
- is the credit costs being taken from the database?
- get list of where all images are being uploaded and then set the rules accordingly
- setup cron job (once a day) 0 3 * * * cd /path/to/BookMyBand-Admin-API && /usr/bin/env python -m app.workers.gig_cleanup_job >> /var/log/gig_cleanup.log 2>&1
- is there an expiry for the verification request?
- verification expires after year from acceptance
- can they send verification only once in 'x' months?
- run the verification flow on the club portal
- if rejected or accpeted, a notifcation has to be sent.
- what if the promotion is accepted after the start date
- 