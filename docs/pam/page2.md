# Household Entity Documentation
![image](https://github.com/user-attachments/assets/35223a20-ef7b-497f-9be3-fc2d72cfd539)

## Overview
The Household entity captures and manages data related to households, including the assigned Head of Household (HHH) and calculated demographic statistics.

---
## Interface Explanation 

1. **Name**: Displays the household name generated from the Head of Household's last name.
2. **Head of Household**: Dropdown to assign or update the Head of Household.
3. **Calculated Statistics**:
   - **Calculated Male**: Total number of males in the household.
   - **Calculated Female**: Total number of females in the household.
   - **Calculated Children**: Number of children under 18.
   - **Calculated Pregnant**: Number of pregnant members.
4. **Member Count**: Total number of household members.
5. **Assigned User & Teams**:
   - Fields for assigning specific users or teams for administrative purposes.
## Fields and Behaviors

### 1. **Name Field**
- **Logic**: The `name` of the household is dynamically generated:
  - If a Head of Household is assigned (`cHeadOfHouseHoldId`):
    - The `name` is set to: `"Household " + lastName of Head of Household`.
  - If no Head of Household is assigned:
    - The system attempts to assign the oldest member as the Head of Household and generates the name accordingly.

---

### 2. **Head of Household (cHeadOfHouseHoldId)**
- **Logic**:
  - If `cTempHeadOfHouseHold` is set:
    - This value is used as the Head of Household and then reset to `null`.
  - If no Head of Household is specified:
    - The system automatically assigns the **oldest household member** as the Head of Household.
  - If the assigned Head of Household is not already part of the household:
    - They are added to the list of members (`cPersonAffectedIds`).
  - The system ensures only one member is marked as the Head of Household:
    - Any other member previously marked as HHH will have their status updated to `false`.

---

### 3. **Household Members (cPersonAffectedIds)**
- **Behavior**:
  - This field stores an array of all individuals in the household.
  - The system dynamically updates the list to ensure the Head of Household is always included.

---

### 4. **Demographic Statistics**
- **Fields**: 
  - `calculatedMale`: Number of male members.
  - `calculatedFemale`: Number of female members.
  - `calculatedChildren`: Number of children under 18 years old.
  - `calculatedPregnant`: Number of pregnant women.
  - `memberCount`: Total number of household members.

- **Logic**:
  - If temporary calculated values (`calculatedTempMale`, `calculatedTempFemale`, etc.) are provided:
    - These values are directly assigned to the respective fields and reset to `null`.
  - If no temporary values are available:
    - The system recalculates the statistics based on the attributes of household members (`cPersonAffectedIds`):
      - **Male**: Count members with gender = "Male".
      - **Female**: Count members with gender = "Female".
      - **Children**: Count members with `age < 18`.
      - **Pregnant**: Count members with `isThisMemberAPregnantWoman = true`.

---

### 5. **Member Count (memberCount)**
- **Logic**:
  - The `memberCount` field is calculated as the total number of entries in `cPersonAffectedIds`.

---

## Key System Behaviors

### 1. **Automatic Assignment of Head of Household**
- When no Head of Household is specified, the system:
  1. Identifies the oldest member in the household.
  2. Assigns them as the Head of Household.
  3. Updates their record to mark them as the Head of Household.

---

### 2. **Consistency Checks**
- Ensures all members marked as Head of Household belong to the household.
- Verifies that only one member is marked as the Head of Household at any given time.

---

### 3. **Dynamic Updates**
- When household members or demographics change, the system recalculates:
  - Gender-based counts (`calculatedMale` and `calculatedFemale`).
  - Age-based counts (`calculatedChildren`).
  - Pregnancy count (`calculatedPregnant`).

---



---



