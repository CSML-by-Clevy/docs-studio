# Introduction

The CSML Studio exposes an API, available as a Channel. To enable the CSML Studio API, select a bot, then go to Channels &gt; Create Channel &gt; Webhook \(API\), and take note of the given credentials.

## Endpoints

All calls are to be made to `https://clients.csml.dev`.

The API is versioned, and alls must be prefixed by their version number. The most recent version is `prod`. The API is reachable on route prefix `/api`.

Hence, the complete endpoint for the API is `https://clients.csml.dev/prod/api`.

## Authentication

Calls are authenticated with the combination of two separate keys: API Key and API Secret.

The **API Key** is the public key and can be put in clear client-side. The **API Secret** should never be shared publicly.

To authenticate all your HTTP calls, you need to set the following headers: `X-Api-Key` and `X-Api-Digest`. The CSML Studio API uses HMAC authentication to ensure that all calls are properly signed with both the API Key and API Secret, while preventing man-in-the-middle attacks and replay attacks.

**Warning: The X-Api-Signature MUST NEVER be done on the client side.**

In the `X-Api-Key` header, concatenate the API Key and the current unix timestamp \(in seconds\), separated by the `|` character.  
In the `X-Api-Signature` header, provide the hexadecimal sha-256 hash of the `X-Api-Key` header value, signed with your API Secret.

The CSML server will be able to validate that both the API Key and the API Secret used are valid, without requiring you to provide the API Secret in clear text. Replay attacks are preventing by invalidating all calls a few minutes after the timestamp provided in the X-Api-Key header.

Here is an example implementation in javascript:

```javascript
const crypto = require('crypto');

const UNIX_TIMESTAMP = Math.floor(Date.now() / 1000);

const XApiKey = `${API_KEY}|${UNIX_TIMESTAMP}`;
const signature = crypto.createHmac('sha256', secret)
  .update(XApiKey, 'utf-8')
  .digest('hex');
const XApiSignature = `sha256=${signature}`;
```

