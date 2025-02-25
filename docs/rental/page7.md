# Messages 

EspoCRM has the built-in functionality for sending SMS, but it's not shipped with any provider implementation. The official [SMS Providers](https://github.com/espocrm/ext-sms-providers/) extension includes implementations for the following SMS providers:

  Twilio
  
  Spryng
  
  seven
  
  smstools
  
  SerwerSms
  
  Verimor
  
  GatewayAPI

Out of the box, it's possible to send SMS from a Formula script or from a PHP code. The [VoIP Integration](https://www.espocrm.com/extensions/voip-integration/) provides also the ability to send SMS through the UI (only for the Twilio provider).


**Setting up**

Download the extension package from the [GitHub repository](https://github.com/espocrm/ext-sms-providers/releases) (under the Assets section). Then upload and install the package in Espo at Administration > Extensions.

After the SMS Providers extension is installed, go to Administration > SMS and select the SMS Provider you want to use from the dropdown list. Also, in the SMS From Number field, enter the number with the country code (e.g. +31001111111) from which you will be sending SMS messages.

Next, go to Administration > Integrations, select your provider, and set up needed credentials and parameters.

The templates for the SMS messages in EspoCRM are stored in the entity “Message Templates”. The text of the message is stored in the field “Body”. This text can contain one or more placeholders, which are defined by curly brackets “{ }” and enable you to use the fields of other entities – for example, Contacts – into the message. The syntax that placeholders follow is “{Entity.Field}”, so for example to use the field “registrationDate” of the entity “Contacts” you need to write “{Contacts.registrationDate}”. Once the message is linked to a specific Contact, the placeholders will be replaced by the values of the fields of that Contact. 

**SMS messages can be sent:**

  -	From Contact entity via “mass update”
  -	Using a flowchart

  ![image](https://github.com/user-attachments/assets/c8343f84-06ec-4fc3-bbb1-3664eb86e9ab)



**Create the template in the Message Templates entity:**

![Screenshot (20)](https://github.com/user-attachments/assets/4412251a-df20-43af-be4c-95d15ce8a3cd)

**Use your template to create a message in the Messages entity:**

![Screenshot (21)](https://github.com/user-attachments/assets/c839ddbb-2391-45b9-9449-74dfb9e834ac)

**You can see the delivery status in the Messages list:**

![Screenshot (22)](https://github.com/user-attachments/assets/64aa22d4-1b32-46c7-bc4b-96b47f40e79c)


**Messages can have the following status:**  

  - Not sent -> person has not received the message 

  - Ready to be sent -> person will receive a message shortly 

  - Queued -> message to this person is in the queue to be sent 

  - Sent -> message is sent 

  - Failed -> sending the message was not successful 
