# NLP

CSML Studio allows you to use your own trained NLP service directly in your CSML chatbots with very little configuration. You can easily setup your favorite NLP provider in **Bot Settings &gt; NLP**:

![](../../.gitbook/assets/image%20%2827%29.png)

When a NLP provider is configured, all `text` events will be sent to the NLP provider and returned either as a `payload` event if an intent is found, or untouched if no intent is found.

Additionally, a few properties are set:

* `event._nlp_provider`: contains details about the NLP provider integration
* `event._nlp_result`: contains the raw response from the NLP provider request
* `event._original_event`: contains the original, untouched event. Only set if an intent is found.

