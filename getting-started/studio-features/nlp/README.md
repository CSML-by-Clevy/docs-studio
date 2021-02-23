# Natural Language Processing

CSML Studio allows you to use your own pre-trained Natural Language Processing \(NLP\) service directly in your CSML chatbots with very little configuration. You can easily setup your favorite NLP provider in **AI & NLU &gt; NLU Configuration**:

![](../../../.gitbook/assets/image%20%2879%29.png)

By default, all bots run in Strict Mode, where the input needs to exactly match one of the given rules to trigger a flow.

When a NLP provider is configured, all `text` events will be sent to the NLP provider and returned either as a `payload` event if an intent is found, or untouched if no intent is found.

A few additional properties are set in the resulting event:

* `event._nlp_provider`: contains details about the NLP provider integration
* `event._nlp_result`: contains the raw response from the NLP provider request
* `event.text`: contains the original text input

## Using NLU in your flows

You can now use the event by matching a found intent with a flow command, by setting that intent as one of the accepted commands for a flow, using the [AI Rules](../ai-rules.md) feature.

Alternatively, you can also decide to match buttons or other actions within a flow with the found data. For instance, you can use NLP to detect a `YES_INTENT`  and match it without having to list all the possible ways to say "yes" in the button's `accepts` array.

```cpp
start:

  say Question(
    "Do you like chocolate?",
    buttons=[
      Button("Yes", accepts=["intent:YES_INTENT"]) as btny,
      Button("No", accepts=["intent:NO_INTENT"]) as btnn,
    ]
  )
  hold
  
  if (event match btny) say "I knew it!"
  else if (event match btnn) say "I think you are lying..."
  
  goto end
```

{% hint style="info" %}
**Caveat**: when using a NLU provider, CSML Studio will send all text events to that provider, adding some additional delay in the request handling. If you don't need NLU for your use case \(and many great chatbot use cases don't need any NLP\), you also don't need to setup a NLU provider. This is completely optional.
{% endhint %}

{% hint style="success" %}
**CSML Tip**: except in very specific scenarios, **you should not map your NLU provider's default or fallback intent to a CSML flow**, as this would result in a behavior where every input that is not a detected intent triggers that flow.   
  
Instead, fallback intents should continue any currently open conversation or automagically fallback to the default CSML when needed.
{% endhint %}

