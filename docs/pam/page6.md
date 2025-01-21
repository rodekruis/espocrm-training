# Guide to Importing Data into EspoCRM Using a CSV File

Importing data into EspoCRM from a CSV file is a straightforward process. Follow the steps below to ensure a successful data import.

### **Step 1: Prepare Your CSV File**

- **Format:** Ensure your file is saved in CSV format. Use tools like Excel or Google Sheets to prepare your data.
  
- **Headers:** The first row of the CSV should contain column headers that match the field names in EspoCRM.
  
- **Field Mapping:** If the field names in your CSV differ from those in EspoCRM, make a note to map them during the import process.
  
- **Data Cleanliness:** Ensure the data:
  - Contains no duplicate rows unless intentional.
  - Matches the field types in EspoCRM (e.g., text, numeric, date).
  - Uses consistent date formats (e.g., YYYY-MM-DD).
  - Includes any mandatory fields required by EspoCRM.
    
- **Encoding:** Use UTF-8 encoding to avoid issues with special characters. 

### **Step 2: Access the Import Page**

Navigate to the Import Page, this is usually accessible via the **Administration** tab, and it should look like below:

![image](https://github.com/user-attachments/assets/681c0c06-d565-4713-b03a-05e80c9c97eb)

### **Step 3: Select Import Settings**

**Entity Type**

  - Select the entity you want to import data into (e.g., Contacts, Accounts, Leads).

**File (CSV)**

 - Click the file icon to upload your prepared CSV file.

 - Ensure the file is UTF-8 encoded and follows CSV formatting.

**What to Do?**

- Choose the desired action:
  - **Create Only:** Add new records without affecting existing ones.
  - **Update Only:** Modify existing records without creating new ones.
  - **Create & Update:** Both create new records and update existing ones.
 
### **Step 4: Configure Import Properties**

**Header Row**

  - Leave this box checked if your CSV file has column headers in the first row.

**Field Delimiter**

  - Select the delimiter used in your CSV file (commas ,, semicolons ;, etc.).

**Text Qualifier**

  - Choose the character used to enclose text values (e.g., double quotes ", single quotes ').

**Person Name Format**

  - Specify the name format (e.g., "First Last").

**Date and Time Formats**

  - Match the formats to your CSV file:
    - **Date Format:** Select the correct date format (e.g., YYYY-MM-DD).
    - **Time Format:** Select the correct time format (e.g., HH:mm:ss).
   
  
**Decimal Mark and Currency**

  - Define the decimal symbol (dot . or comma ,) and the currency format if applicable.

**Timezone**

  - Select the appropriate timezone for your data.

**Telephone Country Code**

  - Provide the default country code for phone numbers, if relevant.

**Execute in Idle**

  - Check this box if you are importing large datasets and want the import to run in the background.

**Skip Searching for Duplicates**

  - Check this box to bypass duplicate checks during the import.

**Silent Mode**
  - Check this box if you do not want any flowcharts or workflows to be triggered by the import.


### **Step 5: Preview and Start the Import**

1. Once all settings are configured, preview your data in the Preview section.

2. Verify that the data appears as expected.
  
3. Click Start Import to begin.

### **Step 6: Access Next Import Page**

Click next, at the bottom right of the screen to get to the next page, it should look like this:

![image](https://github.com/user-attachments/assets/13dd0f2a-83c4-43b9-9269-a71523611c35)

### **Step 7: Match Field Names**

If the headers in your CSV are the same as the field names in PAM, they will automatically link. However, if they are not the same, you will have to manually link the fields. If you are importing a file with many columns, it is _strongly_ recommended to make sure the field names are correct in the CSV as manually linking these fields can be a time consuming process.

### **Step 8: Set Default Values**

Set any values that will be the same for all newly created records, such as country, that are not included in the CSV.

### **Step 9: Run Import**

Press the 'Run Import' button, and you will proceed to the final page, which will look like below: 

![image](https://github.com/user-attachments/assets/21ebbcb5-e6a3-401b-9dd4-291b2eff1e66)

Make sure all appears correct, if there are errors, check which rows are affected. If there is a mistake, you can revert the import by pressing the red 'Reverse Import' button in the top right of the screen.


### **Tips for a Successful Import**

**Data Consistency:** Ensure the CSV file matches the field formats in EspoCRM.

**Testing:** Import a small sample first to confirm accuracy.















