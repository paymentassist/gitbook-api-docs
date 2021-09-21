# /account

{% api-method method="get" host="https://api.v1.payment-assist.co.uk" path="/account" %}
{% api-method-summary %}
Get account configuration details
{% endapi-method-summary %}

{% api-method-description %}
This endpoint returns some account level information, including a breakdown of available Plan Types.
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
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Request successfully processed. Example response below:
{% endapi-method-response-example-description %}

```javascript
{
    "status": "ok",
    "msg": null,
    "data": {
        "legal_name": "Test Dealer",
        "display_name": "Test Dealer",
        "plans": [
            {
                "plan_id": 6,
                "name": "3-Payment",
                "instalments": 3,
                "deposit": true,
                "apr": 0,
                "frequency": "monthly",
                "min_amount": null,
                "max_amount": 500000,
                "commission_rate": "8.50",
                "commission_fixed_fee": null
            },{
                "plan_id": 1,
                "name": "4-Payment",
                "instalments": 4,
                "deposit": true,
                "apr": 0,
                "frequency": "monthly",
                "min_amount": null,
                "max_amount": 300000,
                "commission_rate": "8.50"
                "commission_fixed_fee": null
            }
        ]
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
For possible error responses, see [Glossary: Status Codes](../glossary.md#status-codes).
{% endhint %}

The `plans` property of the response contains an array of plan objects, each with the following properties:

| Name | Description |
| :--- | :--- |
| `plan_id` | This is the internal PA identifier for the plan type, this should be used in calls to the [/begin](begin.md) and [/plan](plan.md) endpoints |
| `name` | The display name of the plan |
| `instalments` | The total number of instalments for the plan |
| `deposit` | Whether the plan requires a deposit \(first payment taken immediately\) |
| `apr` | The APR % of the plan \(generally, this will be 0 depicting an interest-free plan\) |
| `frequency` | The instalment frequency |
| `min_amount` | The minimum value allowed for the plan \(in pence\) or `null` for no minimum |
| `max_amount` | The maximum value allowed for the plan \(in pence\) or `null` for no maximum |
| `commission_rate` | The Payment Assist commission rate on the plan \(%\) |
| `commission_fixed_fee` | The Payment Assist commission fixed fee on the plan \(in pence\) or `null` for no fixed fee |

{% hint style="info" %}
It's possible for plans to have both a `commission_rate` and a `commission_fixed_fee`. For example, £5.00 fixed fee + 2.5% on a £500 plan would mean a total commission fee of £17.50.
{% endhint %}
