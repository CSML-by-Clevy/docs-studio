---
description: How to configure a callbot on CSML Studio with Twilio Voice
---

# Installation

## Setup Twilio

### Step 1: Purchase a Twilio phone number compatible with Programmable Voice

To get started, you will need to create a Twilio account and purchase a phone number in the country of your choice. [Twilio has a documentation on this topic](https://support.twilio.com/hc/en-us/articles/223135247-How-to-Search-for-and-Buy-a-Twilio-Phone-Number-from-Console). The only point of attention is that you must make sure that the number you purchase has Voice capabilities. Please keep in mind that depending on your country of origin, the requirements may differ, and Twilio may ask you for business verification. Keep track of this phone number (including the country code) as you are going to need to add it later to CSML Studio!

### Step 2: Configure a TwiML App

TwiML is Twilio's own markup language for connecting with their programmable interfaces. You will need to create a new app by [visiting the TwiML dashboard](https://www.twilio.com/console/voice/twiml/apps) and clicking on **Create a new app**, then fill the Voice Request URL and provide with this URL: [https://clients.csml.dev/v1/twilio/voice/request](https://clients.csml.dev/v1/twilio/voice/request).

![](<../../.gitbook/assets/image (48).png>)

Once you have created this app, find its **Application SID** by clicking on its name again on the list of TwiML apps, and keep this information for later.

You will then need to link this Application with the phone number you created earlier. To do so, visit the [Phone Numbers sections of the Twilio console](https://www.twilio.com/console/phone-numbers/incoming), and click on your number to configure it. Under Voice & Fax, select Accept incoming voice calls, configure with TwiML App and pick the TwiML App we provided earlier.

![](<../../.gitbook/assets/image (50).png>)

### Step 3: Security and Authorization

The last step is to provide CSML Studio with means to make sure that the requests that are sent to the Twilio Voice endpoint are indeed coming from Twilio. To do so, [visit your Twilio Project Settings](https://www.twilio.com/console/project/settings) and **copy your Account SID and Auth Token**, found under API Credentials:

![](<../../.gitbook/assets/image (51).png>)

## Setup CSML Studio

To setup your Twilio Callbot in CSML Studio, you will simply need to visit the Channels section and create a new Twilio (Voice) channel. Then simply fill the required fields with the information you gathered earlier.

![](<../../.gitbook/assets/image (53).png>)

About the Language field: as Twilio provides Speech-To-Text and Text-To-Speech capabilities, it must know in advance in what language the user is supposed to speak. [The list of all supported languages is available in Twilio's documentation](https://support.twilio.com/hc/en-us/articles/223132827-What-Languages-can-the-Say-TwiML-Verb-Speak-). You must specify the full ISO locale code (i.e `en-US`, `fr-FR`...).

Once you click on **Submit**, your bot is ready to use!
