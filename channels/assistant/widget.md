# Widget

The Assistant channel also comes with a configurable website plugin (called the **Widget**) that can be added to any website by adding a single line in your source code. The Widget will then appear as a small bubble in the bottom-right corner of your site for every visitor.

## Installation

Simply add the following line of code in your source code, just before the closing `</body>` tag (replace it with the actual line that you can find in your Webapp configuration panel):

```markup
<script
  src="https://widget.csml.dev/script.min.js?token=ASSISTANT_TOKEN"
  id="clevy-widget"
  async>
</script>
```

Once this is done, a chat bubble will appear as follows on every page where that code is included.

## Adding a Custom Greeting

The Widget lets you configure a custom popup message to help you engage more actively with your customers. You can even have default greeting messages depending on the page where the widget is loaded! Here is how it works:

* Greetings are matched with their page based on the URI. The first message that matches the URI is the one that will be displayed. We support wildcards `*` and `**` to make it more versatile!
* To display a message on all pages, use `/**` as the URI.
* If you want to target one specific page, use its URI, i.e `/about-us/the-team`
* You can also target all subpages of a directory with `*`: `/about-us/*` will match `/about-us/the-team` and `/about-us/the-company`
* The `**` wildcard will also match any subdirectory: `/about-us/**` will match `/about-us/team/europe`&#x20;

## Optional Attributes

Several configurations are available as [standard HTML data attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use\_data\_attributes) to maximize compatibility across browsers.

```markup
<script
  src="{WIDGET_URL}"
  id="clevy-widget"
  data-position="left"
  data-widget-metadata="%7B%22firstname%22%3A%22Jane%22%2C%22email%22%3A%22jane.doe%40company.com%22%7D"
  async>
</script>
```

### data-position

By default, the widget will be displayed on the right side of the screen. To display the widget on the left instead, simply add `data-position="left"`.

### data-assistant-metadata

To add custom metadata in a widget ([see this page for more information about injecting metadata in the assistant](features.md)), you need to add a `data-widget-metadata` attribute to the widget initialization script tag that contains the encoded (with [javascript's encodeURIComponent function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/encodeURIComponent)) JSON string of the metadata you want to inject.

For example: `data-assistant-metadata="%7B%22email%22%3A%22jane.doe%40company.com%22%7D"`

### data-logo-url

You can configure a custom image to be used as the widget logo by setting this parameter to the URL of your image. You can use a transparent png or a svg to achieve this effect below, or directly use a square image (it will be rounded automatically) without a transparent background to use as the logo.

For example: `data-logo-url="https://cdn.clevy.io/clevy-logo-square-white.png"`

![](<../../.gitbook/assets/image (86).png>)

### data-launcher-fill, data-launcher-background

These two parameters let you change the fill color of the default icons, as well as the background for the launcher button.

Any valid CSS value for these elements is accepted. The default values are:

```markup
<script src="{WIDGET_URL}"
  id="clevy-widget"
  data-launcher-fill="#ffffff"
  data-launcher-background="linear-gradient(135deg, #4f89fc 0, #1965ff 51%, #104dc7 100%)"
  async></script>
```

### data-force-open

Force the widget to open as soon as the script is loaded. Not recommended as it might be a bit agressive for the visitors of the page, but may be useful in some cases!

```html
<script src="{WIDGET_URL}"
  id="clevy-widget"
  data-force-open="true"
  async></script>
```

### data-ref

Set the Assistant's [ref param](features.md#referral-parameter) to trigger a specific flow or step.

```html
<script src="{WIDGET_URL}"
  id="clevy-widget"
  data-ref="someRefParam"
  async></script>
```
