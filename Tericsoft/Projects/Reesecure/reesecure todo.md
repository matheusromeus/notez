

- [ ] user onboarding
- [ ] add user validations is left (check excel sheet)
- [ ] for counties/districts - make it searchable or make it state and the district (for USA its just chicago right now)
- [ ] mobile number not taken in review details of add user 
- [ ] without accepting both checkbox in user add, cannot send invitation
- [ ] add ticket for s2 R&D


- [ ] need api for trigger configurations (then validations also have to be done dont forget)
- [ ] how should the aoi location id should be?
- [ ] are 3 max limit in phases (the number of phases or digits of phases)
- [ ] same above for duration what's the max number of days?
- [ ] can we edit the growth phase in the crop? no screens for that yet.
- [x] trigger config ticket has not been created?
- [ ] resolve bugs allocated to you
- [ ] talk to shyam
	- [ ] for a country, and for a state -> crop
	- [ ] for a country, and for a state -> trigger
	- [ ] there is no way to get details of the user after clickign on magic link (what role did he select, what is his name)
		- [ ] what is the token even doing? token is hashed and then the hash is stored in the db, fk to users.id (so we need an endpoint to give the token and get the details) also how do we know if he's the us version or the indian version? CAN SELECT CROSS IN THE ADD USER FORM
	- [x] duplicate validations have to be added from the backend (check how the error message is being sent)
- [ ] Agricultural Lending Focus: cant see on user onbaording first role, india


how are we selecting whether the us version or the indian version of the user add has to be shown?

what is different between the indian and us version in user onboarding?
- for each country
	- for each role


http://localhost:5173/complete-profile?token=E0iA1Vy2ldNB87DukByiZgF70x_axW5gi3nwzt94dx8


- Regulatory complicance status (dropdown)
	- compliant
	- under review 
	- conditional approval
- Authorized Compliance Officer Name (text input box)
- Compliance Officer Email Address (text input box)
- Compliance Officer Mobile Number (mobile number input)
- Credit Rating Agency (dropdown)
	- CRISIL
	- ICRA
	- CARE
	- India Ratings
	- Brickwork
- Credit Rating Grade (dropdown)
	- AAA
	- AA
	- A
	- BBB
	- BB
	- Unrated
- Total loan portfolio size (dropdown)
	- < ₹50 Cr
	- ₹50–200 Cr
	- ₹200–1000 Cr
	- > ₹1000 Cr
	- Number of active borrowers (number input box)


- cryptographically signed, short-lived, ideally single-use, and
- validated server-side on every request.

India
lender admin
lender user
fpo administrator
fpo user
regulator
insurer administrator
insurer user
underwriter
reinsurer administrator
reinsurer user
broker
broker admin
broker user

[[roles]]