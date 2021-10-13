# Installation

## Setup a Google Chat service account

[Service accounts](https://developers.google.com/hangouts/chat/how-tos/service-accounts) are the primary way to interact with Google Cloud resources, and setting up a chatbot is no different.

The first step is to create a new Google Cloud project. Visit [https://console.cloud.google.com/projectcreate](https://console.cloud.google.com/projectcreate) and fill the required fields:

![](<../../.gitbook/assets/image (55).png>)

Then, [visit this page](https://console.cloud.google.com/marketplace/product/google/chat.googleapis.com) to enable the Google Chat API for this project:

![](<../../.gitbook/assets/image (56).png>)

Then, go to Identity > Service Accounts in the menu (or visit [https://console.cloud.google.com/identity/serviceaccounts](https://console.cloud.google.com/identity/serviceaccounts)) and create a service account for the project.

![](<../../.gitbook/assets/image (57).png>)

In the next screen, grant the **Project > Editor** role to the service account:

![](<../../.gitbook/assets/image (58).png>)

The third step (_Grant users access to this service account_) is optional and can be skipped. Click on Done to create the service account. 

Once the service account is created, you will need to generate a key. Select the service account, click on **Add Key > Create New Key**, select **JSON **as the Key type, and save the file.

## Setup the channel in CSML Studio

In CSML Studio, under **Channels > Connect a new channel**, select the Google Chat channel. In the next screen, give your channel a name, a description and upload your service account credentials.

![](<../../.gitbook/assets/image (59).png>)

In the next screen, you can configure the bot's Welcome Flow, and copy the **Chatbot Endpoint URL**, which we will use in the next step.

## Connect the chatbot with Google Chat

To finalize the configuration, visit [https://console.developers.google.com/apis/api/chat.googleapis.com/hangouts-chat](https://console.developers.google.com/apis/api/chat.googleapis.com/hangouts-chat) (make sure that the selected project is still the same one as before) and fill the information as requested.

![](<../../.gitbook/assets/image (60).png>)

You can select **Bot works in direct messages** or **Bot works in rooms...** depending on the experience you want to give to users.

Under **Bot URL**, paste the **Chatbot Endpoint URL** from the previous step.

Click **Save**, and you are all set!

## Finding the bot in Google Chat

To find your bot in Google Chat, users have to navigate to the Bot catalog, which can be reached either by clicking the + icon next to the bot section of the left sidebar, or by searching for the name of the bot directly:

![](<../../.gitbook/assets/image (61).png>)

Upon activating the bot for the first time, the Welcome Message will be displayed:

![](<../../.gitbook/assets/image (63).png>)
