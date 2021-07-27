# /plan

{% api-method method="post" host="https://api.v1.payment-assist.co.uk" path="/plan" %}
{% api-method-summary %}
Get a plan breakdown
{% endapi-method-summary %}

{% api-method-description %}
This endpoint accepts a transaction amount and optional plan ID + term length. It returns a full plan schedule including payment amounts and dates.
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

{% api-method-parameter name="amount" type="integer" required=true %}
Invoice value in pence \(1000 = £10.00\)
{% endapi-method-parameter %}

{% api-method-parameter name="plan\_id" type="integer" required=false %}
The plan ID, if empty then your account default is used.
{% endapi-method-parameter %}

{% api-method-parameter name="plan\_length" type="integer" required=false %}
The length of the payment plan \(must correspond to those available on plan\_id\).
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Request accepted
{% endapi-method-response-example-description %}

```javascript
{  
   "status": "ok",
   "msg": null,
   "data": {  
      "plan": "4-Payment", /* the plan name */
      "amount": 50000,
      "interest": 0, /* the total interest (in pence) */
      "repayable": 50000, /* the total amount repayable (in pence) */
      "schedule": [  
         {  
            "date": "2019-03-12",
            "amount": 12500
         },
         {  
            "date": "2019-04-12",
            "amount": 12500
         },
         {  
            "date": "2019-05-12",
            "amount": 12500
         },
         {  
            "date": "2019-06-12",
            "amount": 12500
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
For possible error responses, see [Glossary: Status Codes](../glossary.md#status-codes)
{% endhint %}

