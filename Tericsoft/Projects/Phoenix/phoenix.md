
**billing entities** have **properties**

and each property has a **property_tower**.

property_tower has the totalLeasableArea

then each tower has floors, and each floor has an area.

that area is occupied by tenants.

how each tenant occupies a certain area is given inside towerBreakdown array. (inside tower_occupancy table)


tables
- billing_entity
- property (belongs to billing_entity)
- property_tower (belongs to property)
- floor (belongs to property_tower)
- tenant
- tenant_occupancy (many tenants per floor, optional partial area)

1. occupiedArea is counted twice. One from property_tower and one from tenant_occupancy. Normally it sets to zero, but if it doesn't it can result in negative values or double counts.
2. There was stale data in the tower breakdown modal screen, which caused to give incorrect values for vacant area which cascaded

the values from frontend are taken without validation. there are no guardrails. 


---



25th invoices are generated and cleared on our end
then on 1st sent to gst, approved and sent to client
and then by 10th the payment is made




1. [x] supply type is hardcoded to B2B
	it can be B2B, B2C, SEZWP, SEZWOP, EXPWP, EXPWOP, DEXP. give them a dropdown to select.
	sezwp - if igst 18%
	if igst 0% - sezwop

2. [x] More items in the Manual Create New Invoice

3. [x] Give option to enter HSN Code too
	- [x] HSN Code - Tenant?
	- [x] Rent & Parking & Signage - 997212
	- [x] CAM - 995419

4. [x] payment due date is not greater than billing to date. remove that condition. can be advance invoices too

when adding a new billing entity, they have to contact us. add a new api user and then add the GST number on code also




---

- [x] company name should be bold
- [x] formatting - decimal points and straight line
- [x] in filter only the current entity tenants are supposed to come
- [x] parking slots (in the invoice)
- [x] date format in 2026-03-25 change to indian format
- [x] multiple address option in the entity and then when selecting the property, automatically add the address or give multiple address and select the one.
- [x] the invoice due date is always 10 days from the date of issue of the invoice. So the day that the invoice was sent to the client.
- [x] test sendtoclient cron from our emails

get all the invoices accepted

- [x] double check the address taking 50 characters , remove the error
- [x] bank details - bank details parking invoice (check in prod)

- [ ] update the gst logic to the following
	if sez Zone = yes
		only take igst
	if sez Zone = no
		only cgst and sgst
- [ ] how did the cam invoice get accepted?




for signage and parking - igst was not taken

once the invoices are created, if no escalation was applied, then no issues. because none of the values are being changed. 
BUT, if there is an escalation, the escalation was applied, and the next escalation date is now changed. also the current rate is also changed.
Now, if we try to delete the invoice, and then try to run it again, then this will cause an issue, because the amounts and details are different too.

CRON JOB, which takes all the approved invoices, and bulk sends it to GST on the 1st.