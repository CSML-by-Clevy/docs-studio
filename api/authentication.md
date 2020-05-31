# Authentication

## Authentication

All API calls are authenticated with the combination of two separate keys: API Key and API Secret.

The **API Key** is the public key and can be put in clear client-side. The **API Secret** should never be shared publicly.

To authenticate all your HTTP calls, you need to set the following headers: `X-Api-Key` and `X-Api-Digest`. The CSML Studio API uses HMAC authentication to ensure that all calls are properly signed with both the API Key and API Secret, while preventing man-in-the-middle attacks and replay attacks.

{% hint style="danger" %}
**The X-Api-Signature process MUST NEVER be done on the client side, as this would give control to your bot to any person in control of your API Secret.**
{% endhint %}

In the `X-Api-Key` header, concatenate the API Key and the current unix timestamp \(in seconds\), separated by the `|` character.  
In the `X-Api-Signature` header, provide the hexadecimal sha-256 hash of the `X-Api-Key` header value, signed with your API Secret.

The CSML server will be able to validate that both the API Key and the API Secret used are valid, without requiring you to provide the API Secret in clear text. Replay attacks are prevented by invalidating all calls a few minutes after the timestamp provided in the X-Api-Key header.

Here is an example implementation in nodejs:

```javascript
const crypto = require('crypto');

const UNIX_TIMESTAMP = Math.floor(Date.now() / 1000);

const XApiKey = `${API_KEY}|${UNIX_TIMESTAMP}`;
const signature = crypto.createHmac('sha256', secret)
  .update(XApiKey, 'utf-8')
  .digest('hex');
const XApiSignature = `sha256=${signature}`;
```

