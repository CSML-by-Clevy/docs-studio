# Features and Limitations

## Conversation design

Designing a callbot is very different from designing a text-based chatbot. There are however some extra rules to make a successful callbot:

* Keep your all your sections short. Nobody wants to listen to \(and can remember\) a huge block of text!
* This integration supports both speech and DTMF \(keypad\) inputs. When you can, let the caller use the number keypad on their phone, as it has much better success rates than speech to text!
* It is impossible/difficult to know in advance what language a user will speak, so we recommend using a different phone number/TwiML app for each language that you intend to serve with this chatbot.
* All conversations start at the welcome\_flow define in the channel. Callbot conversations never continue where they left off.
* To hung up on a user, simply reach a `goto end`.
* By default, there is a timeout of 5s on every `hold`. If the user does or says nothing, the conversation stops.

{% hint style="info" %}
Twilio has a web interface to test your chatbot on your TwiML App page. You can use it to test your bot!

**Note: this web interface does not support the CallForwarding component.**
{% endhint %}

![](../../.gitbook/assets/image%20%2852%29.png)

## Components

As you can expect, not all CSML components work well with a callbot, as there is no support for any visual component. However you can use all of the following components:

* Text
* Question
* Audio
* Typing
* Wait

Callbots on CSML Studio also support an additional custom component, `CallForwarding`. This allows redirecting the user to a different phone number. This is very useful in a triage type of chatbots: when the request is qualified enough, you can simply redirect the user to the right person or service!

```cpp
// This will redirect the call to the provided number
say CallForwarding("+33123456789")
```

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

* For now, you can not create multilingual Twilio callbots as the language is set in the channels settings. However, this feature can be added upon request, so let us know if you need it!

