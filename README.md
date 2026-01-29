## How to Retrieve and Deploy Session_Id__c Field

If you encounter errors deploying the Session_Id__c field as a Lookup, follow these steps:

1. **Retrieve the field from your org (if it exists):**
	```
	sfdx force:source:retrieve -m CustomField:AuditTrail__c.Session_Id__c
	```
	If you get errors, check your Salesforce CLI and Node.js installation.

2. **If the field exists in your org as a different type:**
	- Delete the Session_Id__c field from Salesforce Setup (Object Manager > AuditTrail__c > Fields & Relationships).
	- Or, rename the existing field if you want to keep the data.

3. **Deploy the new Lookup field:**
	```
	sfdx force:source:deploy -m CustomField:AuditTrail__c.Session_Id__c
	```

This ensures the field is created as a Lookup(User) in your org.
# OnBoardingEsign
