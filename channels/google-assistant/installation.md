# Installation

## 1. Creating the Google Actions project

Google Assistant chatbots are instances of Google Actions. To get started, visit [https://console.actions.google.com](https://console.actions.google.com) and create a new project:

![](<../../.gitbook/assets/image (93).png>)

In the next screens, select **Custom** then **Blank Project**, and click on **Start building**.

![](<../../.gitbook/assets/CleanShot 2021-06-08 at 11.28.51.png>)

![](<../../.gitbook/assets/CleanShot 2021-06-08 at 11.29.07.png>)

In the next screen, you will be able to create a display name, which is also the default invocation for your action. Read more about how to [pick the right display name here](https://support.google.com/actions-console/answer/9613473?hl=en#null)!

![](<../../.gitbook/assets/image (94).png>)

Finally, you will also need to retrieve your action project's ID, which you can easily copy from the URL:

![](<../../.gitbook/assets/CleanShot 2021-06-09 at 14.23.09@2x.png>)

## 2. Connecting the Channel in CSML Studio

In CSML Studio, create a new Google Assistant channel from the Channels page and fill in the requested fields. The name and description can differ from the name of the Action, they are only visible inside CSML Studio!

After you created the channel, download and install the `gactions CLI` utility from this page: [https://developers.google.com/assistant/actions/actions-sdk/](https://developers.google.com/assistant/actions/actions-sdk/). This tool will let you "bind" your gactions and the CSML studio project, using the `gactions.json` package that you can download on the channel's configuration page:

![](<../../.gitbook/assets/image (96).png>)

You will need to execute the command on a terminal and follow the instructions to authenticate your requests with Google. Concretely, after you execute the command, you will need to click on the link that the command will prompt you to visit, login with your Google account, and copy and paste the given code:

![](<../../.gitbook/assets/image (97).png>)

After you have done this process, you can go test the bot in the Test panel:

![](<../../.gitbook/assets/CleanShot 2021-06-09 at 14.27.26@2x.png>)
