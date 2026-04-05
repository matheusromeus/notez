
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


- [x] trigger 
- [x] crop config
- [ ] user onboarding
- [ ] add request
- [x] aoi locations

### tickets today
trigger config tickets are added, but not like how we think.
3hrs - trigger config UI screens
2hrs - integrating apis for trigger config and cleaning up branches
3hrs - s2 rnd
3hrs - Integrating Request APIs for viewing and UI screens for View Request
x hrs - resolve bugs


is fpo organisations the organistations?


in the /management/request/add form, in the section historical simulation and backtest, if one of the checkbox is selected, then the run simulation has to b enabled.
curl --location --request GET '[https://archive-api.open-meteo.com/v1/archive?latitude=52.52&longitude=13.41&start_date=2010-01-01&…](https://archive-api.open-meteo.com/v1/archive?latitude=52.52&longitude=13.41&start_date=2010-01-01&end_date=2019-12-31&hourly=temperature_2m%2Crelative_humidity_2m%2Capparent_temperature%2Crain%27 "https://archive-api.open-meteo.com/v1/archive?latitude=52.52&longitude=13.41&start_date=2010-01-01&end_date=2019-12-31&hourly=temperature_2m%2crelative_humidity_2m%2capparent_temperature%2crain%27") \  
--header 'accept: application/json' \  
--header 'Content-Type: application/json' \  
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI1MTcxM2I2Yy1iZTVjLTQ0ZjMtOWM2OS0xNTZlZjljZWMyMDkiLCJleHAiOjE3NzUyOTEyNTgsInR5cGUiOiJhY2Nlc3MifQ.d2p80_a6ixOjKaEfJmdbx4XKGF6UK6lU6Pj2QTVKEWc' \  
--data {  
    "latitude": "38.6275",  
    "longitude": "-92.5666",  
    "start_date": "2020-01-01",  
    "end_date": "2026-01-02"
}