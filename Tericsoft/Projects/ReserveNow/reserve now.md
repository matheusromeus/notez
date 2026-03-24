
 refer [[landing page]]

customers are multiple because we dont have a customer creation or accounts. it's tied to a package.

To Do
---
- [x] carousel on view business page - 1h
- [x] show only owner packages in the dsaboard dropdown - 5m
- [x] only 10/page working on dashboard tbale - 5m
- [x] even afte rtoggling active and inactive packages the filter is not working in my packages - 5m
- [x] phase 2 of onboarding is going to be moved to superadmin portal
- [x] display email and phone number to be shown/disabled on view business (what to show too) add alternate email and phone (add them to the form, and they will be shown on the view) - 0.5h
- [x] filters booking not working status
- [x] add the owner info in the verifications tab
- [x] when somebody books a package, send email to the business head
- [x] packages and sales have different duration edit option for sale duration, optional toggle for sale duration
- [x] if we can select duarion of the package, and select days, only then itll be created, like sundays, like how the alarm feature works in iphone (no need to edit the days)
- [x] extending package option ux is very painful (inside upadte session 302) & rate for bulk change
- [x] editing package, should allow zero price when package is free
- [x] no of slots card in the dashboard - what is slots?
- [x] add the fields needed in phase 1 and phase 2 of onboarding
	- **Aadhar Card No** - only number and png/jpg/pdf? - phase 1
	- **Cancelled Cheque** - png jpg
	- business type
- [x] make the first text as 500 rupees
- [x] access/role management for EDP role - changing the permissions of the business owner and their team 1h
- [x] making new clients flow in marketing - 2h
- [x] slots can never go below the number of bookings on that session
- [x] individual/bulk slot updation logic
- [x] zoho invoices should be called for every payment
- [x] customers excel export
- [x] Still mentioning as slots instead of tickets
- [x] gap in payment completion screen in client portal - make the button disabled (full screen loader, do not click back) - on razorpay-details api call, redirect and then loading
- [x] want to change the booking date (the entire booking)
- [x] give the calendar in the view business page (with multiple days) - 6h, with multiple day qr code and package opening in new page
- [x] onboarding in superadmin - rememebr the step we are in.
- [x] sale duration should not outpass last date of package
- [ ] email saying that these data are needed

- [ ] add the new commission structure with internal formulae
- [ ] onboarding redirection issue, from go to Admin button, from payment page
- [ ] disable ended events only for MIS
- [ ] responsive design

- [ ] Look into export functionality of 
	for bookings - it can not be the last stage.
	for transactions - its only what money is involved in


check every payment to see whether zoho invoice is working, may need change in env variables

same email id is given, for 2 different users. between users, cusoimters, business_clients.

subscription starts from the day you paid and not when the kyc got approved


- [ ] no payment in onboarding. after entering details, go straight to kyc verification pending page. nothing about any price or payment.
- [ ] qrcode with extra info
	- [ ] the unique code
	- [ ] branding reserve now
	- [ ] name, email
	- [ ] booking id
- [ ] customer bulk client upload (customer or business client?)
- [ ] instead uuid, he wants the business name
- [ ] super admin, transactions company wise / export option (how the filter is applied)
- [ ] multiple business heads entry
- [ ] checkbox for whether they want GST details
	- [ ] ![[Pasted image 20260324073656.png]]
	- [ ] when toggled, they can enter the gst number and the company name (this is for customer)

so option to create a customer (same popup as creating a booking), map them to a package (instead of tickets). they just want a customer database, 

he has to know what transactions each company has done. so that he can pay him. so we need to add a column for the company name.

edp does verification, entering a new client

