---
description: 'With the Conversations API, you can manage your client''s conversation statuses'
---

# Conversations API

## POST /conversations/open

Find out whether a user currently has an open conversation.

### Request example

```text
curl -X "POST" "https://clients.csml.dev/prod/api/conversations/open" \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -H 'x-api-key: ${X-API-KEY}' \
     -H 'x-api-signature: ${X-API-SIGNATURE}' \
     -d $'{
          "user_id": "some-user-id"
        }'
```

### Response example

```javascript
{
  "has_open": true,
  "conversation": {
    "id": "43d5939f-4afc-4953-9e53-4c28b33cedd8",
    "client": {
      "channel_id": "dd446008-3768-41df-9be9-f6ea0371f920",
      "user_id": "some-user-id",
      "bot_id": "b797a3b6-ad8c-446c-acfe-dfcafd787f4e"
    },
    "flow_id": "31c2c4b0-05d6-44ce-9442-e87e9ae7e8a2",
    "step_id": "start",
    "metadata": {
      "somekey": "somevalue",
    },
    "status": "OPEN",
    "last_interaction_at": "2019-11-16T19:57:42.219Z",
    "created_at": "2019-11-16T19:57:42.219Z"
  }
}
```

