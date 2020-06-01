# Broadcasts API

A broadcast is a message sent from the bot to a user, without the user sending a request first. It is a great way to reengage your users, for example to remind them about a conversation they didn't finish, or let them know a product they ordered has been shipped.

## POST /broadcasts

Send a broadcast on the requested channel \(supported channels only\) to the requested client. Broadcast requests are queued and usually sent within a few seconds. If a target is unavailable, no error is generated.

### Request example

```text
curl "https://clients.csml.dev/v1/api/broadcasts" \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -H 'x-api-key: ${X-API-KEY}' \
     -H 'x-api-signature: ${X-API-SIGNATURE}'
     -d $'{
  "payload": {
    "content": {
      "flow_id": "myflow",
      "close_flows": true
    },
    "content_type": "flow_trigger"
  },
  "client": {
    "user_id": "some-user-id"
  },
  "metadata": {
    "somekey": "somevalue"
  }
}'

```

### Response example

```javascript
{
  "request_id": "57d2d4ab-6994-4449-82bf-206619d9d063",
  "client": {
    "user_id": "some-user-id",
    "bot_id": "bc5de819-e4c5-463e-9090-5648fac3a570",
    "channel_id": "b1f74f8d-99b6-40b2-ad64-00ec364bae23"
  },
  "payload": {
    "content_type": "flow_trigger",
    "content": {
      "flow_id": "myflow",
      "close_flows": true
    }
  },
  "metadata": {
    "somekey": "somevalue"
  }
}
```

