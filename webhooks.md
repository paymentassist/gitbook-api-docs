---
description: Receive event notifications via webhooks.
---

# Webhooks

{% hint style="danger" %}
**This feature is currently in preview mode and available on demo/test only. Preview features are subject to breaking changes until they reach GA.**
{% endhint %}

Webhooks allow your application to listen for events within your Payment Assist merchant account and trigger reaction code accordingly; such as updating your internal order record or sending notifications.

You can configure your callback URL on a per request basis by passing a `webhook_url`  parameter within your call to the [/begin](methods/begin.md) endpoint. Your `webhook_url` must return an **HTTP 200** response to avoid unnecessary retries.

{% hint style="info" %}
We recommend that you do not perform any heavy processing within the callback request/response cycle itself. Instead, drop the payload into a queue and execute any related business logic via an external worker.
{% endhint %}

### Event Properties

| param | description |
| :--- | :--- |
| `event_name` | The event name \(in dot notation\). |
| `event_data` | Any specific data related to the event. |
| `event_time` | The original date/time of the event in `Y-m-d H:i:s T` format. |
| `signature` | The [authentication signature](authentication.md) of the request, generated using your account credentials. |

### Examples

You will receive an event notification as a JSON POST when the application changes to a finite state \(either `expired`, `failed` or `completed`\).

Example webhook payload:

```javascript
{
    "event_name": "application.failed",
    "event_data": {
        "token": "b1e45648-f369-11ea-8ed1-2cfda158243b"
    },
    "event_time": "2020-09-10 14:31:05 UTC",
    "signature": "..."
}
```

The signature is computed using your `api_key` and `secret` in the same way you generate signatures for inbound requests. You should always verify the payload before any further processing takes place within your application. See [Authentication](authentication.md).

{% hint style="warning" %}
It's best practice to never rely solely on webhooks for tracking application status. We will retry up to 3 times before giving up but network issues or application errors could result in failed requests. You should always poll the [/status](methods/status.md) endpoint periodically if you have not received an expected callback \(we would recommend every 5-10 minutes\).
{% endhint %}

