# /status

{% api-method method="get" host="https://api.v1.payment-assist.co.uk" path="/status" %}
{% api-method-summary %}
Get application status
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to check the status of an existing application. You should pass the `token` received from the /begin endpoint.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Your API key
{% endapi-method-parameter %}

{% api-method-parameter name="signature" type="string" required=true %}
Your request signature
{% endapi-method-parameter %}

{% api-method-parameter name="token" type="string" required=true %}
The token \(UUID\) returned from /begin endpoint.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Application status successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "status": "ok",
    "msg": null,
    "data": {
        "token": <TOKEN>,
        "status": <pending|in progress|completed|failed|expired>,
        "pa_ref": <PAYMENT ASSIST REFERENCE>,
        "requires_invoice": <true|false>,
        "has_invoice": <true|false>,
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
If you plan to store the `pa_ref` \(customer-facing transaction/loan reference\) then please note this is a variable length string. We recommend allowing at least 24 characters within your database field for future expansion.
{% endhint %}

{% hint style="info" %}
For possible error responses, see [Glossary: Status Codes](https://api-docs.payment-assist.co.uk/glossary#status-codes)​
{% endhint %}

