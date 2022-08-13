---
description: Step by step guide to install a Slack channel
---

# Installation

The Slack integration provides you with a **Manifest** that allows you to setup most of the heavy Slack App configuration in seconds. To get started, simply click on the link provided here:

![](<../../.gitbook/assets/image (127) (1).png>)

Simply follow the on-screen instructions until the app is installed to your workspace. You will be required to allow the app to perform the necessary actions - you must be a workspace admin to do that.

![](<../../.gitbook/assets/image (125) (1).png>)

You will still need to perform a few actions to correctly setup your app. First, visit the **App Manifest** menu. It may have an orange warning box at the top: in that case, click the "**Click here to verify**" link to make that warning disappear. Another way to perform this verification if needed is by visiting **Event Subscriptions** and performing the same operation.

![](<../../.gitbook/assets/image (128).png>)

Next, visit the **OAuth & Permissions** menu, copy the **Bot User Token** and save it for later.

![](<../../.gitbook/assets/image (3).png>)

Next, select **App Home** in the left-side menu. Enter a Display Name and a Default Name for your bot and select **Always Show My Bot as Online**.

![](<../../.gitbook/assets/image (2) (1).png>)

At the bottom of the same **App Home** page, under **Show Tabs**, make sure the **Messages Tab** toggle is _on_ and the **Allow users to send Slash commands and messages from the messages tab** checkbox is _checked_.

![](<../../.gitbook/assets/image (129) (1).png>)

Next, visit **Basic Information** from the left-side menu, copy the **App ID**, **Client ID**, **Client Secret** and **Signing Secret** under **App Credentials** and save them for later.

![](<../../.gitbook/assets/image (7).png>)

On the same page, you can also customize the appearance of your chatbot in Slack (image, colors...).

![](<../../.gitbook/assets/image (1) (1) (1).png>)

Finally, back in CSML Studio, paste the credentials you retrieved earlier: **Bot User Token**, **App ID**, **Client ID**, **Client Secret**, **Signing Secret**, then click on **Submit**.

You should now be able to see your app in the left sidebar of your Slack workspace, under **Apps**. This is where you can chat with your slack bot!

![](<../../.gitbook/assets/image (126) (1).png>)
