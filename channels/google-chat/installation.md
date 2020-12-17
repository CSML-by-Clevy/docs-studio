# Installation

## Setup a Google Chat service account

[Service accounts](https://developers.google.com/hangouts/chat/how-tos/service-accounts) are the primary way to interact with Google Cloud resources, and setting up a chatbot is no different.

The first step is to create a new Google Cloud project. Visit [https://console.cloud.google.com/projectcreate](https://console.cloud.google.com/projectcreate) and fill the required fields:

![](../../.gitbook/assets/image%20%2860%29.png)

Then, [visit this page](https://console.cloud.google.com/marketplace/product/google/chat.googleapis.com) to enable the Google Chat API for this project:

![](../../.gitbook/assets/image%20%2858%29.png)

Then, go to Identity &gt; Service Accounts in the menu \(or visit [https://console.cloud.google.com/identity/serviceaccounts](https://console.cloud.google.com/identity/serviceaccounts)\) and create a service account for the project.

![](../../.gitbook/assets/image%20%2865%29.png)

In the next screen, grant the **Project &gt; Editor** role to the service account:

![](../../.gitbook/assets/image%20%2856%29.png)

The third step \(_Grant users access to this service account_\) is optional and can be skipped. Click on Done to create the service account. 

Once the service account is created, you will need to generate a key. Select the service account, click on **Add Key &gt; Create New Key**, select **JSON** as the Key type, and save the file.

## Setup the channel in CSML Studio

In CSML Studio, under **Channels &gt; Connect a new channel**, select the Google Chat channel. In the next screen, give your channel a name, a description and upload your service account credentials.

![](../../.gitbook/assets/image%20%2857%29.png)

In the next screen, you can configure the bot's Welcome Flow, and copy the **Chatbot Endpoint URL**, which we will use in the next step.

## Connect the chatbot with Google Chat

To finalize the configuration, visit [https://console.developers.google.com/apis/api/chat.googleapis.com/hangouts-chat](https://console.developers.google.com/apis/api/chat.googleapis.com/hangouts-chat) \(make sure that the selected project is still the same one as before\) and fill the information as requested.

![](../../.gitbook/assets/image%20%2855%29.png)

You can select **Bot works in direct messages** or **Bot works in rooms...** depending on the experience you want to give to users.

Under **Bot URL**, paste the **Chatbot Endpoint URL** from the previous step.

Click **Save**, and you are all set!

## Finding the bot in Google Chat

To find your bot in Google Chat, users have to navigate to the Bot catalog, which can be reached either by clicking the + icon next to the bot section of the left sidebar, or by searching for the name of the bot directly:

![](../../.gitbook/assets/image%20%2861%29.png)

Upon activating the bot for the first time, the Welcome Message will be displayed:

![](../../.gitbook/assets/image%20%2863%29.png)

