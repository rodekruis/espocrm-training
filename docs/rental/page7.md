EspoCRM has the built-in functionality for sending SMS, but it's not shipped with any provider implementation. The official [SMS Providers](https://github.com/espocrm/ext-sms-providers/) extension includes implementations for the following SMS providers:

  Twilio
  
  Spryng
  
  seven
  
  smstools
  
  SerwerSms
  
  Verimor
  
  GatewayAPI

Out of the box, it's possible to send SMS from a Formula script or from a PHP code. The [VoIP Integration](https://www.espocrm.com/extensions/voip-integration/) provides also the ability to send SMS through the UI (only for the Twilio provider).


# Setting up # 
Download the extension package from the GitHub repository (under the Assets section). Then upload and install the package in Espo at Administration > Extensions.

After the SMS Providers extension is installed, go to Administration > SMS and select the SMS Provider you want to use from the dropdown list. Also, in the SMS From Number field, enter the number with the country code (e.g. +11111111111) from which you will be sending SMS messages.

Next, go to Administration > Integrations, select your provider, and set up needed credentials and parameters.

# Messages can have the following status: # 

  - Not sent -> person has not received the message 

  - Ready to be sent -> person will receive a message shortly 

  - Queued -> message to this person is in the queue to be sent 

  - Sent -> message is sent 

  - Failed -> sending the message was not successful 
