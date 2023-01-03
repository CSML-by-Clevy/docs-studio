# Customization

## Referral Parameter

You can launch a specific flow (and step) instead of the default **Welcome Flow** when loading the Assistant by providing a `ref` query parameter in its URL.

To force the launch of a specific flow when opening the Assistant URL, use the following special syntax:

```yaml
# will redirect to the step NAME_OF_STEP in the flow called NAME_OF_FLOW
https://chat.csml.dev/s/abc12345678901234?ref=target:NAME_OF_STEP@NAME_OF_FLOW

# or, if no step is provided, the `start` step will be used
https://chat.csml.dev/s/abc12345678901234?ref=target:NAME_OF_FLOW
```

## Injecting Conversation Metadata

By default, the Assistant channel does not include any specific context about the conversation (see the `_metadata`  object [documentation](https://docs.csml.dev/language/memory/temporary-and-long-term-variables#user-context)). In some cases, it can be useful to load the Assistant (or Widget) with pre-existing metadata.

Some common scenarios:

* **the bot is loaded in a website where the user is already known**: in that case, we may be interested in injecting the user's context (name, email...) inside the conversation.
* **the user is authentified on the parent website**: in that case, we may want to inject an authentication token into the user's conversation for subsequent calls.
* **the same bot is used across several websites and we want to know which website the user is currently visiting**: in that case we can inject a unique website identifier into the conversation.

![In this example, the chatbot already knows the user's email address and first name](<../../.gitbook/assets/image (68).png>)

The injected data is available in the `_metadata` global variable, available in every flow.\
The code of the example above is:

```cpp
start:
  say "Hi {{_metadata.firstname}}"
  say QuickReply(
    "Your email address is: {{_metadata.email}}. Do you confirm?",
    buttons=[Button("yes"), Button("no")]
  )
  hold
```

To add custom metadata in your Assistant, simply add the encoded (with [javascript's encodeURIComponent function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/encodeURIComponent)) JSON string of the metadata you want to inject to the query parameters of the URL. The URL of the Assistant in the example above would be:

```
{ASSISTANT_URL}?metadata=%7B%22firstname%22%3A%22Jane%22%2C%22email%22%3A%22jane.doe%40company.com%22%7D
```

## Customizing the UI

You can change the appearance of the Assistant by visiting the **Design** tab of the configuration panel. This lets you have even more control over the final experience for your end users, and match your own branding even better!

Many elements are configurable:

* Chatbot avatar, header card color and background image
* User bubble colors
* Hiding the CSML branding
* Disabling the speech input
* And many others!

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>
