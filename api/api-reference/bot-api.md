---
description: The Bot API allows you to retrieve information about your bot and its flows
---

# Bot API

{% api-method method="get" host="https://clients.csml.dev/v1" path="/api/bot" %}
{% api-method-summary %}
Get bot
{% endapi-method-summary %}

{% api-method-description %}
Retrieve the bot for this integration
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://clients.csml.dev/v1" path="/api/bot" %}
{% api-method-summary %}
Update bot
{% endapi-method-summary %}

{% api-method-description %}
Update a bot's name, default\_flow and/or description. Parameters that are not set will not be changed.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="default\_flow" type="string" required=false %}
ID of default flow to set \(flow must exist\)
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://clients.csml.dev/v1" path="/api/bot/flows" %}
{% api-method-summary %}
Get bot flows
{% endapi-method-summary %}

{% api-method-description %}
Retrieve all the flows in the current bot
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://clients.csml.dev/v1" path="/api/bot/flows" %}
{% api-method-summary %}
Create Flow
{% endapi-method-summary %}

{% api-method-description %}
Add a new flow to the current bot
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="description" type="string" required=false %}
Description of the flow to create
{% endapi-method-parameter %}

{% api-method-parameter name="commands" type="array" required=false %}
Commands that will trigger the flow.  
Example: \["some", "command"\]
{% endapi-method-parameter %}

{% api-method-parameter name="content" type="string" required=true %}
CSML Flow
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
Name of the flow
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://clients/csml.dev/v1" path="/api/bot/flows/:flow\_id" %}
{% api-method-summary %}
Get flow
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="flow\_id" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://clients/csml.dev/v1" path="/api/bot/flows/:flow\_id" %}
{% api-method-summary %}
Update flow
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="flow\_id" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="commands" type="array" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="content" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://clients.csml.dev/v1" path="/api/bot/usage" %}
{% api-method-summary %}
Bot usage
{% endapi-method-summary %}

{% api-method-description %}
Get usage information about a bot
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://clients.csml.dev/v1" path="/api/bot/validate" %}
{% api-method-summary %}
Validate bot
{% endapi-method-summary %}

{% api-method-description %}
Validate bot data against the CSML interpreter
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="bot" type="object" required=false %}
a bot object as returned from the GET /bot operation
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://clients.csml.dev/v1" path="/api/bot/build" %}
{% api-method-summary %}
Build bot
{% endapi-method-summary %}

{% api-method-description %}
Build a new version of the bot
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://clients.csml.dev/v1" path="/api/bot/build" %}
{% api-method-summary %}
Get bot build version
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="version\_id" type="string" required=false %}
ID of version to retrieve.  
Defaults to \`latest\` if not set.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

