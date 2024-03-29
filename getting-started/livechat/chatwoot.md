# Chatwoot

[Chatwoot](https://www.chatwoot.com) is an open-source livechat platform, with an online SaaS version as well as a self-hosted version. If you are looking for a livechat solution that you can have full control over, or with a free plan if you want the SaaS version, we recommend Chatwoot!

To get started, go to your bot's **Settings > Livechat** then select Chatwoot as your livechat support platform.

![](<../../.gitbook/assets/CleanShot 2021-06-04 at 12.37.58@2x.png>)

You will need to retrieve:

* the URL of your Chatwoot instance. If you are using chatwoot.com, it will be `https://app.chatwoot.com`&#x20;
* your access token (which you can find at the bottom of your profile settings) and&#x20;

![](<../../.gitbook/assets/image (30).png>)

Hit **Save**, and a dedicated inbox will be created for you!

## Canned Responses

We recommend you configure a "Signing off" canned response in Chatwoot to trigger the `LIVECHAT_SESSION_END` event under **Settings > Canned Responses**.

![](<../../.gitbook/assets/image (31) (1).png>)

You can simply copy and paste the text below, or adjust to your liking - just make sure that the LIVECHAT\_SESSION\_END is at the end of the content.

```
Let us know if we can do anything else for you - we are here to help.

LIVECHAT_SESSION_END
```

