# Installation

Creating a Telegram chatbot is particularly easy. You only need to get a regular Telegram account, then to interact with [**@BotFather**](https://t.me/botfather)** **on Telegram, which is a built-in bot that will help you setup your own bot!

## Telegram's @BotFather

![](<../../.gitbook/assets/image (112).png>)

{% hint style="danger" %}
**Very important**: make sure that you never **EVER** show the bot's token to anybody! Otherwise anyone will be able to take control of your chatbot instantly.
{% endhint %}

BotFather lets you customize your bot even more. You can use the following commands:

* `/setname` to change the bot's name
* `/setuserpic` to change the bot's profile picture
* `/setdescription` and `/setabouttext` to change the bot's description/about texts

![](<../../.gitbook/assets/image (116).png>)

This is also a perfect way to try the Telegram commands feature, which is very powerful!

## CSML Studio Setup

Once you have received the bot's token, go to your bot's **Channels** page and click on **Telegram** to create a new Telegram chatbot.

![(obviously, this token is now revoked!)](<../../.gitbook/assets/image (113).png>)

Once this is done, you will be able to setup a few commands for your own bot. The `/start` command is mandatory and can not be removed (but you can change its description), and it will always trigger the chatbot's welcome flow. You can add more commands to your bot, which will show if you start typing `/` or click on the corresponding symbol in the Telegram interface:

![](<../../.gitbook/assets/image (117).png>)

If you have flows matching the names of the commands, these flows will be triggered automatically. Otherwise, you can set custom rules in the [AI Rules section](../../getting-started/nlp/ai-rules.md) to match the given commands (including the leading `/`)

![](<../../.gitbook/assets/image (114).png>)
