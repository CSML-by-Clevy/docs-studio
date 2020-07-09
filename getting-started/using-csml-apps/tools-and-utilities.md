# Tools and utilities

CSML Studio also comes with a number of tools helping you perform day-to-day tasks such as generating QR codes, manipulating dates and times, or scheduling conversation events in the future.

## Scheduler

The scheduler is a good way to plan events to happen at a later time. There are 2 types of scheduled events:

* **webhook**, when you want a certain URL to be notified at a later time
* **broadcast**, when you want to create a new conversation with the user later

To install the CSML scheduler, go to Functions &gt; Apps directory &gt; Scheduler, and click **Install**.

### Example scenario

Imagine an e-commerce chatbot where the user leaves the conversation before checkout, but has items in their cart. In that situation, you might want to send them a reminder a few hours later that they have items in their shopping cart and they might not want to loose them. Heck, why not throw a discount code with it?

![](../../.gitbook/assets/image%20%2814%29.png)

Of course, if the user did go through with their order, you want to cancel this reminder, because it does not make sense to keep it.

Here is what this scenario would look like in CSML:

```cpp
start:
  say "Thanks for shopping with us!"
  goto shop

shop:
  // cancel any existing reminder
  if (sched) do Fn("utils/scheduler", action="cancel", schedule_id="cart_reminder")
  // ... get the user to buy some items
  say Question("Select an item to buy", buttons=[Button("Mascara"), Button("Perfume")])
  hold
  // then add a new reminder with ID "cart_reminder"
  remember sched = Fn("utils/scheduler", delay="1 hr", flow_id="remind_cart", schedule_id="cart_reminder")
  
  say "You have {{cart.count}} items in your shopping cart, for a total of ${{cart.total}}"
  say Question(
    "What do you want to do?",
    button_type="quick_reply",
    buttons=[
      Button("Continue shopping 🛍") as shop,
      Button("Go to checkout 💵") as checkout,
    ]
  )
  hold
  // the user wants to continue shopping, let them do that
  if (event match shop) {
    goto shop
  }
  goto checkout

checkout:
  // execute the order from the user
  say "Go to stripe payment page to pay here: XXX"
  hold
  // no need to remind the user anymore, they already paid
  if (sched) do Fn("utils/scheduler", action="cancel", schedule_id="cart_reminder")
```

Read below for more information on how to create scheduled items.

### Scheduling a webhook call

You can schedule a POST request to a webhook using something like the following:

```cpp
do sched = Fn(
    "utils/scheduler",
    action = "webhook",
    url = "https://my.url.com/whatever",
    body = { "some": ["custom", "data"] },
    delay = "10 min",
)
say "Created scheduled event with ID {{sched.result.schedule_id}}"
```

This means that in about 10 minutes, the endpoint [`https://my.url.com/whatever`](https://my.url.com/whatever) will receive a POST request containing the body `{ "some": ["custom", "data"] }`.

### Scheduling a broadcast

{% hint style="warning" %}
Channels that do not support the broadcast feature will also not support scheduled broadcasts.  
Hence, **scheduled broadcasts are currently only supported on MS Teams, Messenger and Workchat** channels.
{% endhint %}

You can schedule a broadcast to the current user with something like the following:

```cpp
do sched = Fn(
    "utils/scheduler",
    action = "broadcast",
    flow_id = "nameOfFlow",
    metadata = { "some": ["custom", "data"] },
    delay = "3 hrs",
)
say "Created scheduled event with ID {{sched.result.schedule_id}}"
```

This means that in about 30 minutes, the user will receive a new conversation initiated by the chatbot from flow `nameOfFlow` with the given additional metadata.

### Cancelling a schedule

It is possible to cancel a scheduled event by calling the following function, where schedule\_id is the ID of the schedule you want to cancel:

```cpp
Fn(
    "utils/scheduler",
    action = "cancel",
    schedule_id = schedule_id
)
```

### Example response

```javascript
{
    "success": true,
    "result": {
        "action": "broadcast",
        "flow_id": "remind_cart",
        "schedule_id": "some-id",
        "scheduled_at": "2020-07-09T20:02:57.255Z",
        "scheduled_at_unix": 1594324977
    }
}
```

### Caveats

* Events will be executed within 1 minute after your event is scheduled.
* If you do not set your own `schedule_id`, a random `schedule_id` will be generated.
* You can use the `delay` \(with either human-readable times, such as `"1 hr"`, `"5 min"` or a number of milliseconds\) or the `schedule_time` \(an ISO-formatted time string OR unix timestamp integer describing when to schedule the event. Example: `1592843603`, `"2020-06-22T16:33:44.377Z"`\) parameters to set the time for your event.
* You can schedule events at any point within the next 1 minute - 1 month.
* Failed events will not be retried. We guarantee that the event will go off, but make sure that your endpoint is available at the time of the scheduled webhook, or that the channel supports scheduled broadcasts.

### 

