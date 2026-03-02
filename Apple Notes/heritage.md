When <span style="font-family:.AppleSystemUIFontMonospaced-Regular;font-size:15pt;">MaxDeliveryCount</span> is exceeded → message auto-dead-letters.


```
workflow.status = FAILED
```
and message moved to DLQ

Then typical flow:
	1.	Engineer inspects failure
	2.	Fix SharePoint/API issue
	3.	Requeue document_id
	4.	Update workflow → PROCESSING
	5.	If success → COMPLETED

check if its setup and max deliverycount is set.