# Configuring a NLP Provider

## Using SaaS providers

CSML Studio currently supports the following NLP providers:

* Dialogflow
* SAP Conversational AI
* Amazon Lex
* Microsoft LUIS

Please refer to each provider's documentation for more information on how to generate credentials. CSML Studio supports the most common and secure way of connecting to these providers.

#### Upcoming providers

We are working on supporting the following additional providers in the short-term:

* Rasa
* IBM Watson
* Huggingface
* Lettria

If your favorite provider is not in this list, please reach out to [contact@csml.dev](mailto:contact@csml.dev).

## Using the Webhook integration

You can also add a custom NLP engine by using the custom Webhook integration. This is especially useful if we don't currently support your NLP provider of choice or if you are running your NLP services on premise.

To use the Webhook integration, simply provide a URL that we can send a POST request to, with the following body:

```javascript
{
  "text": "TEXT_TO_ANALYZE",
  "_client": {
    "user_id": "abcd",
    "channel_id": "efgh",
    "bot_id": "ijkl"
  }
}
```

The URL may contain query parameters, for example with an API Key for authentication purposes.

When called, this endpoint must return the response in the following form:

```javascript
{
  "intent": "NAME_OF_INTENT", // can be null if no intent is found
  "data": { 
    ... any additional data: entities, sentiment analyzis...
  }
}
```

You can test this endpoint directly on the configuration page.

