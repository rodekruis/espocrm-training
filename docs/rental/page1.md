**Introduction**

The EspoCRM Information Management (IM) template streamlines the IM process of rental and hosting assistance programs. The template includes:

- An EspoCRM instance with a tailored set of entities and fields covering the different phases of rental and hosting assistance programs
  
- Workflows to automize processes such as eligibility calculation, marking duplicate registrations and the creation of cash transfers
  
- XLS- and Kobo-based question libraries, empowering National Societies to easily create registration forms in Kobo and EspoCRM
  

The figure below provides an overview of the program phases, the entities and the functionalities that are included in the module. 
![image](https://github.com/user-attachments/assets/c8387d97-2c91-4881-9759-215f94cb164f)


# Affected Households 
The registration of affected households can be done with KoboCollect or directly in EspoCRM. Affected households is one of the entities in EspoCRM. This entity contains data fields which include an overview, household composition, matching criteria, and status. 

In the overview section, contact information on the head of the households (I.e., name, contact details, and date of arrival in the country) can be recorded. The overview section also contains data fields for identification, language preferences, current accommodation, comment box and matches. 

Information on the household size, number of children or number of elderly is recorded in the household composition. In the matching criteria, information that can match the affected household to a potential homeowner is provided. Under status, the registration status (whether new, pending, ready for matching or match confirmed) and eligibility status (approved, rejected, or needs validation) are assigned. The results of the duplicate check and the eligibility score (see section 6.4.3 for eligibility score calculation) are also reflected under the status section. 

![image](https://github.com/user-attachments/assets/dc7957b5-0715-4250-9cea-121a6069582d)


##Registration directly in EspoCRM##
-	Click on the Affected households entity in the upper bar
-	You are directed to the page with all existing registrations 
-	To create a new registration, click on Create Affected household at the top-right 
-	The registration form opens
-	The question of the form are divided into multiple themes
6.4.3	Eligibility status
-	An eligibility status is assigned to affected households during registration
-	Based on an eligibility score, the eligibility status assigned can be:
o	Approved 
o	Rejected 
o	Needs validation 

-	Eligibility score is currently calculated based on the following parameters, but this can be adjusted based on your eligibility criteria:
o	Household composition (I.e., single, elderly headed, large family)
o	Health (I.e., physical, and chronic difficulties)
o	Accommodation type (I.e., if household has access to accommodation or live in a collective center)

-	The eligibility status can be seen under the overview of the affected households and the status for each household can be updated by;
o	Clicking on the household ID
o	Navigate to status
o	Update eligibility status





- **Page Title**: `Persons Affected › create`
  - This page is used for creating a new record for a person affected by a specific situation.

