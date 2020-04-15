# Features

## Available components

Whatsapp \(via MessageBird\) supports the following components:

* `Text()` or string templates
* `Object()` or JSON templates
* `Wait()`
* `Image()`
* `Video()`
* `Audio()`
* `File()`
* `Url()`

Markdown is partially supported \(only **bold**, _italic_ and ~~strikethrough~~\). 

To send completely custom requests, use `say Object(...)` . The content of the object will be forwarded as is in the request body.

## Limitations

### Buttons

Whatsapp has a very limited set of interactive components. Buttons for example are textual only, and your users will have to type the actual text of the button.

![To select &quot;Latest numbers&quot;, the user has to type &quot;1&quot; or use the emoji &#x1F522;](../../.gitbook/assets/img_0161.PNG)

The mapping of `Question()` and `Button()` components to text is performed  automatically. However you need to set the right `title` and `accepts` values in order to correctly match the user's input.

### Typing

The typing indicator `...` is not supported and replaced by a simple `Wait()` component of the same duration.

### Urls

The `Url()` component does not support any alternative text or title. Only the given url will be shown as is.  
For instance, the following code:

```cpp
start:
	say Url("https://www.google.com", text="Go to google")
	goto end
```

Has the following output:

![](../../.gitbook/assets/img_0162.jpg)

### Video

You must upload videos in mp4 format. Videos hosted on Youtube, Dailymotion or Vimeo will not display \(use the `Url()` component\).

### Audio

You must upload audio files in mp3 format. Audio files hosted on Spotify, Deezer or Soundcloud will not display \(use the `Url()` component\).

### Files \(any type\)

There is a hard limit of 25MB for all uploaded files. Also, the file upload process happens asynchronously on Whatsapp, so messages might show out of order if there is a large upload with not enough time left for its upload before sending the next message.

### Carousel, Card

Carousel\(\) and Card\(\) are currently not supported.



