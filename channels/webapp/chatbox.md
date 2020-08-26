# Chatbox

The webapp channel also comes with a configurable website plugin \(called the **Chatbox**\) that can be added to any website by adding a single line in your source code. The Chatbox will then appear as a small bubble in the bottom-right corner of your site for every visitor.

## Installation

Simply add the following line of code in your source code, just before the closing `</body>` tag \(replace it with the actual line that you can find in your Webapp configuration panel\):

```text
<script
  src="https://chatbox.csml.dev/script.min.js?token=CHATBOX_TOKEN"
  id="clevy-chatbox"
  async>
</script>
```

Once this is done, a chat bubble will appear as follows on every page where that code is included. Clicking the chat icon will open the chatbox:

![](../../.gitbook/assets/image%20%2837%29.png)

CSML Studio has an option to display an optional greeting text when the chatbox is closed:

![](../../.gitbook/assets/image%20%2836%29.png)

The content of the text bubble is configurable in the Chatbox settings at the bottom of the Webapp configuration panel. If that field is left empty, only the blue chat icon will appear.

![](../../.gitbook/assets/image%20%2838%29.png)



