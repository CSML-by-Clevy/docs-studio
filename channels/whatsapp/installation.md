# Installation

## Prerequisites

There are two prerequisites for installing a Whatsapp bot in the CSML Studio.

1. you MUST have a verified Meta Business account
2. you MUST have a Meta Developer account

And more generally, you must be able to follow this guide to setup a Meta app correctly: [https://developers.facebook.com/docs/whatsapp/business-management-api/get-started](https://developers.facebook.com/docs/whatsapp/business-management-api/get-started).

## Connecting Whatsapp to CSML Studio

In your bot in CSML Studio, go to **Channels** > **Connect a new channel,** then select **Whatsapp**.

In the next screen, enter a name and description for your channel (it is purely informational and can be changed later) and add the required credentials.

![](<../../.gitbook/assets/CleanShot 2022-07-29 at 11.10.11@2x.png>)

The **App ID** and **App Secret** can be found in the app's Basic Settings page:

![](<../../.gitbook/assets/CleanShot 2022-07-29 at 11.11.38@2x.png>)

The **User Access Token,** **Phone Number ID** (_and not the actual phone number!_) and **WhatsApp Business Account ID** can be foud under **Whatsapp > Getting Started**. You can start with one of the Test numbers provided by Facebook, but in production you will want to change that to your own phone number once it is properly configured.

![](<../../.gitbook/assets/CleanShot 2022-07-29 at 11.07.01@2x.png>)

Then, click **Save** to setup the channel. In the following page, you will also receive your Webhook configuration parameters:

![](<../../.gitbook/assets/image (1) (1).png>)

Use these parameters in the **Whatsapp > Configuration** page under **Callback URL** and **Verify token**. Make sure to also **subscribe to the `messages` Webhook field**.

![](<../../.gitbook/assets/CleanShot 2022-07-29 at 11.07.32@2x.png>)

The final step before you can deploy this app to production is to [verify your business](https://www.facebook.com/business/help/2058515294227817) (if not already done), and obtain [the `whatsapp_business_management` permissions](https://developers.facebook.com/micro\_site/url/?click\_from\_context\_menu=true\&country=FR\&destination=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fpermissions%2Freference%2Fwhatsapp\_business\_management\&event\_type=click\&last\_nav\_impression\_id=1KC47D7snVtyQUZe8\&max\_percent\_page\_viewed=30\&max\_viewport\_height\_px=831\&max\_viewport\_width\_px=1512\&orig\_http\_referrer=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fget-started\&orig\_request\_uri=https%3A%2F%2Fdevelopers.facebook.com%2Fajax%2Fdocs%2Fnav%2F%3Fpath1%3Dwhatsapp%26path2%3Dbusiness-management-api%26path3%3Dget-started\&region=emea\&scrolled=true\&session\_id=1Q0luFHipTpQvWDFI\&site=developers).
