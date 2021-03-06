# Preprocessing

CSML Studio also offers a way to preprocess every incoming event of certain types, in order to add some metadata or transform it. Here are some use cases:

* transcribe audio inputs
* translate incoming text
* save uploaded files to a dedicated file storage
* perform OCR on each uploaded image
* run a custom natural language processing library on text inputs \(for that use case, you may also want to look at [Natural Language Processing](../nlp/)\)

Preprocessors are simply external apps that are run on every incoming event \(of the given type\) and return a valid CSML event. The only specificity is that the parameters it must accept and return are standard CSML event payloads. Preprocessors that fail to accept or return such payloads are simply ignored and your incoming event will not be transformed.

## How to add a CSML preprocessor

Let's create a simple Text preprocessor that will return a picture of a hot dog if the user had the word "hot dog" in their input, or change the text to `"Not hot dog"`  otherwise.

To add a preprocessor, you first need to add a _preprocessor-compatible_ app under the apps section \(see here\). For this tutorial, let's just use the Quick Mode, but of course you can use Complete Mode as well.

This is the code we are going to use:

```javascript
exports.handler = async (event) => {

  const text = event.content.text;

  if (text.toLowerCase().includes('hot dog')) {
    return {
      content_type: 'image',
      content: {
        url: 'https://www.papillesetpupilles.fr/wp-content/uploads/2019/04/Hot-dog-%C2%A9nikolaskus-shutterstock.jpg',
        _original_event: event,
      },
    };
  }

  return {
    content_type: 'text',
    content: {
      text: 'Not hot dog!',
      _original_event: event,
    },
  };

};

```

It is really simple: if the user text input contains the words "hot dog" anywhere, then return an image of a hotdog. Otherwise, change the text to "Not hot dog". In both cases, the original, untransformed event is still accessible with `event._original_event` in you CSML code, if needed.

Next, go to **Apps &gt; Add Custom App** and under **Quick Mode**, simply copy and paste it, select a name for your app \(for instance, `hotdog` seems like a fitting name\), and click save.

![](../../.gitbook/assets/image%20%2834%29.png)

Then, head to **Settings &gt; Preprocessing**. We only want to preprocess text events, but of course, we could do a similar app for other types of events. 

![](../../.gitbook/assets/image%20%2835%29.png)

Now, back to the CSML Editor, you can do something like the following:

```cpp
start:
  if (event.get_type() == "image") say Image(event)
  else say event
  goto end
```

![](../../.gitbook/assets/image%20%2832%29.png)

