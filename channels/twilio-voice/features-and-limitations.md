# Features and Limitations

## Conversation design

Designing a callbot is very different from designing a text-based chatbot. There are some extra rules:

* Keep your all your sections short. Nobody wants to listen to \(and can remember\) a huge block of text.
* This integration supports both speech and DTMF inputs. When you can, let the caller use the number pad on their phone!
* It is impossible/difficult to know in advance what language a user will speak, so we recommend using a different phone number/TwiML app for each language that you intend to serve with this chatbot.

## Components

As you can expect, not all CSML components work well with a callbot, as there is no support for any visual component. However you can use all of the following components:

* Text
* Question
* Audio

All remaining components \(including Wait and Typing\) are ignored by the system.

## Metadata

Each call made to CSML Studio will have a number of metadata, based on what information is provided by Twilio. An example `_metadata` object would look like this:

```javascript
{
  "AccountSid": "ACa63XXXXXXXXXXa94",
  "ApiVersion": "2010-04-01",
  "ApplicationSid": "AP95bXXXXXXXXXX17a",
  "CallSid": "CA13bXXXXXXXXXXc6b",
  "CallStatus": "ringing",
  "Called": "+336XXXXXXXXX",
  "CalledCity": "",
  "CalledCountry": "FR",
  "CalledState": "",
  "CalledZip": "",
  "Caller": "+336XXXXXXXX",
  "CallerCity": "",
  "CallerCountry": "FR",
  "CallerState": "",
  "CallerZip": "",
  "Direction": "inbound",
  "From": "+336XXXXXXXXX",
  "FromCity": "",
  "FromCountry": "FR",
  "FromState": "",
  "FromZip": "",
  "To": "+336XXXXXXXXX",
  "ToCity": "",
  "ToCountry": "FR",
  "ToState": "",
  "ToZip": "",
  "_channel": {
    "type": "twilio-voice",
    "name": "XXXXXXXXXXXX"
  }
}
```

## Limitations

* For now, CSML Studio does not support call redirection, but this feature will be added in an upcoming release
* For now, you can not create multilingual Twilio callbots as the language is set in the channels settings. However, this feature can be added upon request, so let us know if you need it!

