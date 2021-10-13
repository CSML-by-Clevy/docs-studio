# AI Rules

In the AI Rules section of CSML Studio, you will find a way to configure flow commands for any of your flows. This section makes it easy to see in one single screen all the rules that govern the triggering of any of your flows!

Commands are words or sentences (or intents, when NLU is configured) that will trigger a given flow. For example, in the example below, if a user says `"Hi"`, no matter where they are in the bot, they will be redirected to the `Welcome` flow:

![](<../../.gitbook/assets/CleanShot 2021-06-04 at 12.28.07@2x.png>)

You can have as many AI Rules as you want on as many flows as you want. The commands are case-insensitive, so for example `"Hi"`, `"hi"`, `"HI"` and `"hI"` will all trigger the `Welcome` flow. Also, if the same rule is used as an input to two different flows, the triggered flow will be randomly chosen among the target flows.

This feature can also be used in conjunction with any Preprocessing or NLP configured in your bot. For instance, if after going through a NLP service, an intent is detected, the intent name can be used as a command for any given flow (with the `intent:` prefix, i.e `intent:myIntentName`). For instance, this is how an intent called `DemoContext` would be handled with AI Rules:

![](<../../.gitbook/assets/CleanShot 2021-06-04 at 12.29.30@2x.png>)
