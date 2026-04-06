
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


---

Available crop_types: ['wheat', 'barley', 'maize', 'rice', 'soybean', 'cotton', 'potato', 'sunflower', 'canola', 'sugar_beet', 'groundnut', 'grape', 'tomato', 'citrus', 'dry_bean', 'pea', 'strawberry', 'coffee', 'banana', 'olive'] - in the entire app

portfolio_value is not needed.

use the json file to get the growth phases from 

configure trigger should be above. 


trigger name is trgger id

trigger hases are bbch stage

trigger_type is only one

payout along with each trigger. 


v1/triggger
backetest and monte carlo

```backtest-response
{
    "mode": "per_trigger",
    "years": [
        {
            "year": 2016,
            "total_rain_mm": 1130.5,
            "max_temp_c": 42.5,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": true,
                    "payout": 2000.0
                }
            ],
            "total_payout": 20000.0,
            "total_payout_pct": 40.0
        },
        {
            "year": 2017,
            "total_rain_mm": 748.5,
            "max_temp_c": 41.0,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": true,
                    "payout": 2000.0
                }
            ],
            "total_payout": 16000.0,
            "total_payout_pct": 32.0
        },
        {
            "year": 2018,
            "total_rain_mm": 911.0,
            "max_temp_c": 40.9,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": true,
                    "payout": 2000.0
                }
            ],
            "total_payout": 16000.0,
            "total_payout_pct": 32.0
        },
        {
            "year": 2019,
            "total_rain_mm": 1265.7,
            "max_temp_c": 44.2,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                }
            ],
            "total_payout": 10000.0,
            "total_payout_pct": 20.0
        },
        {
            "year": 2020,
            "total_rain_mm": 998.4,
            "max_temp_c": 39.0,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": true,
                    "payout": 2000.0
                }
            ],
            "total_payout": 12000.0,
            "total_payout_pct": 24.0
        },
        {
            "year": 2021,
            "total_rain_mm": 1247.7,
            "max_temp_c": 37.2,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                }
            ],
            "total_payout": 0.0,
            "total_payout_pct": 0.0
        },
        {
            "year": 2022,
            "total_rain_mm": 1780.3,
            "max_temp_c": 42.9,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                }
            ],
            "total_payout": 10000.0,
            "total_payout_pct": 20.0
        },
        {
            "year": 2023,
            "total_rain_mm": 948.9,
            "max_temp_c": 41.8,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": true,
                    "payout": 2000.0
                }
            ],
            "total_payout": 18000.0,
            "total_payout_pct": 36.0
        },
        {
            "year": 2024,
            "total_rain_mm": 1402.3,
            "max_temp_c": 41.0,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                }
            ],
            "total_payout": 6000.0,
            "total_payout_pct": 12.0
        },
        {
            "year": 2025,
            "total_rain_mm": 1278.7,
            "max_temp_c": 39.5,
            "trigger_results": [
                {
                    "trigger_id": "COTTON_00_09_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_00_09_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Germination (BBCH 0)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_10_19_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Leaf development (BBCH 1)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_30_49_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": true,
                    "payout": 2000.0
                },
                {
                    "trigger_id": "COTTON_30_49_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Squaring (BBCH 3-4)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_60_69_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_60_69_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Flowering (BBCH 6)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_HEAT",
                    "peril": "Heat Stress",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_70_79_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll development (BBCH 7)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_HEAT",
                    "peril": "Cold Stress",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                },
                {
                    "trigger_id": "COTTON_80_89_DROUGHT",
                    "peril": "Drought",
                    "phase_name": "Boll opening (BBCH 8)",
                    "fired": false,
                    "payout": 0.0
                }
            ],
            "total_payout": 2000.0,
            "total_payout_pct": 4.0
        }
    ],
    "summary": {
        "sum_insured": 50000.0,
        "mean_rainfall_mm": 1171.2,
        "avg_annual_payout": 11000.0,
        "avg_annual_payout_pct": 22.0,
        "years_with_payout": 9,
        "max_payout": 20000.0,
        "max_payout_pct": 40.0,
        "return_period_years": 1.1,
        "trigger_stats": [
            {
                "trigger_id": "COTTON_00_09_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Germination (BBCH 0)",
                "threshold_value": 41.0,
                "payout_amount": 2000.0,
                "fire_count": 4,
                "fire_frequency_pct": 40.0,
                "return_period_years": 2.5,
                "avg_annual_payout": 800.0
            },
            {
                "trigger_id": "COTTON_00_09_DROUGHT",
                "peril": "Drought",
                "phase_name": "Germination (BBCH 0)",
                "threshold_value": 60.0,
                "payout_amount": 2000.0,
                "fire_count": 0,
                "fire_frequency_pct": 0.0,
                "return_period_years": 10.0,
                "avg_annual_payout": 0.0
            },
            {
                "trigger_id": "COTTON_10_19_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Leaf development (BBCH 1)",
                "threshold_value": 40.1,
                "payout_amount": 2000.0,
                "fire_count": 7,
                "fire_frequency_pct": 70.0,
                "return_period_years": 1.4,
                "avg_annual_payout": 1400.0
            },
            {
                "trigger_id": "COTTON_10_19_DROUGHT",
                "peril": "Drought",
                "phase_name": "Leaf development (BBCH 1)",
                "threshold_value": 0.733,
                "payout_amount": 2000.0,
                "fire_count": 5,
                "fire_frequency_pct": 50.0,
                "return_period_years": 2.0,
                "avg_annual_payout": 1000.0
            },
            {
                "trigger_id": "COTTON_30_49_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Squaring (BBCH 3-4)",
                "threshold_value": 37.5,
                "payout_amount": 2000.0,
                "fire_count": 9,
                "fire_frequency_pct": 90.0,
                "return_period_years": 1.1,
                "avg_annual_payout": 1800.0
            },
            {
                "trigger_id": "COTTON_30_49_DROUGHT",
                "peril": "Drought",
                "phase_name": "Squaring (BBCH 3-4)",
                "threshold_value": 0.484,
                "payout_amount": 2000.0,
                "fire_count": 5,
                "fire_frequency_pct": 50.0,
                "return_period_years": 2.0,
                "avg_annual_payout": 1000.0
            },
            {
                "trigger_id": "COTTON_60_69_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Flowering (BBCH 6)",
                "threshold_value": 40.0,
                "payout_amount": 2000.0,
                "fire_count": 7,
                "fire_frequency_pct": 70.0,
                "return_period_years": 1.4,
                "avg_annual_payout": 1400.0
            },
            {
                "trigger_id": "COTTON_60_69_DROUGHT",
                "peril": "Drought",
                "phase_name": "Flowering (BBCH 6)",
                "threshold_value": 0.404,
                "payout_amount": 2000.0,
                "fire_count": 5,
                "fire_frequency_pct": 50.0,
                "return_period_years": 2.0,
                "avg_annual_payout": 1000.0
            },
            {
                "trigger_id": "COTTON_70_79_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Boll development (BBCH 7)",
                "threshold_value": 42.0,
                "payout_amount": 2000.0,
                "fire_count": 3,
                "fire_frequency_pct": 30.0,
                "return_period_years": 3.3,
                "avg_annual_payout": 600.0
            },
            {
                "trigger_id": "COTTON_70_79_DROUGHT",
                "peril": "Drought",
                "phase_name": "Boll development (BBCH 7)",
                "threshold_value": 0.25,
                "payout_amount": 2000.0,
                "fire_count": 5,
                "fire_frequency_pct": 50.0,
                "return_period_years": 2.0,
                "avg_annual_payout": 1000.0
            },
            {
                "trigger_id": "COTTON_80_89_HEAT",
                "peril": "Cold Stress",
                "phase_name": "Boll opening (BBCH 8)",
                "threshold_value": 10.0,
                "payout_amount": 2000.0,
                "fire_count": 0,
                "fire_frequency_pct": 0.0,
                "return_period_years": 10.0,
                "avg_annual_payout": 0.0
            },
            {
                "trigger_id": "COTTON_80_89_DROUGHT",
                "peril": "Drought",
                "phase_name": "Boll opening (BBCH 8)",
                "threshold_value": 0.347,
                "payout_amount": 2000.0,
                "fire_count": 5,
                "fire_frequency_pct": 50.0,
                "return_period_years": 2.0,
                "avg_annual_payout": 1000.0
            }
        ]
    }
}
```


