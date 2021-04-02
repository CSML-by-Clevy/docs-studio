# Features and message formats

Workplace Chat is very, very similar to Messenger \(except that it's grey\). Please refer to Messenger's CSML documentation:

{% page-ref page="../messenger/features.md" %}

{% page-ref page="../messenger/message-formats.md" %}

## Broadcasts

Broadcasts can be sent without any limitation to any of your Workplace Chat users, with either their valid Workplace email address or ID as the user\_id.

## Event Metadata

A sample `_metadata`  for an incoming event will be similar to the following object:

```javascript
{
  "_channel": {
    "app_id": "10067197168686",
    "name": "test-22032021",
    "type": "workchat"
  },
  "email": "john.doe@company.com",
  "first_name": "John",
  "id": "581595168271418",
  "last_name": "Doe",
  "link": "https://work.facebook.com/app_scoped_user_id/HASH",
  "name": "John Doe",
  "name_format": "{first} {last}",
  "picture": {
    "data": {
      "height": 1016,
      "is_silhouette": false,
      "url": "https://platform-lookaside.fbsbx.com/platform/profilepic/?asid=581595189176358&height=1200&width=1200&ext=NUMBER&hash=HASH",
      "width": 1016
    }
  }
}
```

