# Asking Questions

A conversation with a chatbot is not very different from a human-to-human dialogue: sometimes the user talks, sometimes the bot talks.

```cpp
somestep:
  say Question("Do you like cheese?", buttons=[Button("yes"), Button("no")])
  hold

  if (event == "yes") say "I'm glad to know that you like cheese!"
  else say "Oh that's too bad!"
```

CSML provides a solution when you need the chatbot wait for the user's input: using the `hold` keyword, the chatbot will remember its position in the conversation and simply wait until the user says something, then continue from there.