```montecarlo response
{
    "status": "success",
    "api_version": "v1",
    "generated_at": "2026-04-06T15:35:58.763124+00:00",
    "request_id": "1baae8dc-d92c-452a-9c3e-1a749238e229",
    "summary": {
        "financials": {
            "currency": "INR",
            "sum_insured": 50000.0,
            "expected_loss": 4955.1,
            "var_95": 10000.0,
            "var_99": 12000.0,
            "pml": 12000.0,
            "burn_cost_pct": 9.9102,
            "suggested_premium": 4932.2,
            "percentile_breakdown": {
                "p25": 0.0,
                "p50": 0.0,
                "p75": 10000.0,
                "p90": 10000.0,
                "p95": 10000.0,
                "p99": 12000.0
            }
        },
        "risk_layers": [
            {
                "name": "Layer 1: Working",
                "attachment": 0.0,
                "exhaustion": 1.0,
                "hit_probability": 0.4957,
                "exhaustion_prob": 0.4957,
                "expected_loss": 0.5,
                "color": "#22c55e",
                "zero_shortfall_hedge": "Primary retention or high-frequency premium coverage."
            },
            {
                "name": "Layer 2: Retention",
                "attachment": 0.0,
                "exhaustion": 10000.0,
                "hit_probability": 0.4957,
                "exhaustion_prob": 0.4886,
                "expected_loss": 4929.1,
                "color": "#f59e0b",
                "zero_shortfall_hedge": "Quota share reinsurance or aggregate stop-loss."
            },
            {
                "name": "Layer 3: XoL",
                "attachment": 10000.0,
                "exhaustion": 10001.0,
                "hit_probability": 0.013,
                "exhaustion_prob": 0.013,
                "expected_loss": 0.01,
                "color": "#ef4444",
                "zero_shortfall_hedge": "Excess-of-loss reinsurance or MCX / CME weather derivatives."
            },
            {
                "name": "Layer 4: Cat XoL",
                "attachment": 10000.0,
                "exhaustion": 50000.0,
                "hit_probability": 0.013,
                "exhaustion_prob": 0.0,
                "expected_loss": 26.0,
                "color": "#a855f7",
                "zero_shortfall_hedge": "Catastrophe bond (ILS) or industry loss warranty."
            }
        ],
        "per_trigger_risk": [
            {
                "trigger_id": "COTTON_00_09_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Germination (BBCH 0)",
                "threshold_value": 41.0,
                "payout_amount": 2000.0,
                "fire_probability_pct": 0.0,
                "expected_annual_payout": 0.0
            },
            {
                "trigger_id": "COTTON_00_09_DROUGHT",
                "peril": "Drought",
                "phase_name": "Germination (BBCH 0)",
                "threshold_value": 60.0,
                "payout_amount": 2000.0,
                "fire_probability_pct": 1.3,
                "expected_annual_payout": 26.0
            },
            {
                "trigger_id": "COTTON_10_19_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Leaf development (BBCH 1)",
                "threshold_value": 40.1,
                "payout_amount": 2000.0,
                "fire_probability_pct": 0.0,
                "expected_annual_payout": 0.0
            },
            {
                "trigger_id": "COTTON_10_19_DROUGHT",
                "peril": "Drought",
                "phase_name": "Leaf development (BBCH 1)",
                "threshold_value": 0.733,
                "payout_amount": 2000.0,
                "fire_probability_pct": 48.9,
                "expected_annual_payout": 977.22
            },
            {
                "trigger_id": "COTTON_30_49_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Squaring (BBCH 3-4)",
                "threshold_value": 37.5,
                "payout_amount": 2000.0,
                "fire_probability_pct": 0.0,
                "expected_annual_payout": 0.0
            },
            {
                "trigger_id": "COTTON_30_49_DROUGHT",
                "peril": "Drought",
                "phase_name": "Squaring (BBCH 3-4)",
                "threshold_value": 0.484,
                "payout_amount": 2000.0,
                "fire_probability_pct": 49.2,
                "expected_annual_payout": 984.74
            },
            {
                "trigger_id": "COTTON_60_69_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Flowering (BBCH 6)",
                "threshold_value": 40.0,
                "payout_amount": 2000.0,
                "fire_probability_pct": 0.0,
                "expected_annual_payout": 0.0
            },
            {
                "trigger_id": "COTTON_60_69_DROUGHT",
                "peril": "Drought",
                "phase_name": "Flowering (BBCH 6)",
                "threshold_value": 0.404,
                "payout_amount": 2000.0,
                "fire_probability_pct": 49.4,
                "expected_annual_payout": 987.14
            },
            {
                "trigger_id": "COTTON_70_79_HEAT",
                "peril": "Heat Stress",
                "phase_name": "Boll development (BBCH 7)",
                "threshold_value": 42.0,
                "payout_amount": 2000.0,
                "fire_probability_pct": 0.0,
                "expected_annual_payout": 0.0
            },
            {
                "trigger_id": "COTTON_70_79_DROUGHT",
                "peril": "Drought",
                "phase_name": "Boll development (BBCH 7)",
                "threshold_value": 0.25,
                "payout_amount": 2000.0,
                "fire_probability_pct": 49.6,
                "expected_annual_payout": 991.36
            },
            {
                "trigger_id": "COTTON_80_89_HEAT",
                "peril": "Cold Stress",
                "phase_name": "Boll opening (BBCH 8)",
                "threshold_value": 10.0,
                "payout_amount": 2000.0,
                "fire_probability_pct": 0.0,
                "expected_annual_payout": 0.0
            },
            {
                "trigger_id": "COTTON_80_89_DROUGHT",
                "peril": "Drought",
                "phase_name": "Boll opening (BBCH 8)",
                "threshold_value": 0.347,
                "payout_amount": 2000.0,
                "fire_probability_pct": 49.4,
                "expected_annual_payout": 988.64
            }
        ],
        "weather": {
            "rain_mean": 917.03,
            "rain_std": 246.23,
            "temp_mean": 31.69
        },
        "payout_histogram": {
            "counts": [
                50568,
                75,
                120,
                376,
                48861,
                0,
                0,
                0,
                0,
                0,
                0,
                0,
                0,
                0,
                0,
                0,
                0,
                0,
                0,
                0
            ],
            "bin_edges": [
                0.0,
                0.05,
                0.1,
                0.15000000000000002,
                0.2,
                0.25,
                0.30000000000000004,
                0.35000000000000003,
                0.4,
                0.45,
                0.5,
                0.55,
                0.6000000000000001,
                0.65,
                0.7000000000000001,
                0.75,
                0.8,
                0.8500000000000001,
                0.9,
                0.9500000000000001,
                1.0
            ]
        },
        "rainfall_histogram": {
            "counts": [
                32,
                47,
                96,
                218,
                418,
                747,
                1312,
                2199,
                3318,
                4704,
                6427,
                8019,
                9253,
                10137,
                10387,
                9878,
                8814,
                7298,
                5748,
                4127,
                2799,
                1802,
                1050,
                594,
                292,
                172,
                72,
                28,
                7,
                5
            ],
            "bin_edges": [
                0.0,
                64.17049290898703,
                128.34098581797406,
                192.5114787269611,
                256.6819716359481,
                320.8524645449352,
                385.0229574539222,
                449.1934503629092,
                513.3639432718962,
                577.5344361808833,
                641.7049290898703,
                705.8754219988573,
                770.0459149078443,
                834.2164078168314,
                898.3869007258184,
                962.5573936348054,
                1026.7278865437925,
                1090.8983794527794,
                1155.0688723617666,
                1219.2393652707535,
                1283.4098581797407,
                1347.5803510887276,
                1411.7508439977146,
                1475.9213369067018,
                1540.0918298156887,
                1604.2623227246756,
                1668.4328156336628,
                1732.6033085426498,
                1796.7738014516367,
                1860.9442943606239,
                1925.114787269611
            ]
        },
        "num_simulations": 100000,
        "historical_years_used": 10
    },
    "metadata": {
        "estimated_duration_days": 98,
        "crop_base_temp_c": 15,
        "target_maturity_gdd": 1500.0
    }
}
```