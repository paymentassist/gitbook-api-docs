# /update

{% api-method method="post" host="https://api.v1.payment-assist.co.uk" path="/update" %}
{% api-method-summary %}
Update an existing application
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to update parameters within an existing application.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Your API key
{% endapi-method-parameter %}

{% api-method-parameter name="signature" type="string" required=true %}
Your request signature
{% endapi-method-parameter %}

{% api-method-parameter name="token" type="string" required=true %}
The application token \(received from /begin endpoint\)
{% endapi-method-parameter %}

{% api-method-parameter name="order\_id" type="string" required=false %}
Your new Order ID. Application must be in `completed` status.
{% endapi-method-parameter %}

{% api-method-parameter name="expiry" type="integer" required=false %}
Your new expiry time, in seconds from request time. Application must be in `pending` or `in progress` status.
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Application updated successfully
{% endapi-method-response-example-description %}

```javascript
{
    "status": "ok",
    "msg": null,
    "data": {
        "token": <TOKEN>,
        <YOUR_PARAM>: <YOUR VALUE>
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
You can immediately expire a pending application by passing 0 seconds as your expiry parameter.
{% endhint %}

