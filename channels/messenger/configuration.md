# Configuration

The Messenger channel on CSML Studio offers some configuration options. More will be added over time!

## Welcome Flow

When a user starts using your bot, the first thing they will see is a Get Started button (the text will be automatically translated in their own configured language and can not be changed). In the background, a `"GET_STARTED"` payload is sent to the bot.

![](../../.gitbook/assets/demomessenger-1.gif)

This setting helps you configure which flow will be triggered by this specific payload. By default it will be the bot's default flow, but you might want to have a different behavior for what happens when users connect to your bot for the very first time (or when they have deleted the conversation before and want to start anew).

To configure a welcome flow, simply select it in the dropdown list the flow you want to run when the user clicks on the Get Started button.

![](../../.gitbook/assets/capture-de-cran-2020-04-20-17.54.10.png)

## Referral Parameters

You can use [Referral (or Ref Parameters)](https://developers.facebook.com/docs/messenger-platform/discovery/m-me-links) to directly send users to various sections of your chatbot instead of the standard Welcome Flow. There are two scenarios:

* If the user has never used your bot before (or has deleted their conversation), they will be shown the default Get Started button but when they click on it, they will reach the target flow instead of the welcome flow
* If the user has already used the bot, they will directly go to the defined flow, in place of where they were before.

If a user uses a link with a Ref parameter that is not configured properly, the regular behaviour will persist (the Get Started button will redirect to the welcome flow, and existing conversations will simply continue).

There are two ways to use Ref parameters to redirect to flows. You can either configure them in the channel's settings page by adding connections between custom Ref parameters and a target flow:

![](<../../.gitbook/assets/image (120).png>)

Or you can use the following special syntax:

```yaml
# will redirect to the flow called NAME_OF_FLOW
https://m.me/12345678901234?ref=FLOWID:NAME_OF_FLOW
```

The main advantage of the second syntax is that you can generate the links on the go; however, the first method is more flexible as you can easily change where a link is redirected even after it is created, and the content of the Ref parameter is entirely customizable.

## Persistent Menu

Messenger makes it possible to add a [persistent menu](https://developers.facebook.com/docs/messenger-platform/send-messages/persistent-menu/#the-persistent-menu) to your bots.

![The default persistent menu for your bot](../../.gitbook/assets/capture-de-cran-2020-04-20-18.05.14.png)

We offer a simple way to set precisely the persistent menu you want, by letting you add a JSON-formatted payload to set as the bot's persistent menu. Any valid persistent menu configuration is accepted.

![](../../.gitbook/assets/capture-de-cran-2020-04-20-18.04.04.png)

## Metadata

This is not really a configuration option, but know that the `_metadata` object inside your flows will contain some info about your user: their `name`, `first_name`, and `last_name`  will be accessible in the conversation's metadata, unless they are not correctly set in their profile.

{% hint style="warning" %}
There is also an `id` field, however this is not the user's real ID but is called an [app-scoped user ID](https://developers.facebook.com/docs/workplace/third-party-apps/development#user-ids). It can not be related back to the user's actual Facebook ID.
{% endhint %}
