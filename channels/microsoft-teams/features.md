# Features

## Broadcast API

The Microsoft Teams channel supports the [broadcast API](../../api/api-reference/broadcasts-api.md).

* The client user_id must be set to a valid conversationId (as returned in every conversation's metadata).
* No broadcast can be sent to a user that has not already actively interacted with the chatbot.

## Event Metadata

A sample `_metadata`  for an incoming event will be similar to the following object:

```javascript
{
  "id": "29:1s83dfDjC67Mst-8raeSEanxC9xENBhZpVcDA2pSIa0ItR3hhYa-xP-ttaSPKKYkSdC1LL7Eq9Q3a7jNoNcCdPQ",
  "objectId": "87209afd-cad1-41e7-bdee-048c600f5859",
  "name": "John Doe",
  "givenName": "John",
  "surname": "Doe",
  "email": "john.doe@company.com",
  "userPrincipalName": "john.doe@company.com",
  "tenantId": "jn8si7dd-7e22-4e93-aa20-4d44f18627cf",
  "userRole": "user",
  "conversationId": "a:1KmhjQAB7zmrktvuoQv4EnRI_Hx6vH6a_JPoQvhdrVFTLf78tavBHtsUjst9iecdBybfiKbIQSTiMlm6wApO2o6R-EZSdAj8_Ll2BVPv5rZ9zZxPZmMTwMk59kIojSuDM",
  "_channel": {
    "type": "msteams",
    "name": "John's channel"
  }
}
```
