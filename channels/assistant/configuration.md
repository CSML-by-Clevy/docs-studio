# Configuration

## General information

The settings panel has a few options to allow you to configure the Assistant. Each Assistant must have a name, and you can also add an optional description and logo.

## Welcome flow

When a user arrives on the page, the chatbot welcomes them with a flow. It can be any flow, but by default it is the **Default flow**.

If you do not want a welcome interaction at all, create an empty flow and use that as the Welcome flow!

## Menu

The Assistant channels lets you add shortcuts to either flows or external websites:

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

This will show as a list of searchable shortcuts in the sidebar in full-screen view, or at the top of the input bar in mobile/widget view:

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Full-screen view</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption><p>Mobile / Widget view. The + icon on the right side opens a panel with the searchable list of all shortcuts!</p></figcaption></figure>

## Autocomplete

The autocomplete feature helps your chatbot provide a list of up to 5 items that are contextualized to what the user is currently typing. Think of it as quickly hitting one of the first google search results!

![](<../../.gitbook/assets/image (122) (1) (1) (1).png>)

To configure Autocomplete, you need to have a backend endpoint that will handle the requests and respond accordingly. You can configure this endpoint in the Assistant's configuration panel:

![](<../../.gitbook/assets/image (121) (1).png>)

The request that will be performed by the Assistant will be as follows:

```
curl -X "POST" "https://my.example.com/autocomplete?token=some-auth-token" \
     -H 'Content-Type: application/json;charset=utf-8' \
     -d $'{"text": "Give me the best result"}'
```

Your endpoint must return results within 5 seconds as an `application/json` content-type, formatted as an array of maximum 5 results containing a title, optional highlighting matches, and the corresponding payload.&#x20;

```json
[
  {
    "title": "What is the best result?",
    "matches": {
      "highlights": [
        {
          "word": "What",
          "highlight": false
        },
        {
          "word": "is",
          "highlight": false
        },
        {
          "word": "the",
          "highlight": false
        },
        {
          "word": "best",
          "highlight": true
        },
        {
          "word": "result",
          "highlight": true
        },
        {
          "word": "?",
          "highlight": false
        }
      ],
      "text": "What is the best result?",
      "has_highlights": true
    },
    "payload": "RESULT_ONE_PAYLOAD"
  },
  {
    "title": "Another good result",
    "matches": {
      "highlights": [
        {
          "word": "Another",
          "highlight": false
        },
        {
          "word": "good",
          "highlight": false
        },
        {
          "word": "result",
          "highlight": true
        }
      ],
      "text": "Another nice result",
      "has_highlights": true
    },
    "payload": "ANOTHER_RESULT_PAYLOAD"
  }
]
```

When a user selects a result, it will behave as a button click where the text is displayed and the payload is sent to the chatbot.

### Enabling/disabling autocomplete

If an autocomplete endpoint is set, it will be enabled by default. However, it can be disabled or reenabled dynamically in your CSML script:

```cpp
say Autocomplete(false)
say Autocomplete(true)
```

{% hint style="info" %}
Autocomplete status is not persisted across page reloads. When reloading the page, this will always be set to `true` by default!
{% endhint %}
