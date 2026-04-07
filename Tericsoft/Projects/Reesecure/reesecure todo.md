
- [ ] user onboarding
- [ ] add user validations is left (check excel sheet)
- [ ] for counties/districts - make it searchable or make it state and the district (for USA its just chicago right now)
- [ ] mobile number not taken in review details of add user


- [ ] how should the aoi location id should be?
- [ ] are 3 max limit in phases (the number of phases or digits of phases)
- [ ] same above for duration what's the max number of days?
- [ ] can we edit the growth phase in the crop? no screens for that yet.
- [ ] resolve bugs allocated to you
- [ ] talk to shyam
	- [ ] there is no way to get details of the user after clickign on magic link (what role did he select, what is his name)
		- [ ] what is the token even doing? token is hashed and then the hash is stored in the db, fk to users.id (so we need an endpoint to give the token and get the details) also how do we know if he's the us version or the indian version? CAN SELECT CROSS IN THE ADD USER FORM
- [ ] there is no active/inactive toggle option for triggers
- [ ] what all are the editable fields in edit request? no UI screens
- [ ] how should the request ID look like for requests?
- [ ] search may not be working on request api


what is different between the indian and us version in user onboarding?
- for each country
	- for each role

http://localhost:5173/complete-profile?token=E0iA1Vy2ldNB87DukByiZgF70x_axW5gi3nwzt94dx8

[[roles]]

### tickets
trigger config tickets are added, but not like how we think.
3hrs - trigger config UI screens
2hrs - integrating apis for trigger config and cleaning up branches
3hrs - s2 rnd
3hrs - Integrating Request APIs for viewing and UI screens for View Request
x hrs - resolve bugs
2 hrs - Evidence Pack Logs
2 hrs - PDF - export pdf from view request.
correlation matrix
adding layer
request flow change
user onboarding screens?

add request then call the auto suggest
when creating a policy - send status as pending.
policy id for all simulations

monitoring or under review popup.








new tab based UI in underwriter requests
	filter for policies