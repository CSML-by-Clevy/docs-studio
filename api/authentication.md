# Authentication

## Authentication

All API calls are authenticated with the combination of two separate keys: **API Key** and **API Secret**.

The **API Key** is the public key and can be put in clear client-side (your website, your app...). The **API Secret** should never be shared publicly and should only be set on your server.

There are two different modes of authentication for Studio endpoints: **Private** or **Public**.

## Public Endpoints Authentication

**Public Endpoints** (consisting of Chat and Broadcasts API endpoints) can be authentified by providing only the value of the Api Key in the X-Api-Key header. They can be accessed from the frontend, i.e by creating your own chat interface integrated in your app or website.

#### Implementation examples

When calling Chat and Broadcasts API endpoints, you only need to set the X-Api-Key header as follows:

```
curl -X "POST" "https://API_ENDPOINT" \
     -H 'content-type: application/json' \
     -H 'X-Api-Key: YOUR_API_KEY' \
     -d $'YOUR_REQUEST_BODY'
```

## Private Endpoints Authentication

**Private Endpoints** are endpoints that should only be accessible to the developer of the chabot, allowing to modify the chatbot in its entirety or access conversation data (Bot and Conversations API endpoints). To authentify your Private Endpoints requests you need to set the `X-Api-Key` and `X-Api-Signature` headers. The CSML Studio Private APIs use HMAC authentication to ensure that all calls are properly signed with both the API Key and API Secret, while preventing man-in-the-middle attacks and replay attacks

{% hint style="danger" %}
**The X-Api-Signature process MUST NEVER be done on the client side, as this would let any person in control of your API Secret also control your bot (make changes, get user data...).** Obviously, never share your API Secret with anyone in clear text.
{% endhint %}

In the `X-Api-Key` header, concatenate the API Key and the current unix timestamp (in seconds), separated by the `|` character.\
In the `X-Api-Signature` header, provide the hexadecimal sha-256 hash of the `X-Api-Key` header value, signed with your API Secret.

The CSML server will be able to validate that both the API Key and the API Secret used are valid, without requiring you to provide the API Secret in clear text. Replay attacks are prevented by invalidating all calls a few minutes after the timestamp provided in the X-Api-Key header.

#### Implementation examples

To authenticate your Private calls, you need to calculate the signature based on the Api Key and the Api Secret that you can find in CSML Studio, as well as the current timestamp. Here are implementation examples of the X-Api-Key and X-Api-Signature headers in Node.js and Python.

**NB: this calculation should never be performed client-side!**

{% tabs %}
{% tab title="Node.js" %}
```javascript
const crypto = require('crypto');

const UNIX_TIMESTAMP = Math.floor(Date.now() / 1000);

const XApiKey = `${API_KEY}|${UNIX_TIMESTAMP}`;
const signature = crypto.createHmac('sha256', secret)
  .update(XApiKey, 'utf-8')
  .digest('hex');
const XApiSignature = `sha256=${signature}`;
```
{% endtab %}

{% tab title="Python" %}
```python
import time
import hmac
import hashlib

timestamp = str(int(time.time()))
x_api_key = ${API_KEY} + "|" + timestamp

signature = hmac.new(
    str.encode(${API_SECRET}),
    x_api_key.encode('utf8'),
    digestmod=hashlib.sha256
  ).hexdigest()
x_api_signature = "sha256=" + signature
```
{% endtab %}
{% endtabs %}

Then, perform an authenticated call as follows:

```
curl -X "POST" "https://API_ENDPOINT" \
     -H 'content-type: application/json' \
     -H 'X-Api-Key: YOUR_API_KEY_AND_TIMESTAMP' \
     -H 'X-Api-Signature: YOUR_CALCULATED_API_SIGNATURE' \
     -d $'YOUR_REQUEST_BODY'
```
