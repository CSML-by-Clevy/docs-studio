# Chatbox

The webapp channel also comes with a configurable website plugin (called the **Chatbox**) that can be added to any website by adding a single line in your source code. The Chatbox will then appear as a small bubble in the bottom-right corner of your site for every visitor.

## Installation

Simply add the following line of code in your source code, just before the closing `</body>` tag (replace it with the actual line that you can find in your Webapp configuration panel):

```markup
<script
  src="https://chatbox.csml.dev/script.min.js?token=CHATBOX_TOKEN"
  id="clevy-chatbox"
  async>
</script>
```

Once this is done, a chat bubble will appear as follows on every page where that code is included. Clicking the chat icon will open the chatbox:

![](<../../.gitbook/assets/image (38).png>)

## Adding a Custom Greeting

The Chatbox lets you configure a custom popup message as well as up to three Quick Action buttons to help you engage more actively with your customers. If both fields are left empty, only the blue chat icon will appear. You can also configure only a popup message or only the action buttons! You can find these configuration options in the Chatbox settings, one of the Web Chat configuration panels.

![The end result](<../../.gitbook/assets/image (121).png>)

{% hint style="info" %}
When configuring Quick Action buttons, you must provide both a title and a payload. The payload can be any string that will be interpreted by CSML. In the example below, those buttons contain a simple payload that match corresponding flows. You can also use an AI Rule trigger as a payload!
{% endhint %}

![](<../../.gitbook/assets/image (123).png>)

## Optional Attributes

Several configurations are available as [standard HTML data attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use\_data\_attributes) to maximize compatibility across browsers.

```markup
<script
  src="{CHATBOX_URL}"
  id="clevy-chatbox"
  data-position="left"
  data-webapp-metadata="%7B%22firstname%22%3A%22Jane%22%2C%22email%22%3A%22jane.doe%40company.com%22%7D"
  async>
</script>
```

### data-position

By default, the chatbox will be displayed on the right side of the screen. To display the chatbox on the left instead, simply add `data-position="left"`.

### data-webapp-metadata

To add custom metadata in a chatbox ([see this page for more information about injecting metadata in the webapp](features.md#injecting-conversation-metadata)), you need to add a `data-webapp-metadata` attribute to the chatbox initialization script tag that contains the encoded (with [javascript's encodeURIComponent function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/encodeURIComponent)) JSON string of the metadata you want to inject.

For example: `data-webapp-metadata="%7B%22email%22%3A%22jane.doe%40company.com%22%7D"`

### data-logo-url

You can configure a custom image to be used as the chatbox logo by setting this parameter to the URL of your image. You can use a transparent png or a svg to achieve this effect below, or directly use a square image (it will be rounded automatically) without a transparent background to use as the logo.

For example: `data-logo-url="https://cdn.clevy.io/clevy-logo-square-white.png"`

![](<../../.gitbook/assets/image (86).png>)

### data-launcher-fill, data-launcher-background

These two parameters let you change the fill color of the default icons, as well as the background for the launcher button.

Any valid CSS value for these elements is accepted. The default values are:

```markup
<script src="{CHATBOX_URL}"
  id="clevy-chatbox"
  data-launcher-fill="#ffffff"
  data-launcher-background="linear-gradient(135deg, #4f89fc 0, #1965ff 51%, #104dc7 100%)"
  async></script>
```

### data-force-open

Force the chatbox to open as soon as the script is loaded. Not recommended as it might be a bit agressive for the visitors of the page, but may be useful in some cases!

```html
<script src="{CHATBOX_URL}"
  id="clevy-chatbox"
  data-force-open="true"
  async></script>
```

### data-ref

Set the inner webapp's ref param to trigger a specific flow or step

```html
<script src="{CHATBOX_URL}"
  id="clevy-chatbox"
  data-ref="someRefParam"
  async></script>
```
