# Create Your First Bot

## Introduction

**In this tutorial, you will learn how to setup a chatbot that will qualify leads and sign them up to your Mailchimp contact list.**

At the end of this tutorial, here is what you will be able to:

* Get information from the end-user
* Subscribe this user to an existing Mailchimp contact list
* Ask users for feedback on their experience, and send a custom answer based on their response

## Writing your CSML flow

A CSML flow always starts in the `start` step, in this step, we introduce the chatbot.  
Note that `Typing(2000)` needs to be preceded by the `say` keyword, this will show the three little jumping dots on the screen, suggesting the chatbot is typing, this action will last 2 seconds \(2000 milliseconds\).

```cpp
start:
	say Typing(2000)
	say "Hi 🤓, I just need a few informations in order to add you to my mailing list."
	goto firstname
```

We can then move on to the next step in which we will start asking for user informations.

## **Asking questions and remembering answers**

With CSML, in order to wait for the user to reply to a question \(or anything else for that matter\), we use the keyword `hold`, the chatbot then waits for the user to reply. After answering, the user input will be placed in the `event` variable.

Note: the event variable is scoped to the current step, which basically means that `event` will be wiped off the memory once the chatbot goes out of the current step.

In order to remember what the user said, we can ask the chat to `remember nlFirstname = event`, and `nlFirstname` will then be accessible anywhere, anytime.

```cpp
firstname:
	say Typing(2000)
	say "What's your firstname?"
	hold
	
	remember nlFirstname = event 
	goto lastname
```

Let's move to the next step : `lastname`

First let's have a look at the `Button(...)` component: it has two parameters, a `title=""` that represents what will be displayed inside the button, and an `accept=[]` parameter that is a list of all the words that correspond to this button. This way, if a user types "NA", CSML will understand it as being the same as a click on this button. Lastly, we set this button as variable `btnLastname`.

Now that our button is saved, we then create a `Question` component, add the preset button and `hold`.

As the user answers, we check if the input matches the button or what it accepts ans remember the appropriate `nlLastname`.

```cpp
lastname:
	say Typing(2000)
	do btnLastname = Button(
		title = "I don't want to share my lastname",
		accept = ["No", "No", "no", "NA", "N/A", "na", "n/a"]
	)
	
	say Question(title="What's your lastname?", buttons=[btnLastname])
	hold
	
	if (event match btnLastname) remember nlLastname = "N/A"
	else remember nlLastname = event
	goto email
```

The same goes with the email, only this time we're checking if the user input contains a `@`, if it doesn't we start the step again, otherwise we remember the email and move on to save everything.

```cpp
email:
	say Typing(2000)
	say "What's your email address?"
	hold
	
	// does the user's input look like an email address?
	if (event.contains("@") {
		remember nlEmail = event
		goto save
	}

	// otherwise the input is probably not a valid email address
	// we need to ask them again
	say "That's not a valid email address 😱"
	goto email

```

## **Sending data to Mailchimp**

Thanks to our app store, you can install the Mailchimp app in a few clicks \(you'll just need to get your API Region, API key and contact list ID\). The App function needs an option parameter that encloses all the informations that Mailchimp needs.

Note that `Fn(...)` needs to be used in a `do` statement.

```cpp
save:
	// prepare the arguments required by the mailchimp function
	do options = {
		"listId": "d8acdcc85f",
		"email": nlEmail,
    "firstname": nlFirstname,
    "lastname": nlLastname,
	}
	// execute the function
	do mailchimpResponse = Fn("mailchimp", action="subscribeToList", options=options)
	
	say Typing(2000)
	say "I have added you to our newsletter subscription list !"
	
	goto feedback
```

Now it's time to get some feedback from the user!

## **NLP coming into play**

We want to use the [SAP Conversational AI](https://cai.tools.sap/) to find out if the user's input is positive, neutral or negative. The API returns this as sentiments. If you want to see the full response from the API, you can print it using `say "{{sapcaiResponse}}"`

```cpp
feedback:
	say "How did you like this newsletter onboarding?"
	hold
	
	// query the NLP service
	do sapcaiResponse = Fn("sap/cai", text=event)
	
	// this contains the sentiment analysis of the query
	say sapcaiResponse.results.sentiment
	
	if (Find("positive", in=sapcaiResponse.results.sentiment)) {
		say "Thank you so much for your kind words 😇."
	} 
	else if (Find("negative", in=sapcaiResponse.results.sentiment)) {
		say "I'd love to know what went wrong, please join our slack channel and let us know."
	} 
	else {
		say "I am sure you'll get to love CSML :D"
	}
	
	goto end
```

## **That's it !**

You've done it, you've created your first CSML bot from scratch ! Here is the full code:

```cpp
start:
	say Typing(2000)
	say "Hi 🤓, I just need a few informations in order to add you to my mailing list."
	goto firstname

	
firstname:
	say Typing(2000)
	say "What's your firstname?"
	hold
	
	remember nlFirstname = event 
	goto lastname


lastname:
	say Typing(2000)
	do btnLastname = Button(
		title = "I don't want to share my lastname",
		accept = ["No", "No", "no", "NA", "N/A", "na", "n/a"]
	)
	
	say Question(title="What's your lastname?", buttons=[btnLastname])
	hold
	
	if (event match btnLastname) remember nlLastname = "N/A"
	else remember nlLastname = event
	goto email
	

email:
	say Typing(2000)
	say "What's your email address?"
	hold
	
	// does the user's input look like an email address?
	if (event.contains("@") {
		remember nlEmail = event
		goto save
	}

	// otherwise the input is probably not a valid email address
	// we need to ask them again
	say "That's not a valid email address 😱"
	goto email


feedback:
	say "How did you like this newsletter onboarding?"
	hold
	
	// query the NLP service
	do sapcaiResponse = Fn("sap/cai", text=event)
	
	// this contains the sentiment analysis of the query
	say sapcaiResponse.results.sentiment
	
	if (Find("positive", in=sapcaiResponse.results.sentiment)) {
		say "Thank you so much for your kind words 😇."
	} 
	else if (Find("negative", in=sapcaiResponse.results.sentiment)) {
		say "I'd love to know what went wrong, please join our slack channel and let us know."
	} 
	else {
		say "I am sure you'll get to love CSML :D"
	}
	
	goto end


save:
	// prepare the arguments required by the mailchimp function
	do options = {
		"listId": "d8acdcc85f",
		"email": nlEmail,
    "firstname": nlFirstname,
    "lastname": nlLastname,
	}
	// execute the function
	do mailchimpResponse = Fn("mailchimp", action="subscribeToList", options=options)
	
	say Typing(2000)
	say "I have added you to our newsletter subscription list !"
	
	goto feedback
```

If you have any question, please come ask us on [Slack](https://join.slack.com/t/csml-by-clevy/shared_invite/enQtODAxMzY2MDQ4Mjk0LWZjOTZlODI0YTMxZTg4ZGIwZDEzYTRlYmU1NmZjYWM2MjAwZTU5MmU2NDdhNmU2N2Q5ZTU2ZTcxZDYzNTBhNTc)!  


