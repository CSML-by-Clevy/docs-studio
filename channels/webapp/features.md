# Features

## Components

The Webapp channel support all default components as specified on the [Components documentation](https://docs.csml.dev/language/key-concepts/sending-receiving-messages/message-payloads).

The broadcasting API is currently not supported on this channel.

## Injecting conversation metadata

By default, the webapp channel does not include any specific context about the conversation \(see the `_metadata`  object [documentation](https://docs.csml.dev/language/memory/temporary-and-long-term-variables#user-context)\). In some cases, it can be useful to load the webapp \(or chatbox\) with pre-existing metadata.

Some common scenarios:

* **the bot is loaded in a website where the user is already known**: in that case, we may be interested in injecting the user's context \(name, email...\) inside the conversation.
* **the user is authentified on the parent website**: in that case, we may want to inject an authentication token into the user's conversation for subsequent calls.
* **the same bot is used across several websites and we want to know which website the user is currently visiting**: in that case we can inject a unique website identifier into the conversation.

![In this example, the chatbot already knows the user&apos;s email address and first name](../../.gitbook/assets/image%20%2870%29.png)

The injected data is available in the `_metadata` global variable, available in every flow. The code of the example above is:

```cpp
start:
  say "Hi {{_metadata.firstname}}"
  say QuickReply(
    "Your email address is: {{_metadata.email}}. Do you confirm?",
    buttons=[Button("yes"), Button("no")]
  )
  hold
```

### Chatbox

To add custom metadata in a chatbox, you need to add a `data-webapp-metadata` [custom data attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/data-*) to the chatbox initialization script tag that contains the encoded \(with [javascript's encodeURIComponent function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent)\) JSON string of the metadata you want to inject. The example above uses the following script:

```markup
<script
  src="{CHATBOX_URL}"
  id="clevy-chatbox"
  data-webapp-metadata="%7B%22firstname%22%3A%22Jane%22%2C%22email%22%3A%22jane.doe%40company.com%22%7D"
  async></script>
```

### Webapp

To add custom metadata in a webapp, simply add the same encoded metadata JSON string to the query parameters of the webapp's URL. The URL of the webapp in the example above would be:

```text
{WEBAPP_URL}?metadata=%7B%22firstname%22%3A%22Jane%22%2C%22email%22%3A%22jane.doe%40company.com%22%7D
```

