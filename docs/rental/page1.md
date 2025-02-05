# Introduction

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

## Main components of the form

**1. Registration through Kobo form**

- To register through Kobo, you need to use KoboCollect, an Android application, and configure it as explained in Sec. 4.3.

- When filling the form, carefully read the explanations underneath the questions

-	People arrive at the registration location with an SMS code, this code should be entered in the registration form; this is how the pre-registration is linked to the registration


**2. Registration directly in EspoCRM** 

-	Click on the `Affected households` entity in the upper bar
  
-	You are directed to the page with all existing registrations
  
-	To create a new registration, click on `Create affected household` at the top-right
  
-	The registration form opens
  
-	The question of the form are divided into multiple themes

  
**3. Eligibility status**

-	An eligibility status is assigned to affected households during registration
  
-	Based on an eligibility score, the eligibility status assigned can be:
  
    - Approved
      
    - Rejected
      
    - Needs validation
    
-	Eligibility score is currently calculated based on the following parameters, but this can be adjusted based on your eligibility criteria:
  
    - Household composition (I.e., single, elderly headed, large family)
      
    - Health (I.e., physical, and chronic difficulties)
      
    - Accommodation type (I.e., if household has access to accommodation or live in a collective center)

-	The eligibility status can be seen under the overview of the affected households and the status for each household can be updated by;
  
  - Clicking on the household ID
    
  - Navigate to status
    
  - Update eligibility status

  ![image](https://github.com/user-attachments/assets/cf5d98c5-447c-4d94-87c2-64ba4226b4af)


**4. Manually approve or reject affected household**

To manually approve or reject affected household

-	Go to `Affected households`
  
-	Search and filter to the household using the household ID or name (registration name)
  
-	Click on `household ID`
  
-	Navigate to `Status`
  
-	Click on the tick box to manually approve or reject the household


**5. Registration status**

-	A registration status is assigned to affected households from the beginning of the registration, and this status changes throughout the process.
  
-	The following registration status are assigned depending on the stage at which the registration process is:
  
    - New – Status is assigned to all new registrations.
      
    - Pending- Status assigned when the registration is under review.
      
    - Ready for matching – Status assigned when review is completed, and the household is ready to be matched with a potential house owner.
      
    - Match confirmed – Status assigned when there is a match between the registered household and a host family or landlord.

-	The registration status can be seen under the overview of the affected household entity and the status for each household can be updated by;
    
    - Clicking on the household ID
      
    - Navigate to status
      
    - Update registration status
 
- The registration status can be manually updated to align with the different stages of the application process. Update of registration status can also be automated based on needs of NS.

![image](https://github.com/user-attachments/assets/4f57a7e9-3265-4091-ae06-871437933d8e)

**6. How do we detect duplicates?**

-	Detecting duplicates is started when;
  
    - A new registration is created
      
    - After an ID number is changed
      
    - Runs every 5 minutes on every affected household
      
-	Duplicates are checked on:
  
    - The ID number
      
    - If the new ID number matches one already existing, then the new record is marked as a duplicate
      
    - If there is no match on ID number, a duplication check is done on the name which results in the record being marked as unique or as a potential duplicate.
      
    - If the record is potentially a duplicate, further verification must be done
      
-	Duplicate status:
  
    - Unique
      
    - Duplicate: ID Number
      
    - Potential Duplicate: Name 



