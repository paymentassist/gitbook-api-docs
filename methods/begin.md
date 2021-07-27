# /begin

{% hint style="danger" %}
IMPORTANT: commencing **March 1st 2020**, the following _optional_  fields will become _required_ for this endpoint: `f_name`, `s_name`, `addr1` and `postcode`.
{% endhint %}

{% api-method method="post" host="https://api.v1.payment-assist.co.uk" path="/begin" %}
{% api-method-summary %}
Begin application
{% endapi-method-summary %}

{% api-method-description %}
This endpoint commences the application process. A successful request will return a `token` \(a 36-char UUID\) along with a continuation URL. You should redirect the customer to this URL so they can complete the rest of the signup process and record the `token` for later use. We'll send them back to either your success or failure URL, depending on the outcome.  
  
Before we redirect the customer back to the client site, we will append the success/failure URL with the following GET parameters:  
  
`token` - \(string\) the application token  
`status` - \(string\) success\|failed  
`signature` - \(string\) the authentication string \(see Authentication\).  
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

{% api-method-parameter name="failure\_url" type="string" required=false %}
URL redirect destination on failure
{% endapi-method-parameter %}

{% api-method-parameter name="success\_url" type="string" required=false %}
URL redirect destination on success
{% endapi-method-parameter %}

{% api-method-parameter name="order\_id" type="string" required=true %}
Your invoice/order ID - must be unique
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="integer" required=true %}
Invoice value in pence \(1000 = £10.00\)
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=true %}
Customer email address
{% endapi-method-parameter %}

{% api-method-parameter name="webhook\_url" type="string" required=false %}
Your webhook URL \(see Webhooks\)
{% endapi-method-parameter %}

{% api-method-parameter name="plan\_id" type="integer" required=false %}
The plan ID \(See Plan Types\). \* **Required where account has access to multiple plan types** \*
{% endapi-method-parameter %}

{% api-method-parameter name="plan\_length" type="string" required=false %}
The plan length \(see Plan Types\). _Note: This parameter is now deprecated and is available for v2 backwards-compatibility only_.
{% endapi-method-parameter %}

{% api-method-parameter name="reg\_no" type="string" required=false %}
Vehicle registration/license \(if applicable\)
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Description of service/goods
{% endapi-method-parameter %}

{% api-method-parameter name="expiry" type="integer" required=false %}
Application expiry in seconds \(default: 86400\)
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

{% api-method-parameter name="addr2" type="string" required=false %}
Customer address line 2
{% endapi-method-parameter %}

{% api-method-parameter name="addr3" type="string" required=false %}
Customer address line 3
{% endapi-method-parameter %}

{% api-method-parameter name="town" type="string" required=false %}
Customer town/city
{% endapi-method-parameter %}

{% api-method-parameter name="county" type="string" required=false %}
Customer county/state
{% endapi-method-parameter %}

{% api-method-parameter name="postcode" type="string" required=true %}
Customer postal/zip code
{% endapi-method-parameter %}

{% api-method-parameter name="telephone" type="string" required=false %}
Customer mobile telephone number
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Application successful
{% endapi-method-response-example-description %}

```javascript
{
    "status": "​ok​",
    "msg": null,
    "data": {
        "token": <TOKEN>​,
        "url": ​<URL>
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Offline Sessions** - where the customer is not in an active browser session, we support two further optional boolean parameters: `send_sms` and `send_email`. These will trigger a notification to be sent via email/SMS to the customer's device with a link to complete the remainder of the sign-up process.

{% hint style="info" %}
For possible error responses, see [Glossary: Status Codes](../glossary.md#status-codes)
{% endhint %}

