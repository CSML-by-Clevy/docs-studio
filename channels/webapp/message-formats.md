# Message Formats

## Text

```cpp
say "His palms are sweaty, knees weak, arms are heavy" // short form
say Text("There's vomit on his sweater already, mom's spaghetti") // long form
```

![](../../.gitbook/assets/capture-de-cran-2020-04-30-09.50.41.png)

The `Text` component of the Webapp channel also supports some basic Markdown:

```cpp
say "He's _nervous_, but **on the surface** he looks [calm and ready](https://www.youtube.com/watch?v=_Yhyp-_hX2s)"
```

![](../../.gitbook/assets/capture-de-cran-2020-04-30-10.58.52.png)

## Typing, Wait

```cpp
say Typing(1000)
```

![](../../.gitbook/assets/cleanshot-2020-04-30-at-09.49.26.gif)

Obviously, `Wait` is also supported \(it simply does not display a typing indicator or anything for the given duration\).

## Image

```cpp
say Image("https://images.unsplash.com/photo-1560114928-40f1f1eb26a0")
```

![](../../.gitbook/assets/capture-de-cran-2020-04-30-09.46.21.png)

## Question, Button

```cpp
say Question(
  "Hi! My name is:", // equivalent to title="Hi! My name is:",
  buttons=[Button("What?"), Button("Who?")]
)
```

![](../../.gitbook/assets/capture-de-cran-2020-04-30-09.51.57.png)

If you need to retrieve a specific data when clicking on either button, use the `payload` argument of the Button component:

```cpp
say Question(
  "Hi! My name is:",
  buttons=[
        Button("What?", payload="btn1"),
        Button("Who?", payload="btn2"),
  ]
)
hold
say "user clicked on button with the {{event}} payload"
```

![](../../.gitbook/assets/capture-de-cran-2020-04-30-09.57.09.png)

{% hint style="info" %}
The Webapp channel also supports single `Button` components. However, as cross-channel support for single buttons is not guaranteed, we encourage you to use the standard Question component instead, with a title.
{% endhint %}

## QuickReply

Quick replies are similar to Questions, where the buttons are removed from view once the user has selected one of them. In a majority of scenarios, you should prefer QuickReplies over regular questions, especially when you don't want the user to be able to scroll up and select one of the buttons after they have made a first choice. Questions should be used when a button is used as a trigger to a given flow \(as configured in the bot's [AI Rules](../../getting-started/nlp/ai-rules.md)\).

```cpp
say QuickReply(
  "Do you like cheese?",
  buttons=[Button("Yes 🧀"), Button("Also yes 🫕")]
)
```

![](../../.gitbook/assets/image%20%2882%29.png)

{% hint style="info" %}
Try this bot: [https://play.csml.dev/bot/0e85f280-d502-4535-8b78-fb763979777e](https://play.csml.dev/bot/0e85f280-d502-4535-8b78-fb763979777e)
{% endhint %}

## Video, Audio

The Video component supports links to mp4 files, as well as Youtube, Vimeo and Dailymotion URLs. The Audio component supports links to mp3 files, as well as Spotify, Soundcloud and Deezer URLs.

```cpp
say Video("https://www.youtube.com/watch?v=lqBhgEQ4LT0")
```

![](../../.gitbook/assets/capture-de-cran-2020-04-30-10.01.51.png)

```cpp
say Audio("https://open.spotify.com/track/1xB3YT8Rakvnfcc1dp2kzJ")
```

![](../../.gitbook/assets/capture-de-cran-2020-04-30-10.03.55.png)

{% hint style="info" %}
**Standard limitations apply**: if the end user is not logged in to a valid spotify/deezer/soundcloud account, only 30s will be playable in the audio component.

For full control over the clip, prefer using a standard mp3 file URL.
{% endhint %}

## Url

The `Url` component will automatically retrieve the target's favicon if available. If a `text` parameter is present, it will be used as the component's title.

```cpp
say Url("https://www.wikipedia.org/", text="Visit Wikipedia")
```

![](../../.gitbook/assets/capture-de-cran-2020-04-30-10.50.11.png)

## Carousel, Card

A `Carousel` is essentially a collection of `Card` elements A single `Card` will display as a `Carousel` of 1 element. Each `Card` can have a maximum of 2 `Button` elements.

```cpp
do card1 = Card(
    "The Marshall Mathers LP",
    subtitle="Release date: May 23, 2000",
    image_url="https://upload.wikimedia.org/wikipedia/en/a/ae/The_Marshall_Mathers_LP.jpg",
    buttons=[Button("Listen to this album", payload="marshallmatherslp1")]
)
do card2 = Card(
    "The Slim Shady LP",
    subtitle="Release date: February 23, 1999",
    image_url="https://upload.wikimedia.org/wikipedia/en/3/35/Eminem_-_The_Slim_Shady_LP_CD_cover.jpg",
    buttons=[Button("Listen to this album", payload="theslimshadylp")]
)
do card3 = Card(
    "The Marshall Mathers LP 2",
    subtitle="Release date: November 5, 2013",
    image_url="https://upload.wikimedia.org/wikipedia/en/8/87/The_Marshall_Mathers_LP_2.png",
    buttons=[Button("Listen to this album", payload="marshallmatherslp2")]
)

say Carousel(cards=[card1, card2, card3])
```

![](../../.gitbook/assets/image%20%2811%29.png)

## Calendar

This component will display a rich calendar in the webapp. By default, when passed with no argument, a simple single-date datepicker will appear:

```cpp
say Calendar()
```

![single mode](../../.gitbook/assets/image%20%2871%29.png)

Optional parameters allow to set a `min_date` and/or `max_date` \(by unix timestamp, in milliseconds\) or an `input_mode` to accept `single` \(the default\) `multiple` or `range` inputs by the user:

```cpp
say Calendar(
    min_date=1617494400000, // April 4th, 2021
    max_date=1623974400000, // June 18th, 2021
    input_mode="range" // can also be "multiple" or "single"
)
```

![range mode](../../.gitbook/assets/image%20%2873%29.png)

![multiple mode](../../.gitbook/assets/image%20%2872%29.png)

The `event` value of a Calendar input will be comma-separated values of all user inputs. Also, `event.input_mode` will be set to the mode of the requested calendar, so that you can differenciate between `single`, `multiple` and `range` modes when receiving values.

```cpp
// given this sample CSML code
say Calendar(...)
hold
say "{{event.get_content()}}"

// example single mode
{
  "input_mode":"single",
  "payload":"2021-04-07T00:00:00.000+02:00"
}
// example multiple mode
{
  "input_mode":"multiple",
  "payload":"2021-04-07T00:00:00.000+02:00,2021-04-15T00:00:00.000+02:00,2021-04-20T00:00:00.000+02:00"
}
// example range mode
{
  "input_mode":"range",
  "payload":"2021-04-07T00:00:00.000+02:00,2021-04-15T00:00:00.000+02:00"
}
```

{% hint style="info" %}
Try this bot: [https://play.csml.dev/bot/8ec99c8c-5bfb-44cd-974d-b7781009279b](https://play.csml.dev/bot/8ec99c8c-5bfb-44cd-974d-b7781009279b)
{% endhint %}

## Full reference

For a complete reference of all the code presented on this page, refer to the [following gist](https://gist.github.com/frsechet/a081fd649fc9f37372f144961f19533a):

{% embed url="https://gist.github.com/frsechet/a081fd649fc9f37372f144961f19533a" caption="" %}

