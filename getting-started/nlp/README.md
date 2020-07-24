# Natural Language Processing

CSML Studio allows you to use your own pre-trained Natural Language Processing \(NLP\) service directly in your CSML chatbots with very little configuration. You can easily setup your favorite NLP provider in **Bot Settings &gt; NLP**:

![](../../.gitbook/assets/image%20%2828%29.png)

When a NLP provider is configured, all `text` events will be sent to the NLP provider and returned either as a `payload` event if an intent is found, or untouched if no intent is found.

A few additional properties are set in the resulting event:

* `event._nlp_provider`: contains details about the NLP provider integration
* `event._nlp_result`: contains the raw response from the NLP provider request
* `event._original_event`: contains the original, untouched event. Only set if an intent is found.

## Using NLP in your flows

You can now use the event by matching a found intent with a flow command, by setting that intent as one of the accepted commands for a flow:

![](../../.gitbook/assets/image%20%2827%29.png)

Alternatively, you can also decide to match buttons or other actions within a flow with the found data. For instance, you can use NLP to detect a `YES_INTENT`  and match it without having to list all the possible ways to say "yes" in the button's `accepts` array.

```cpp
start:

  say Question(
    "Do you like chocolate?",
    buttons=[
      Button("Yes", accepts=["YES_INTENT"]) as btny,
      Button("No", accepts=["NO_INTENT"]) as btnn,
    ]
  )
  hold
  
  if (event match btny) say "I knew it!"
  else if (event match btnn) say "I think you are lying..."
  
  goto end
```

{% hint style="info" %}
**Caveat**: using a NLP provider will send all your text events to that provider, adding some additional delay in the request handling. If you don't need NLP for your use case \(and many great chatbot use cases don't need any NLP\), you also don't need to setup a NLP provider. This is completely optional.
{% endhint %}

