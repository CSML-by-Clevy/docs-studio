# Authoring Custom Apps

If you already have custom code that you would like to use in your chatbot, you can import it directly as a custom app in CSML Studio and use it without any change.

In CSML Studio, apps are run by default on AWS Lambda, which ensures maximum availability, scalability and security by isolating your code in separate containers. The supported runtimes are currently:

* Nodejs v10.x and 12.x
* Java 8 and 11
* Python 2.7, 3.6, 3.7 and 3.8
* Dotnetcore 2.1 and 3.1
* Go 1.x
* Ruby 2.5 and 2.7

To get started with AWS Lambda compatible deployment package in any language, [you can refer to this documentation](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-features.html#gettingstarted-features-package).

{% hint style="warning" %}
**Deprecation notice:** the original `Fn()` notation for calling Apps \(formerly called Functions\) in your CSML code has been replaced by the newer `App()` built-in as of CSML v1.5. Both notations will continue to work until CSML v2 is released, but this documentation will only reference the new `App()` usage from now on.
{% endhint %}

## Quick Mode

The easiest way to author custom apps in CSML Studio is to use the **Quick Mode**, which provides you with a code editor to create your app directly in the browser. There are several limitations:

* only nodejs is supported \(support for python will be added shortly\)
* quick apps can not contain more than 4096 characters
* custom modules can not be added \(however all native node modules are supported\)
* environment variables can not be configured

If you need more configuration options \(other languages, bigger package size, custom modules\), we recommend using the **Complete Mode** as explained below.

As an example, let's create a simple nodejs 12.x app that will return a random user from [RandomUser.me](https://randomuser.me/). This code performs a simple GET request to https://randomuser.me/api and returns the first user in the returned array. The code is available [here on github](https://github.com/frsechet/csml-function-example-node12): download it or clone it to get started.

#### The App Code

To test this program, simply run `node test.js` at the root of the project. You should see something like the following:

![](../../.gitbook/assets/image%20%2816%29.png)

#### Authoring in Quick Mode

Select **Add Custom App** at the top-right corner of the apps page, which brings you directly to Quick Mode \(nodejs\). Simply copy-paste the content of index.js into the code editor, choose a name for your app, then click **Save**.

![](../../.gitbook/assets/image%20%2833%29.png)

You can now use your app in your CSML Chatbot, like this:

```cpp
start:
  do user = App("getRandomUser")
  say "The random user's name is: {{user.name.first}} {{user.name.last}}"
  goto end 
```

![](../../.gitbook/assets/image%20%2813%29.png)

## Complete Mode

With complete mode, a few extra steps are needed, as you will need to provide the code in a _deployment package_ and upload it on the platform.

#### Creating a deployment package

At the root of the project as downloaded from github, run the command `zip -r9 ../randomuser.zip .`. This will create a deployment package for your app, that you will be able to import in CSML Studio.

{% hint style="warning" %}
You **MUST** run this command inside the project directory. Zipping the folder itself produces an invalid deployment package.
{% endhint %}

#### Uploading to CSML Studio

In the sidebar, click on **Apps &gt; Add a new app**. In the app creation page, upload your deployment package, give your app a distinctive and unique name such as `getRandomUser`, leave `index.handler` as your app's main handler and select `nodejs12.x` as the runtime.

You can leave the sections below as is for now; if your app took any argument or required any environment variable, this is where you would configure it.

Once you are done, simply save. You can now use your app in your CSML Chatbot as above.

## Good practices

* As in every development project, apps have a processing cost associated to them. The more difficult the task is, the longer it takes to perform, the worse your user experience will be. Keep in mind that running apps will also increase the latency between the user's input and the bot's response. If possible, try to stick to native CSML code!
* It is always a good practice to only return what you intend to use. For example, if you are interfacing with a product catalog, do you need to get all 3542 items in the catalog, or will the first 5 suffice? If you are retrieving a list of items, what properties from that list do you actually need?
* Apps are limited to 30s of execution time. If it takes longer, the app will stop and return an error.
* Apps only get 512MB of RAM by default. Any excessive resource usage will lead the app to stop its execution immediately.
* If you are saving the output of your app to a `do x = App(..)` \(or a `remember`\), the data is subject to the usual memory size limitations. In general, if your app returns more than a few KB of data, ask yourself if you really need all that data that you most likely won't be able to display in a chatbot \(text-based, so really light\) or if you shouldn't strip it down directly in the app itself!

