# /invoice

{% api-method method="post" host="https://api.v1.payment-assist.co.uk" path="/invoice" %}
{% api-method-summary %}
Upload invoice to completed application
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to upload an invoice corresponding to a previously completed application. Applications that are not yet completed will return HTTP 404.
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
The token returned from the /begin endpoint
{% endapi-method-parameter %}

{% api-method-parameter name="filetype" type="string" required=true %}
The file type \(accepted: pdf, html, txt, doc, xls\)
{% endapi-method-parameter %}

{% api-method-parameter name="filedata" type="string" required=true %}
The base64 encoded file
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Request processed without higher level error
{% endapi-method-response-example-description %}

```
{
    "status": "ok",
    "msg": null,
    "data": {
        "token": <TOKEN>,
        "upload_status": <success|failed>,
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
For possible error responses, see [Glossary: Status Codes](https://api-docs.payment-assist.co.uk/glossary#status-codes)​
{% endhint %}

{% hint style="danger" %}
It is imperative that the `filetype` matches the uploaded `filedata`as we perform no subsequent validation. If our support staff can not open the document then this may delay funds being released to you.
{% endhint %}

