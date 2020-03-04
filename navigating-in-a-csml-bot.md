# Navigating in a CSML Bot

## Navigating within a flow

A flow is made of at least one step \(called `start`\), but can also contain as many steps as necessary. You should think of steps as individual, simple bits of logic, linked inside the same conversation topic \(which is the flow\).

To go from one step to the next, you can simply use the keyword `goto` \(or `goto step`\) followed by the name of the step.

To finish a flow \(and close the conversation\), add `goto end`.

```cpp
start:
  say "hi"
  goto step otherstep // note: in the following examples, we will use the shorthand notation `goto otherstep`

otherstep:
  say "I'm in otherstep"
  goto end
```

## Navigating between flows

Similarly to navigating between steps of the same flow, you can go to the beginning of any other flow by using the `goto flow` keyword. This will trigger the `start` step of the target flow and close the current flow, so coming back to the first flow will actually go back to the beginning of that flow.

```cpp
somestep:
  goto flow anotherflow
```

## Recursive flows

When a new flow is triggered, the CSML engine will first check whether or not the user was already inside another flow. If that's the case, and if the new flow is direct \(i.e it does not stop to ask the user for any input at any time\), the last action of the previous flow will be triggered once more.

This means that if for some reason in the middle of a long questionnaire, the user were to ask for a quick information, the bot would immediately return to the previous flow after giving the user the requested information.

Below is an example of the expected behavior

```text
bot: What is your favorite color?
user: help
bot: I'm FormBot, developed by FormCorp. I'm here to ask you to fill a form. To start a new form, type "restart".
bot: What is your favorite color?
...
```

