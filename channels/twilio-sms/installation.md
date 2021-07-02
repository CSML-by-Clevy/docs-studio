# Installation

## Setup Twilio

### Step 1: Purchase a Twilio phone number compatible with Programmable Messaging

To get started, you will need to create a Twilio account and purchase a phone number in the country of your choice. [Twilio has a documentation on this topic](https://support.twilio.com/hc/en-us/articles/223135247-How-to-Search-for-and-Buy-a-Twilio-Phone-Number-from-Console). The only point of attention is that you must make sure that the number you purchase has Messaging capabilities. Please keep in mind that depending on your country of origin, the requirements may differ, and Twilio may ask you for business verification. Keep track of this phone number \(including the country code\) as you are going to need to add it later to CSML Studio!

### Step 2: Configure the messaging webhook

To configure the webhook, you can either use a TwiML app c or directly set a webhook in the messaging configuration panel. Either way, you will need to set the HTTP POST webhook to [https://clients.csml.dev/v1/twilio/sms/request](https://clients.csml.dev/v1/twilio/sms/request), for example like so:

![](../../.gitbook/assets/image%20%28100%29.png)

### Step 3: Security and Authorization

The last step is to provide CSML Studio with means to make sure that the requests that are sent to the Twilio Voice endpoint are indeed coming from Twilio. To do so, [visit your Twilio Project Settings](https://www.twilio.com/console/project/settings) and **copy your Account SID and Auth Token**, found under API Credentials:

![](../../.gitbook/assets/image%20%2851%29.png)

## Setup CSML Studio

To setup your Twilio SMS channel in CSML Studio, you will simply need to visit the Channels section and create a new Twilio SMS channel. Then simply fill the required fields with the information you gathered earlier.

![](../../.gitbook/assets/image%20%2899%29.png)

Once you click on **Submit**, your bot is ready to use!

