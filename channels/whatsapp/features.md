# Features and Limitations

## Features

### Available components

Whatsapp supports the following components:

* Simple texts
* `Wait()` and `Typing()`
* Medias: `Image(), Video(), Audio(), File()`
* `Url()`
* `Question()` and `QuickReply()`

Markdown is partially supported (only **bold**, _italic_ and ~~strikethrough~~).

### QR Codes Messages

Whatsapp provides an easy way to generate QR codes that let users reach your chatbot easily. You can read more about it here: [https://developers.facebook.com/docs/whatsapp/business-management-api/qr-codes](https://developers.facebook.com/docs/whatsapp/business-management-api/qr-codes)

## Limitations

### Channel Availability

As a security measure, user access tokens expire after about 60 days. If your Whatsapp chatbot remains unused for a longer time, the token will be automatically expired and you will need to reconnect your app to restore it.

### Buttons

Whatsapp has a very limited set of interactive components. Buttons for example are textual only, and your users will have to type the actual text of the button

The mapping of `Question()` and `Button()` components to text is performed automatically. However you need to set the right `title` and `accepts` values in order to correctly match the user's input.

{% hint style="warning" %}
The title of a button must be between 1-20 characters long. You can however manually set a longer payload if needed:

`say Button("Click here!", payload="MY_BUTTON_CLICK_HERE_PAYLOAD")`
{% endhint %}

### Urls

The `Url()` component does not support any alternative text or title. Only the given url will be shown as is.\
For instance, the following code:

```cpp
start:
    say Url("https://www.google.com", text="Go to google")
    goto end
```

Has the following output:

![](../../.gitbook/assets/img\_0162.jpg)

### Video

You must upload videos in mp4 format. Videos hosted on platforms such as Youtube, Dailymotion or Vimeo will not display (use the `Url()` component).

### Audio

You must upload audio files in mp3 format. Audio files hosted on platforms such as Spotify, Deezer or Soundcloud will not display (use the `Url()` component).

### Files

There is a hard limit of 25MB for all uploaded files (including image, video and audio files).

In a `File()` component, not all file types are supported. A list of supported file types could not be found, but it is safe to recommend using very common file types only.

The file upload process happens asynchronously on Whatsapp, so messages might show out of order if there is a large upload with not enough time left for its upload before sending the next message.

### Carousel, Card

`Carousel()` and `Card()` components are not supported.
