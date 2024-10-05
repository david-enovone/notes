---
ticket: https://www.notion.so/Pharmacogenomics-doctor-admin-widget-6450943349e64871a88c7eeb7e0a5d59
tags:
  - "#db"
  - "#graph"
priority: P2
---


The doctors would like to know when a patient is currently taking a medication that they have a genetic risk factor for and for that to be displayed in the doctor admin

Tasks:

Replace the text field where users enter medication with an autocomplete. For this we will need to create a table and upload the medications database to it. Chantal has created a mockup you can ask for.

Create a widget where doctors in the doctor admin can see which medications that the user is taking has risk factors. To do this we will need to create a table for the pharmacogenomics database and upload it.

Since the pharmacogenomics database uses generic medication names, we will need to convert the medication that the user inputed into the generic name, and then use that name to search the pharmacogenomics table for mentions of it. The pharmacogenomics table will also state which RSID that effect is relevant to, see lastly we need to cross check that against the users genotype to see if theres a match and then surface those matches in the doctor admin.


Notes:

- Old data? 
	- What to do about users data that's already in this row?

