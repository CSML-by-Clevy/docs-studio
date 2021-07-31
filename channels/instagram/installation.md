# Installation

## Setup

### Instagram Business Account

The first thing you need is an instagram business account. Luckily, switching from personal to business account is a straightforward process: simply follow [this guide](https://www.facebook.com/business/help/502981923235522).

{% hint style="warning" %}
Instagram Messaging APIs are currently in [rollout phase 2](https://developers.facebook.com/docs/messenger-platform/instagram/rollout), which means only accounts with 1,000 to 100,000 followers can currently deploy Instagram chatbots. It will be accessible to all accounts later this year.

If your account does not fit this requirement, you can create a test account on Instagram \(starting with `test_`\) and follow the same steps described below.
{% endhint %}

### Facebook Business Page

You will also need a Facebook Business page linked to your Instagram Business account. You can easily create a new page or use an existing one, and connect it to your Instagram account by [following this process](https://www.facebook.com/help/1148909221857370).

## CSML Studio Setup

To connect your Instagram account to your CSML Studio chatbot, visit the **Channels** page, then click on **Instagram** to create a new Instagram channel. Then, follow the Login with Facebook flow, and make sure to select both the Instagram Business Account, and the Facebook Page it is linked with:

![](../../.gitbook/assets/image%20%28109%29.png)

![](../../.gitbook/assets/image%20%28106%29.png)

Also, make sure that all the requested permissions are checked:

![](../../.gitbook/assets/image%20%28104%29.png)

After this flow, you will be presented with a list of your Facebook pages. Select the one that is linked to your Instagram page:

![](../../.gitbook/assets/image%20%28105%29.png)

After a few seconds, you are redirected to a new page. It's done!
