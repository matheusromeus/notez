
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

payment due date is not greater than billing to date.

25th invoices are generated and cleared on our end
then on 1st sent to gst, approved and setn to client
and then by 10th the payment is made

insert supply type in code itself for tenant, add a dropdown.

HSN Code - Tenant?
Rent & Parking & Signage - 997212
CAM - 995419

More items in the Create New Invoice

sezwp - igst 18%
if igst 0% - sezwop
