# Gorgias

## Configuration

[Gorgias](https://www.gorgias.com/) is a support platform specialized in e-commerce. It is the perfect solution if you are a Shopify or Magento user!

To get started, go to your bot's **Settings &gt; Livechat** then select Gorgias as your livechat support platform.

![](../../.gitbook/assets/image%20%2819%29.png)

In your Gorgias backoffice, visit **Settings &gt; REST API** and copy/paste the information in the next screen:

![](../../.gitbook/assets/image%20%2825%29.png)

Then, in Gorgias, go to **Integrations &gt; HTTP &gt; Add new integration**, give it a name and description, check only the "ticket-message-created" event, then copy/paste the following URL under **URL:**

```text
https://clients.csml.dev/v1/livechat/gorgias/receive?external_id={{ticket.external_id}}&ticket_id={{ticket.id}}&event_type={{event.type}}&event_id={{event.id}}&message_id={{event.object_id}}&text={{message.body_text}}&from_agent={{message.from_agent}}
```

![](../../.gitbook/assets/image%20%2823%29.png)

When you are done, click **Save** both in Gorgias and in CSML Studio. Voilà, your bot now supports livechat!

## Using macros

You can configure a macro in Gorgias to trigger the `LIVECHAT_SESSION_END` event under **Settings &gt; Macros**.

![](../../.gitbook/assets/image%20%2822%29.png)

## Getting customer information

Wherever possible, we are trying to pass the metadata information about the user to the livechat backend. For instance here is a demo with the test webapp:

![](../../.gitbook/assets/image%20%2824%29.png)

