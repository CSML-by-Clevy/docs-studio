# Features and Limitations

## Components

As you can expect, not all CSML components work well with a SMS chatbot, as there is no support for any visual component or buttons. However you can use all of the following standard components:

* Text
* Question \(buttons will be added in a new line under the question's title\)
* Image

Other components will be automatically reduced to simple text components.

## Metadata

Each call made to CSML Studio will have a number of metadata, based on what information is provided by Twilio. An example `_metadata` object would look like this:

```javascript
{
  "ToCountry": "FR",
  "ToState": "",
  "SmsMessageSid": "SMfaXXXX",
  "NumMedia": "0",
  "ToCity": "",
  "FromZip": "",
  "SmsSid": "SMfaXXXXX",
  "FromState": "",
  "SmsStatus": "received",
  "FromCity": "",
  "Body": "Hello",
  "FromCountry": "FR",
  "To": "+33644648719",
  "ToZip": "",
  "NumSegments": "1",
  "MessageSid": "SMfaXXXX",
  "AccountSid": "ACa6XXXX",
  "From": "+336XXXXXXX",
  "ApiVersion": "2010-04-01",
  "_channel": {
    "type": "twilio-sms",
    "name": "XXXXXXXXXXXX"
  }
}
```

