

full page loader at last step of onboarding.
after band onboarding, a flash of the band onboarding is coming again.



# Phoenix

occupancy breakdown is wrong 
```json
"occupancyBreakdown": {
	"tenant": {
		"officeFloorOccupiedArea": 174168,
		"basementOccupiedArea": 0,
		"totalOccupiedArea": 174168
	},
	"amenity": {
		"officeFloorOccupiedArea": 0,
		"basementOccupiedArea": 0,
		"totalOccupiedArea": 0
	}
},
```

```json
"occupancyList": [
	{
		"id": "699303c2f7dc24e52b0054be",
		"clientType": "tenant",
		"totalAreaOccupiedByClient": 12
	},
	{
		"id": "69942b21f7dc24e52b0054ca",
		"clientType": "tenant",
		"totalAreaOccupiedByClient": 114902
	},
	{
		"id": "6992fd3af7dc24e52b0054ab",
		"clientType": "tenant",
		"totalAreaOccupiedByClient": 59254
	}
],
```

```json
this value is also wrong

"occupiedFloors": [
	{
		"floorNumber": 9,
		"floorTitle": "9",
		"leasableArea": 114902,
		"vacantArea": 0,
		"occupiedArea": 114902,
		"towerId": "6992fb8963b9954dfa2349ef",
		"previousLeasableArea": 114902,
		"isSezZone": false,
		"igst": 0
	}
],
```