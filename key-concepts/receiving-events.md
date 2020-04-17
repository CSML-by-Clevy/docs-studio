# Receiving Events

When receiving an event from an end-user, the CSML interpreter will try to match it with a new flow, or consume it in the existing conversation, or trigger the default flow as defined in the bot settings, by order of priority.

CSML Events are made available in the script when a step is triggered by a user's input. The `event` object is a complex structure which contains a lot more than just the string that was typed by the user. It contains a lot of information that is used by the CSML interpreter, for example the custom button payload to match a list of choices offered to the user. This makes it easy to handle both a click on a "OK" button or the user typing the word "yes".

By default, events are only expected when:

* the flow was just triggered, the current step being triggered is `start`
* the bot asked something to the user, and is waiting for the user's input at the same step

In those cases, a local variable, `event`, is made available, with the content of the user request. When no event is available, event is set to `NULL`.

## 

