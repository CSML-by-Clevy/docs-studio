# Gorgias

## Configuration

[Gorgias](https://www.gorgias.com/) is a support platform specialized in e-commerce. It is the perfect solution if you are a Shopify or Magento user!

To get started, go to your bot's **Settings > Livechat** then select Gorgias as your livechat support platform.

![](<../../.gitbook/assets/CleanShot 2021-06-04 at 12.37.31@2x.png>)

In your Gorgias backoffice, visit **Settings > REST API** and copy/paste the information in the next screen:

![](<../../.gitbook/assets/image (22) (1).png>)

Then, in Gorgias, go to **Integrations > HTTP > Add new integration**, give it a name and description, check only the "ticket-message-created" event, then copy/paste the following URL under **URL:**

```
https://clients.csml.dev/v1/livechat/gorgias/receive?external_id={{ticket.external_id}}&ticket_id={{ticket.id}}&event_type={{event.type}}&event_id={{event.id}}&message_id={{event.object_id}}&text={{message.body_text}}&from_agent={{message.from_agent}}
```

![](<../../.gitbook/assets/image (24).png>)

When you are done, click **Save** both in Gorgias and in CSML Studio. Voilà, your bot now supports livechat!

## Using macros

You can configure a macro in Gorgias to trigger the `LIVECHAT_SESSION_END` event under **Settings > Macros**.

![](<../../.gitbook/assets/image (23) (1).png>)

## Getting customer information

Wherever possible, we are trying to pass the metadata information about the user to the livechat backend. For instance here is a demo with the test webapp:

![](<../../.gitbook/assets/image (25).png>)
