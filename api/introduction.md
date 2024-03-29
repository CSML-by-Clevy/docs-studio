# Getting Started

In CSML Studio, every channel generates a set of API keys that you can use to perform various operations, such as managing the bot, sending broadcasts, getting information about current conversations... Channels are external connectors to your bot.

Every channel has different capabilities but all channels rely on the same API methods.&#x20;

## Endpoints

All calls are to be made to `https://clients.csml.dev`.

The API is versioned, and all calls must be prefixed by their version number. The most recent version is `v1`. The API is reachable on route prefix `/api`.

Hence, the complete endpoint for the API is `https://clients.csml.dev/v1/api`.

## Throttling

To ensure the stability of downstream systems, API requests are throttled. Each client (a set of API key/secret) can only send up to 50 reqs/sec. Over this limit, an error code is returned and the request will not be treated.

## Webhook

On the API channel exclusively, you can also register a webhook, which will be called with a POST request every time a message is sent by the bot to the end user. This is a good way to handle the outgoing messages in real time! The body of the webhook call is documented [here](api-reference/chat-api.md#response-body).

{% hint style="info" %}
Your webhook has to respond within 5 seconds with a success code. Calls will not be retried in case of error.
{% endhint %}
