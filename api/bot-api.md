---
description: The Bot API allows you to retrieve information about your bot and its flows
---

# Bot API

## GET /bot

Retrieve the bot for this integration

### Request example

```text
curl "https://clients.csml.dev/v1/api/bot" \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -H 'x-api-key: ${X-API-KEY}' \
     -H 'x-api-signature: ${X-API-SIGNATURE}'
```

### Response example

```javascript
{
  "id": "06e63f93-2e1a-4f76-b174-9c4aa6e31401",
  "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
  "name": "MyBot",
  "description": "This is my bot",
  "default_flow": "fd2e74e5-1305-4650-a300-8097d71df01f",
  "created_at": "2019-12-11T18:59:39.391Z",
  "updated_at": "2019-12-13T01:27:38.653Z",
  "flows": [
      {
      "id": "fd2e74e5-1305-4650-a300-8097d71df01f",
      "bot_id": "06e63f93-2e1a-4f76-b174-9c4aa6e31401",
      "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
      "name": "Default",
      "description": "Default custom flow",
      "commands": [
        "/default"
      ],
      "content": "start:\n\tsay \"hello!\"\n\tgoto end",
      "created_at": "2019-12-11T18:59:39.610Z",
      "updated_at": "2019-12-13T01:31:51.507Z",
    },
    ...
  ]
}
```

## GET /bot/flows

Retrieve all the flows in the current bot

### Request example

```text
curl "https://clients.csml.dev/v1/api/bot/flows" \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -H 'x-api-key: ${X-API-KEY}' \
     -H 'x-api-signature: ${X-API-SIGNATURE}'
```

### Response example

```javascript
[
  {
    "id": "fd2e74e5-1305-4650-a300-8097d71df01f",
    "bot_id": "06e63f93-2e1a-4f76-b174-9c4aa6e31401",
    "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
    "name": "Default",
    "description": "Default custom flow",
    "commands": [
      "/default"
    ],
    "content": "start:\n\tsay \"hello!\"\n\tgoto end",
    "created_at": "2019-12-11T18:59:39.610Z",
    "updated_at": "2019-12-13T01:31:51.507Z",
  },
  ...
]
```

## GET /bot/flows/:flow\_id

Retrieve a specific flow

### Request example

```text
curl "https://clients.csml.dev/v1/api/bot/flows/${FLOW_ID}" \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -H 'x-api-key: ${X-API-KEY}' \
     -H 'x-api-signature: ${X-API-SIGNATURE}'
```

### Response example

```javascript
  {
    "id": "fd2e74e5-1305-4650-a300-8097d71df01f",
    "bot_id": "06e63f93-2e1a-4f76-b174-9c4aa6e31401",
    "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
    "name": "Default",
    "description": "Default custom flow",
    "commands": [
      "/default"
    ],
    "content": "start:\n\tsay \"hello!\"\n\tgoto end",
    "created_at": "2019-12-11T18:59:39.610Z",
    "updated_at": "2019-12-13T01:31:51.507Z",
  }
```

## GET /bot/usage

Get usage information about a bot

### Request example

```text
curl "https://clients.csml.dev/v1/api/bot/usage" \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -H 'x-api-key: ${X-API-KEY}' \
     -H 'x-api-signature: ${X-API-SIGNATURE}'
```

### Response example

```javascript
{
  "currentmonth": {
    "messages": 0,
    "clients": 0
  },
  "last30d": {
    "messages": 0,
    "clients": 0
  },
  "lastmonth": {
    "messages": 0,
    "clients": 0
  }
}
```

