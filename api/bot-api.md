# Bot API



The Bot API allows you to retrieve information about your bot and its flows

## GET /bot

Retrieve the bot for this integration

### Request example

```text
curl "https://clients.csml.dev/prod/api/bot" \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -H 'x-api-key: ${X-API-KEY}' \
     -H 'x-api-signature: ${X-API-SIGNATURE}'
```

### Response example

```javascript
{
  "updated_at": "2019-12-13T01:27:38.653Z",
  "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
  "name": "test",
  "created_at": "2019-12-11T18:59:39.391Z",
  "description": null,
  "default_flow": "fd2e74e5-1305-4650-a300-8097d71df01f",
  "id": "06e63f93-2e1a-4f76-b174-9c4aa6e31401",
  "status": "PUBLISHED",
  "tags": [],
  "file_ids": [],
  "flows": [
    {
      "intents": [],
      "updated_at": "2019-12-13T01:31:51.507Z",
      "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
      "name": "Default",
      "created_at": "2019-12-11T18:59:39.610Z",
      "description": "Default custom flow",
      "id": "fd2e74e5-1305-4650-a300-8097d71df01f",
      "bot_id": "06e63f93-2e1a-4f76-b174-9c4aa6e31401",
      "commands": [
        "/default"
      ],
      "content": "start:\n\tsay \"hello!\"\n\tgoto end",
      "status": "PUBLISHED",
      "tags": []
    }
  ]
}
```

## GET /bot/flows

Retrieve all the flows in the current bot

### Request example

```text
curl "https://clients.csml.dev/prod/api/bot/flows" \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -H 'x-api-key: ${X-API-KEY}' \
     -H 'x-api-signature: ${X-API-SIGNATURE}'
```

### Response example

```javascript
[
  {
    "intents": [],
    "updated_at": "2019-12-13T01:31:51.507Z",
    "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
    "name": "Default",
    "created_at": "2019-12-11T18:59:39.610Z",
    "description": "Default custom flow",
    "id": "fd2e74e5-1305-4650-a300-8097d71df01f",
    "bot_id": "06e63f93-2e1a-4f76-b174-9c4aa6e31401",
    "commands": [
      "/default"
    ],
    "content": "start:\n\tsay \"hello!\"\n\tgoto end",
    "status": "PUBLISHED",
    "tags": []
  },
  ...
]
```

## GET /bot/flows/:flow\_id

Retrieve a specific flow

### Request example

```text
curl "https://clients.csml.dev/prod/api/bot/flows/${FLOW_ID}" \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -H 'x-api-key: ${X-API-KEY}' \
     -H 'x-api-signature: ${X-API-SIGNATURE}'
```

### Response example

```javascript
{
  "intents": [],
  "updated_at": "2019-12-13T01:31:48.849Z",
  "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
  "name": "Default",
  "created_at": "2019-12-11T18:59:39.610Z",
  "description": "Default custom flow",
  "id": "fd2e74e5-1305-4650-a300-8097d71df01f",
  "bot_id": "06e63f93-2e1a-4f76-b174-9c4aa6e31401",
  "commands": [
    "/default"
  ],
  "content": "start:\n\tsay \"hello!\"\n\tgoto end",
  "status": "PUBLISHED",
  "tags": []
}
```

