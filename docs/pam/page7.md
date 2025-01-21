
# How to integrate EspoCRM with Kobotoolbox 

In this example we are using the IFRC server. 
There are two options for doing this:

1. Make a direct connection between KoBo and espoCRM through the REST functionality of KoBo
2. Use KoboConnect
   
For option 1 you don't need additional resources, but it has the following drawbacks:

- There is no support for images or other attachments
- It can take a lot of time to configure in the xlsform
- Debugging can be difficult and time consuming
  
Option 2 only requires some extra configuration of the Kobo REST Service.

All options are explained below, but first universal preparation steps are listed:

***Preparation:*** 

- Create all the fields in EspoCRM that you will need
- Create the corresponding layout(s)
- Create an API user in EspoCRM with a corresponding role
  
# Option 1: Direct connection through KoBo REST service

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
  
# Option 2: use KoboConnect
See KoboConnect docs. Note: if debugging is needed, this can be done by checking the logs of EspoCRM

Warning

Be aware that boolean values are not send over the REST service by Kobo Also, fields in EspoCRM cannot be Read-only, because it doesnot allow the REST service to enter information
