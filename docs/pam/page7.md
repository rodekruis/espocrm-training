# Registration with Kobo

Registration (any data collection) can be done efficiently using Kobo and the data can be pulled to EspoCRM. To do this, you need to **integrate EspoCRM with Kobotoolbox**. 

In this example we are using the [IFRC Server](https://kobo.ifrc.org/).
There are two options for doing this:

1. Make a direct connection between KoBo and espoCRM through the REST functionality of KoBo
2. Use KoboConnect
   
For option 1 you don't need additional resources, but it has the following drawbacks:

- There is no support for images or other attachments
- It can take a lot of time to configure in the xlsform
- Debugging can be difficult and time consuming
  
Option 2 only requires some extra configuration of the Kobo REST Service.

**Preparation:** 

- Create all the fields in EspoCRM that you will need
- Create the corresponding layout(s)
- Create an API user in EspoCRM with a corresponding role
  
## Option 1: Direct connection through KoBo REST service

- Create your form in your preferred way
- Download the xlsform
- Create hidden fields with the "name" corresponding to the fieldnames in espoCRM
- Use calculations to "map" the answers to the questions of the survey, for example:
- Upload the updated xlsForm in KoBo
- Go to your form, click on settings and then REST Services
- Fill in the following things
  - endpoint: this is the API endpoint for the entity that you want to make a record for
  - Select fields subset: type all the fields you want to push to espoCRM (tip: you can paste a comma separated list)
  - Custom HTTP Headers: X-Api-Key - copy & paste the api key from the api user in EspoCRM
- Test and debug
  
## Option 2: use KoboConnect
Using the [kobo-to-espocrm](https://kobo-connect.azurewebsites.net/docs#/default/kobo_to_espocrm_kobo_to_espocrm_post) endpoint it is possible to save a Kobo submission as one or more entities in EspoCRM.

### Basic setup

1. Define which questions in the Kobo form need to be saved in which entity and field in EspoCRM.
2. In EspoCRM,
   - Create a role (Administration>Roles), set `Access` to the target entity on `enabled`, with the permission on `yes` to `Create` (if you need to update records, also add `Read` and `Edit`).
   - Create an API user (Administration>API Users), give it a descriptive `User Name`, select the previously created role, make sure `Is Active` is checked and that `Authentication Method` is `API Key`. After saving, you will see a newly created API Key which is needed for the next step.
3. [Register a new Kobo REST Service](https://support.kobotoolbox.org/rest_services.html) for the Kobo form of interest and give it a descriptive name.
4. Insert as `Endpoint URL`
```
https://kobo-connect.azurewebsites.net/kobo-to-espocrm
```
5. Add the following headers under `Custom HTTP Headers`:
   - Under `Name` insert `targeturl` and under `Value` the EspoCRM URL (for example, https://espocrminstancex.com).
   - Under `Name` insert `targetkey` and under `Value` the (newly) created API Key (from EspoCRM API User).
6. For each question, add a header that specifies which Kobo questions corresponds to which entity and field EspoCRM: (tip: this is a manual task. If you want to semi-automatically add headers, read this [section](#create-headers-endpoint) on the creating headers endpoint)
   - The header name (left) must correspond to the Kobo question **name**. (You can check the Kobo question name by going into edit mode of the form, open 'Settings' of the specific question and inspect the `Data Column Name`. Also, the Kobo question names can be found in the 'Data' table with previous submissions. This Kobo question name is different from the [Kobo question label](https://support.kobotoolbox.org/getting_started_xlsform.html#adding-questions) and can not contain spaces or symbols (except the underscore).).
   - The header value (right) must correspond to the EspoCRM entity **name**, followed by a dot (`.`), followed by the specific field **name**. Example: `Contact.name`. (EspoCRM name is different from the EspoCRM label, similar to the difference between Kobo question name and Kobo question label).
    

 
> If you need to send **attachments** (e.g. images) to EspoCRM, add a `Custom HTTP Header` called `kobotoken` with your API token (see [how to get one](https://support.kobotoolbox.org/api.html#getting-your-api-token)).

<img src="https://github.com/rodekruis/kobo-connect/assets/26323051/06de75f3-d02d-4f9f-bb82-db6736542cf5" width="500">



### Advanced setup: select many, repeat groups, etc.

- If you have a question of type `Select Many` (`select_multiple`) in Kobo and you want to save it in a field of type `Multi-Enum` in EspoCRM, add `multi.` before the Kobo question name in the header name.
  - Example header: `multi.multiquestion1`: `Entity.field1`
- If you have a **repeating group** of questions in Kobo:
  - you will need to save each repeated question in a different field in EspoCRM, as specified by a different header;
  - under each header name:
    - insert `repeat.`, followed by the repeating group name, followed by a dot (`.`);
    - then insert a number to specify the number of the repeated question (starting from 0), followed by a dot (`.`);
    - then insert the name of the repeated question after the number;
  - under each header value:
    - as before, insert the entity name, followed by a dot (`.`), followed by the field name in EspoCRM.
  - Example headers:
    - `repeat.repeatedgroup.0.repeatedquestion`: `Entity.field1`
    - `repeat.repeatedgroup.1.repeatedquestion`: `Entity.field2`
  - Not all repeated questions need to be filled in nor saved to EspoCRM.
- If you need to **update** a pre-existing record:
  - add a question of type `calculate` called `updaterecordby` in the Kobo form, which will contain the value of the field which you will use to identify the record;
  - add a header with name `updaterecordby` and as value the name of the field that you will use to identify the record.
- If you need to **avoid sending specific submissions** to EspoCRM:
  - add a question called `skipconnect` in the Kobo form;
  - whenever its value is `1` (based on some condition), the submission will not be sent to EspoCRM.
- If you need to **link the new record with another pre-existing record in** EspoCRM:
  - ensure that the API user has read-access to the related entity;
  - under the header name insert the name of the Kobo question, as usual;
  - under the header value insert the entity name, followed by a dot (`.`), followed by the field name of type `Link` (the one containing the related entity record), followed by a dot (`.`), followed by the field name of the related entity used to relate the two.
  - Example headers:
    - `pcode`: `Entity.AdminLevel1.pcode`
    - `programCode`: `Entity.program.code`



Note: if debugging is needed, this can be done by [checking the logs of EspoCRM](https://github.com/rodekruis/EspoCRM-knowledge-base/wiki/Administration#access-logs-via-ssh-putty)


Be aware that the fields in EspoCRM cannot be Read-only, because it does not allow the REST service to enter information.
