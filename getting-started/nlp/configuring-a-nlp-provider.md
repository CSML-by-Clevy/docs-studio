# Configuring a NLU Provider

## Using SaaS providers

CSML Studio currently supports the following NLP providers:

* Dialogflow ([read our blog post](https://blog.csml.dev/connecting-dialogflow-with-a-csml-chatbot/))
* SAP Conversational AI (formerly Recast.ai)
* Amazon Lex
* Microsoft LUIS
* Rasa
* Wit.ai
* IBM Watson
* Custom Webhook

Please refer to each provider's documentation for more information on how to generate credentials. CSML Studio supports the most common and secure way of connecting to these providers.

If your favorite provider is not in this list, please reach out to [contact@csml.dev](mailto:contact@csml.dev).

## Using the Custom Webhook integration

You can also add a custom NLP engine by using the custom Webhook integration. This is especially useful if we don't currently support your NLP provider of choice or if you are running your NLP services on premise.

To use the Webhook integration, simply provide a URL that we can send a POST request to, with the following body:

```javascript
{
  "text": "TEXT_TO_ANALYZE"
}
```

The URL may contain query parameters, for example with an API Key for authentication purposes.

When called, this endpoint must return the response in the following form:

```javascript
{
  // intent can also be null if no intent is found
  "intent": { 
    "name": "NAME_OF_INTENT", 
    "confidence": 0.84
  },
  "alternative_intents": [ 
    // ... other matching intents
  ],
  "entities": {
    "someEntity": [
      {
        "value": "somevalue",
        "metadata": { 
          // ... any additional information about entity
        },
      },
      // ... other values for the same entity
    ],
    // ... other entities
  }
  // ... any additional data: sentiment analyzis, language...
}
```

You can test this endpoint directly on the configuration page.
