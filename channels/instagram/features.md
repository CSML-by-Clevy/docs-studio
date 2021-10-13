# Features

Instagram Chatbots are quite similar to Messenger Chatbots, but there are quite a few differences. Here is everything you can do with Instagram Chatbots!

## Available components

Messenger channel supports many CSML components: `Text`, `Typing`, `Wait`, `Image`, `Question`, `Button`, `Card`, `Audio`, `Video`, `Url`, `File`.

Note that the `Typing` component is converted to a simpler `Wait` component, and `Carousel` components are entirely unavailable.

Also, all types of `Buttons` do not display at all on the web version of Instagram (but a vast majority of Instagram users are on the mobile app).

## Broadcast

Instagram supports [broadcasts](../../api/api-reference/broadcasts-api.md), with the same limitations as with Messenger. Please refer to the [Messenger Channel documentation](https://docs.csml.dev/studio/channels/messenger/features#broadcast) for more information!

{% hint style="warning" %}
**Failing to respect this rule may get your chatbot and/or page banned from Facebook or Instagram!**
{% endhint %}

## Limitations

In general, all Instagram limitations apply. For example, texts can not be larger than 2000 UTF-8 characters, and attachment sizes (Videos, Audio, Files) can not be larger than 25MB.

Regular buttons are limited to 13 per component. The length of the button title should also never be longer than 20 characters.

You can also refer to the [Messenger Channel documentation](https://docs.csml.dev/studio/channels/messenger/features#limitations) for relevant information on other Facebook limitations.

## Event Metadata

A sample `_metadata`  for an incoming event will be similar to the following object:

```javascript
{
  "_channel": {
    "name": "test_myinstapage",
    "page_id": "866763783487618",
    "type": "instagram"
  },
  "name": "John Doe"
  "id": "1106013791815671",
  "profile_pic":"https://example.com/XXXX"
}
```
