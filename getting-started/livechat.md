# Livechat

With CSML Studio, you can decide to bypass CSML and get your users to talk to a human agent instead! This is especially useful if the user needs help beyond what the chatbot can propose.

In order to get your users to talk to your human agents over livechat, you will need:

* a CSML chatbot and channel setup
* a supported Livechat platform
* a special flow to handle livechat requests

## Configuring a Livechat platform in CSML Studio

In this example, we are going to use [Gorgias](https://www.gorgias.com/), a support platform specialized in e-commerce. To get started, go to your bot's **Settings &gt; Livechat** then select Gorgias as your livechat support platform.

![](../.gitbook/assets/image%20%2819%29.png)

In your Gorgias backoffice, visit Settings &gt; REST API and copy/paste the information in the next screen:

![](../.gitbook/assets/image%20%2825%29.png)

Then, in Gorgias, go to **Integrations &gt; HTTP &gt; Add new integration**, give it a name and description, check only the "ticket-message-created" event, then copy/paste the following URL under **URL:**

```text
https://clients.csml.dev/v1/livechat/gorgias/receive?external_id={{ticket.external_id}}&ticket_id={{ticket.id}}&event_type={{event.type}}&event_id={{event.id}}&message_id={{event.object_id}}&text={{message.body_text}}&from_agent={{message.from_agent}}
```

![](../.gitbook/assets/image%20%2823%29.png)

When you are done, click **Save** both in Gorgias and in CSML Studio. Voilà, your bot now supports livechat!

## Using Livechat in your bot

Using livechat in your flows is very easy. You can find an example implementation to import in CSML Studio [here on github](https://github.com/CSML-by-Clevy/CSML-livechat-demo).

To start a livechat session, the user needs to specifically request a livechat session with an available agent. This is achieved by getting the user to send the payload `LIVECHAT_SESSION_START`. When this happens, your CSML chatbot stops receiving events, and all messages are sent to the livechat backend of your choice.

To end a session, the user must send the payload `LIVECHAT_SESSION_END` . To do this, we recommend that your agent sends a "signing off" message containing that payload, which will be automatically transformed into an adequate button.

The session will also expire if no message is exchanged between the agent and the user within 30 minutes. When that happens, an event is sent to your bot with the payload `LIVECHAT_SESSION_EXPIRED`. 

This example flow explains in detail the lifecycle of a livechat request:

{% embed url="https://gist.github.com/frsechet/3fff50049b23c65abaf73e3431be9514" caption="https://gist.github.com/frsechet/3fff50049b23c65abaf73e3431be9514" %}

## Tips and tricks

### Using macros

You can configure a macro in Gorgias to trigger the `LIVECHAT_SESSION_END` event under **Settings &gt; Macros**.

![](../.gitbook/assets/image%20%2822%29.png)

### Getting customer information

Wherever possible, we are trying to pass the metadata information about the user to the livechat backend. For instance here is a demo with the test webapp:

![](../.gitbook/assets/image%20%2824%29.png)

