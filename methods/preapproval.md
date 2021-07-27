# /preapproval

{% api-method method="post" host="https://api.v1.payment-assist.co.uk" path="/preapproval" %}
{% api-method-summary %}
Obtain pre-approval
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to pre-check the eligibility of a customer. Pre-approval success simply means the customer has passed our internal checks, they will still need to have funds available to cover their deposit payment for the application to ultimately be successful.
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

{% api-method-parameter name="f\_name" type="string" required=true %}
Customer first name
{% endapi-method-parameter %}

{% api-method-parameter name="s\_name" type="string" required=true %}
Customer last name
{% endapi-method-parameter %}

{% api-method-parameter name="addr1" type="string" required=true %}
Customer address line 1
{% endapi-method-parameter %}

{% api-method-parameter name="postcode" type="string" required=true %}
Customer postal/zip code
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Request successfully processed
{% endapi-method-response-example-description %}

```javascript
{
    "status": "​ok​",
    "msg": null,
    "data": {
        "approved": ​<true|false>
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

{% hint style="danger" %}
**NOTE:** Where a customer has failed pre-approval, **DO​ NOT**​ modify details and reapply. The customer should be informed of the outcome and the `/begin` endpoint should not be called.
{% endhint %}



