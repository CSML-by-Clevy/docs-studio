---
description: >-
  CSML Studio offers a number of other bot configuration options. Let's do a
  quick tour!
---

# Bot Configuration Options

## Bot-Wide Environment Variables

When you need to access some static values across all your users and all your flows, you should use **Bot Environment Variables**.

These values are injected in your conversations under the `_env` global variable and are accessible everywhere, without ever being injected in the current user's memory. They are also encrypted for enhanced security.

This is a perfect use case for API keys or secrets, as well as global configuration options.

![](../.gitbook/assets/image%20%2884%29.png)

## Self-Hosted CSML Engine

If you have strong requirements for data hosting or prefer hosting the CSML Engine on your own servers, you may want to use the On-Premise feature. By using this feature, you have full control over what version of CSML Engine is used at any given time \(the Studio will always default to the latest available version otherwise\), but you also have the responsibility of maintaining and scaling the engine according to your usage. We recommend that you only use this option if you really know what you are doing or if you have strong legal \(i.e data privacy, compliance\) requirements for doing so.

![](../.gitbook/assets/image%20%2886%29.png)



