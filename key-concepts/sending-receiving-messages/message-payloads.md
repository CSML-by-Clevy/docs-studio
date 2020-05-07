# Message payloads

CSML message components all have a matching message format for client use. They can be extended by adding additional properties to the `content` wrapper.

```javascript
> Text()
{
  "content": {
    "text": "message"
  },
  "content_type": "text"
}
```

```javascript
> Typing()
{
  "content": {
    "duration": 1000
  },
  "content_type": "typing"
}
```

```javascript
> Wait()
{
  "content": {
    "duration": 1000
  },
  "content_type": "wait"
}
```

```javascript
> Url()
{
  "content": {
    "url": "https://example.com",
    "title": "title",
    "text": "text"
  },
  "content_type": "url"
}
```

```javascript
> Image()
{
  "content": {
    "url": "https://example.com/image.jpg",
  },
  "content_type": "image"
}
```

```javascript
> Audio()
{
  "content": {
    "url": "https://example.com/audio.mp3",
  },
  "content_type": "audio"
}
```

```javascript
> Video()
{
  "content": {
    "url": "https://example.com/video.mp4",
  },
  "content_type": "video"
}
```

```javascript
> File()
{
  "content": {
    "url": "https://example.com/video.mp4",
  },
  "content_type": "file"
}
```

```javascript
> Button()
{
  "content": {
    "title": "Button title",
    "payload": "Button payload"
  },
  "content_type": "button"
}
```

```javascript
> Payload()
{
  "content": {
    "payload": "Custom payload"
  },
  "content_type": "payload"
}
```

```javascript
> Question()
{
  "content": {
    "title": "Question",
    "buttons": [Button]
  },
  "content_type": "question"
}
```

## Child components

Component payloads can be included into one another seamlessly. For example: 

```cpp
// CSML
say Question(
    "Where is Brian",
    buttons = [
        Button("In the kitchen"),
        Button("Somewhere else"),
    ]
)

// JSON output
{
    "content": {
    "title": "Question",
    "buttons": [
      {
        "content_type": "button",
        "content": {
          "title": "In the kitchen",
        }
      },
      {
        "content_type": "button",
        "content": {
          "title": "Somewhere else",
        }
      },
    ],
  },
  "content_type": "video"
}
```

