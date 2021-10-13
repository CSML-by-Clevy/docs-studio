---
description: The Bot API allows you to retrieve information about your bot and its flows
---

# Bot API

{% swagger baseUrl="https://clients.csml.dev/v1" path="/api/bot" method="get" summary="Get bot" %}
{% swagger-description %}
Retrieve the bot for this integration
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```javascript
{
  "id": "06e63f93-2e1a-4f76-b174-9c4aa6e31401",
  "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
  "name": "MyBot",
  "description": "This is my bot",
  "default_flow": "fd2e74e5-1305-4650-a300-8097d71df01f",
  "created_at": "2019-12-11T18:59:39.391Z",
  "updated_at": "2019-12-13T01:27:38.653Z",
  "env": {
    "MY_VAR": "somevalue"
  },
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://clients.csml.dev/v1" path="/api/bot" method="put" summary="Update bot" %}
{% swagger-description %}
Update a bot's name, default_flow and/or description. Parameters that are not set will not be changed.
{% endswagger-description %}

{% swagger-parameter in="body" name="env" type="object" %}
key/value hash of bot environment variables
{% endswagger-parameter %}

{% swagger-parameter in="body" name="default_flow" type="string" %}
ID of default flow to set (flow must exist)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://clients.csml.dev/v1" path="/api/bot/flows" method="get" summary="Get bot flows" %}
{% swagger-description %}
Retrieve all the flows in the current bot
{% endswagger-description %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://clients.csml.dev/v1" path="/api/bot/flows" method="post" summary="Create Flow" %}
{% swagger-description %}
Add a new flow to the current bot
{% endswagger-description %}

{% swagger-parameter in="body" name="description" type="string" %}
Description of the flow to create
{% endswagger-parameter %}

{% swagger-parameter in="body" name="commands" type="array" %}
Commands that will trigger the flow.

\


Example: ["some", "command"]
{% endswagger-parameter %}

{% swagger-parameter in="body" name="content" type="string" %}
CSML Flow
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}
Name of the flow
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
  "id": "c3187b49-5833-4572-960f-a6eedd59d9cd",
  "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
  "name": "SomeFlow",
  "bot_id": "3944ec9b-81c8-4b58-854d-b412c89b8e42",
  "commands": [
    "/someflow",
    "some command"
  ],
  "content": "start:\n  say \"Hi!\"\n  goto end",
  "created_at": "2020-08-23T17:54:39.461Z",
  "updated_at": "2020-08-23T17:54:39.461Z"
} 
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://clients/csml.dev/v1" path="/api/bot/flows/:flow_id" method="get" summary="Get flow" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="flow_id" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://clients/csml.dev/v1" path="/api/bot/flows/:flow_id" method="put" summary="Update flow" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="flow_id" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="commands" type="array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="content" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="204" description="" %}
```javascript
{
  "id": "c3187b49-5833-4572-960f-a6eedd59d9cd",
  "organization_id": "0b50ddf9-052b-4dd6-9901-459caa15ed33",
  "name": "SomeFlow",
  "bot_id": "3944ec9b-81c8-4b58-854d-b412c89b8e42",
  "commands": [
    "/someflow",
    "some command"
  ],
  "content": "start:\n  say \"Hi!\"\n  goto end",
  "created_at": "2020-08-23T17:54:39.461Z",
  "updated_at": "2020-08-23T17:54:39.461Z"
} 
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://clients.csml.dev/v1" path="/api/bot/usage" method="get" summary="Bot usage" %}
{% swagger-description %}
Get usage information about a bot
{% endswagger-description %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://clients.csml.dev/v1" path="/api/bot/validate" method="post" summary="Validate bot" %}
{% swagger-description %}
Validate bot data against the CSML interpreter
{% endswagger-description %}

{% swagger-parameter in="body" name="" type="object" %}
The bot object as retrieved from the GET /bot operation
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
// bot is valid
{
  "valid": true
}

// bot is invalid
{
  "valid": false,
  "errors": [
    {
      "flow": "someFlow",
      "step": "someStep",
      "line": 0,
      "column": 0,
      "message": "error message"
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://clients.csml.dev/v1" path="/api/bot/build" method="post" summary="Build bot" %}
{% swagger-description %}
Build a new version of the bot
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```javascript
{
  "id": "3944ec9b-81c8-4b58-854d-b412c89b8e42",
  "name": "test",
  "default_flow": "4c9d5234-cad2-4c97-be47-a82f31ec26a3",
  "created_at": "2020-08-23T17:47:21.229Z",
  "version_id": "40e19091-9f5b-4f38-9494-9a97a1072640",
  "engine_version": "1.4.0",
  "flows": [
    {
      "id": "4c9d5234-cad2-4c97-be47-a82f31ec26a3",
      "name": "Default",
      "commands": [
        "/default"
      ],
      "content": "start:\n  say \"Hello\"\n  goto end",
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://clients.csml.dev/v1" path="/api/bot/build" method="get" summary="Get bot build version" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="version_id" type="string" %}
ID of version to retrieve.

\


Defaults to `latest` if not set.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
  "id": "3944ec9b-81c8-4b58-854d-b412c89b8e42",
  "name": "test",
  "default_flow": "4c9d5234-cad2-4c97-be47-a82f31ec26a3",
  "created_at": "2020-08-23T17:47:21.229Z",
  "version_id": "40e19091-9f5b-4f38-9494-9a97a1072640",
  "engine_version": "1.4.0",
  "flows": [
    {
      "id": "4c9d5234-cad2-4c97-be47-a82f31ec26a3",
      "name": "Default",
      "commands": [
        "/default"
      ],
      "content": "start:\n  say \"Hello\"\n  goto end",
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}
