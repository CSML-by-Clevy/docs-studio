# Introduction

CSML \(Conversational Standard Meta Language\) is a Domain-Specific Language developed for creating conversational experiences easily.

The purpose of this language is to simplify the creation and maintenance of rich conversational interactions between humans and machines. With a very expressive and text-only syntax, CSML flows are easy to understand, making it easy to deploy and maintain conversational agents. The CSML handles short and long-term memory slots, metadata injection, and connecting to any third party API or injecting arbitrary code in any programming language thanks to its powerful runtime APIs.

By using the CSML language, any developer can integrate arbitrarily complex conversational agents on any channel \(Facebook Messenger, Slack, Facebook Workplace, Microsoft Teams, custom webapp, ...\) and make any bot available to any end user. The CSML platform comes with a large number of channel integrations that work out of the box, but developers are free to add new custom integrations by using the CSML interfaces.

## Getting started

```cpp
/* Always start the conversation with this step */
start:
  /* The bot knows the name of the user */
  if (username) {
    say "Hi {{username}}!"
    say "It's nice to see you again."
    goto end
  }

  /* This is the first time we speak with the user */
  else {
    say "Hello World!"
    goto getname
  }


/* Step to retrieve the user's name */
getname:
  say OneOf(["What's your name?", "How do people call you?"])
  hold

  remember username = event
  say "OK, I now know that your name is {{event}}."
  goto end
```

This is a simple CSML flow example, which describes a conversation between a user and a machine.

A CSML `flow` contains several `steps`, which are defined by a name \(which must be unique within a flow\) followed by a colon. Each step contains instructions on how to handle the interactions within the step, what to say, what to remember, where to go. The syntax is very descriptive and contains very few keywords.

This goal of the example flow on the right is to retrieve the name of the user.

To do so, we will first check if we already have it in memory. If so, we can use it to greet our user, and close this conversation. Otherwise, we can go to a different step and simply ask for it. When the user responds, we will be able to `remember` the name for future use, and close the conversation.

This simple flow shows a few of the features of the language. There are many more, which we will go into in detail now!

