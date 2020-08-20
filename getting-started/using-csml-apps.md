# Functions and Apps

CSML provides a way to execute external code in any language of your choice via a _Foreign Function Interface_, represented by the `Fn()` keyword.

Here are some ideas for CSML integrations:

* file tickets to [Zendesk](https://zendesk.com), [ServiceNow](https://servicenow.com) or [Front](https://frontapp.com/)
* create leads in [Hubspot](https://hubspot.com), [Mailchimp](https://mailchimp.com), [Salesforce](https://salesforce.com)
* store data on [Airtable](https://airtable.com/), [Google Sheet](https://docs.google.com/spreadsheets), [Amazon DynamoDB](https://aws.amazon.com/dynamodb)
* upload files to [Box](http://box.com/), [Google Docs](https://docs.google.com/), [Office 365](https://www.office.com/)
* analyze text with [SAP Conversational AI](https://cai.tools.sap/), [Dialogflow](https://dialogflow.cloud.google.com/), [Rasa](https://rasa.com/)
* book meetings on [Google Calendar](https://calendar.google.com/), [Hubspot](https://hubspot.com), [Calendly](https://calendly.com/fr)
* trigger events in [Zapier](https://zapier.com), [IFTTT](https://ifttt.com/), [Integromat](https://www.integromat.com/)
* generate QR codes, format documents, upload images
* and many more!

There are 2 ways you can augment your CSML chatbot by connecting it to other services: importing custom code, or installing CSML Apps.

## Using CSML Apps

[CSML Apps](https://www.csml.dev/integrations.html) are a great way to extend the capabilities of your CSML chatbot by integrating other products with your bot without writing any additional code. CSML Studio provides a number of available apps \(more than 50 and growing!\), that make it possible to integrate your chatbot with the most popular services and applications on the market.

### Example: Giphy app

For instance, if you are looking to add some fun Gifs to your bot, you can try our [Giphy](https://giphy.com) integration. To get started, go to **Functions &gt; Apps directory &gt; Giphy**.

![](../.gitbook/assets/image%20%2815%29.png)

Simply click on **Install**, and you are done! Some apps require credentials or API keys, but this one does not. If that's the case you are prompted to add _environment variables_ upon installation.

Then, to use the app in your code, you can use it like this:

```cpp
start:
  do gifs = Fn("giphy", action="gif", query="hello")
  say Image(gifs[0])
  goto end
```

![The above code will generate a nice gif automatically!](../.gitbook/assets/image%20%2818%29.png)

## Using Custom Code

If you already have custom code that you would like to use in your chatbot, you can import it directly as a custom function in CSML Studio and use it without any change.

In CSML Studio, functions are run by default on AWS Lambda, which ensures maximum availability, scalability and security by isolating your code in separate containers. The supported runtimes are currently:

* Nodejs v10.x and 12.x
* Java 8 and 11
* Python 2.7, 3.6, 3.7 and 3.8
* Dotnetcore 2.1 and 3.1
* Go 1.x
* Ruby 2.5 and 2.7

To get started with AWS Lambda compatible deployment package in any language, [you can refer to this documentation](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-features.html#gettingstarted-features-package).

### Quick Mode

The easiest way to author custom functions in CSML Studio is to use the **Quick Mode**, which provides you with a code editor to create your function directly in the browser. There are several limitations:

* only nodejs is supported \(support for python will be added shortly\)
* quick functions can not contain more than 4096 characters
* custom modules can not be added \(however all native node modules are supported\)
* environment variables can not be configured

If you need more configuration options \(other languages, bigger package size, custom modules\), we recommend using the **Complete Mode** as explained below.

As an example, let's create a simple nodejs 12.x function that will return a random user from [RandomUser.me](https://randomuser.me/). This code performs a simple GET request to https://randomuser.me/api and returns the first user in the returned array. The code is available [here on github](https://github.com/frsechet/csml-function-example-node12): download it or clone it to get started.

#### The function

To test this program, simply run `node test.js` at the root of the project. You should see something like the following:

![](../.gitbook/assets/image%20%2816%29.png)

#### Authoring in Quick Mode

Select **Add Custom Function** at the top-right corner of the functions page, which brings you directly to Quick Mode \(nodejs\). Simply copy-paste the content of index.js into the code editor, choose a name for your function, then click **Save**.

![](../.gitbook/assets/image%20%2832%29.png)

You can now use your function in your CSML Chatbot, like this:

```cpp
start:
  do user = Fn("getRandomUser")
  say "The random user's name is: {{user.name.first}} {{user.name.last}}"
  goto end 
```

![](../.gitbook/assets/image%20%2813%29.png)

### Complete Mode

With complete mode, a few extra steps are needed, as you will need to provide the code in a _deployment package_ and upload it on the platform.

#### Creating a deployment package

At the root of the project as downloaded from github, run the command `zip -r9 ../randomuser.zip .`. This will create a deployment package for your function, that you will be able to import in CSML Studio.

{% hint style="warning" %}
You **MUST** run this command inside the project directory. Zipping the folder itself produces an invalid deployment package.
{% endhint %}

#### Uploading to CSML Studio

In the sidebar, click on **Functions &gt; Add a new function**. In the function creation page, upload your deployment package, give your function a distinctive and unique name such as `getRandomUser`, leave `index.handler` as your function's main handler and select `nodejs12.x` as the runtime.

You can leave the sections below as is for now; if your function took any argument or required any environment variable, this is where you would configure it.

Once you are done, simply save. You can now use your function in your CSML Chatbot as above.

