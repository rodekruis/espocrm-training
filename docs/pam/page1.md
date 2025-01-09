**PAM (People Affected Management) template** 
is a standard EspoCRM template for managing affected persons data. It contains individuals contact details, information about household composition, assistance projects run by a National Society, tasks for the assigned team, history of communication and support provided. When linked to another entity in EspoCRM, data can be used for various assistance programs: there will be no need to fill in the beneficiary's data in a new form, the operator will be able to select a name from the list and include a person or a household in any project. 

# Persons Affected entity 
This entity contains contact information of individuals. Click the 'Create Person Affected' button in the upper right corner and fill in the form.

![Screenshot (582)](https://github.com/user-attachments/assets/07e9865c-f5d7-4251-84ca-ab54289c5eac)

# CRM - Persons Affected Creation Form

This section describes the "Persons Affected" creation form in the CRM system. The form captures all necessary information related to a person affected by an event, and it is structured into multiple sections for organized data entry.

## Form Overview

- **Page Title**: `Persons Affected › create`
  - This page is used for creating a new record for a person affected by a specific situation.

- **Buttons**:
  - **Save**: Submits the form data to save the record.
  - **Cancel**: Cancels the creation process and discards entered data.
  - **More Options (`...`)**: Additional features, settings, or actions may be available here.

## Main Form Sections

The form is divided into the following sections:

### 1. Overview Section

This section includes basic details about the affected person.

- **First Name** (required)
- **Last Name** (required)
- **Other Name**: Optional field for alternate names (e.g., nicknames).
- **Nationality** (required): Dropdown or text field for the person's nationality.
- **Gender** (required): Dropdown to select gender.
- **Date of Birth** (required): Date picker for DOB.
- **Age**: Automatically calculated based on the Date of Birth field.
- **ID Type** (required): Dropdown to select the type of ID (e.g., Passport, National ID).
- **ID Number**: Text field for the ID number associated with the selected ID type.
- **Languages Spoken** (required): Field for specifying spoken languages.

### 2. Address Section

This section collects the person's location information.

- **Country** (required): Dropdown for selecting the person's country of residence.
- **Province**: Field for selecting or entering the province.
- **City**: Field for specifying the city.
- **Postal Code**: Field for entering the postal code.

### 3. Contact Information Section

This section gathers communication details.

- **Phone**: Allows multiple phone numbers, with an option to choose phone types (e.g., Mobile, Home).
  - Edit and delete icons are available for managing phone numbers.
- **Email**: Input for the person's email address.

### 4. Individual Information Section

This section captures additional personal details related to the individual.

- **Disability Type**: Field to specify any disabilities the person may have.
- **Vulnerability Type**: Input for specifying vulnerability factors (e.g., elderly, child, etc.).
- **Is She Pregnant?**: Checkbox to indicate if the person is pregnant.
- **Household**: Dropdown to associate the person with a household.
- **Head of Household**: Dropdown to specify whether the person is the head of the household.

## Right-Side Widgets

- **Assigned User**: Dropdown to assign the person to a specific user in the CRM system.
- **Teams**: Dropdown to assign the person to specific teams or groups.

---

## Notes

- Fields marked with an asterisk (*) are required for submitting the form.

# Backend Formulas and Logic

### 1. Name Field
- **Logic**: The `name` field is generated dynamically:
  - If `extraName` is provided: `name = firstName + " " + extraName + " " + lastName`.
  - If `extraName` is not provided: `name = firstName + " " + lastName`.

### 2. Age Calculation
- **Logic**: The `age` field is calculated as the difference (in years) between the current date and the `dateofbirth` field.

### 3. Head of Household (HHH) Logic
- If `isThisMemberAHeadOfHouseholdTemp` is set, it updates the `isThisMemberAHeadOfHousehold` field.
- If the person is the Head of Household:
  - The household record is updated with this member's ID and name.
  - All other members in the household are marked as not being the Head of Household.
- If the Head of Household changes:
  - The oldest member is identified and assigned as the new Head of Household.

### 4. Household Statistics Updates
The following fields are recalculated whenever household membership changes:
- `calculatedTempMale`: Number of male members.
- `calculatedTempFemale`: Number of female members.
- `calculatedTempChildren`: Number of children under 18.
- `calculatedTempPregnant`: Number of pregnant women.

### 5. Consistency Checks
- The system verifies if the stored household statistics match the calculated statistics.
- If there is a mismatch, the household record is updated.

### 6. Adding a New Household Member
- When a new person is added to a household:
  - The system recalculates statistics (e.g., gender counts, age groups, pregnancy status) and updates the household record.

