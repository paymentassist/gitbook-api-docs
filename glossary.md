# Glossary

### Conventions

* **Client** - Client application.
* **Status code**​ - HTTP status code of response.
* All the possible success responses are listed under the ‘Response’ tab for each method. Only one of them is issued per request.
* All POST requests should be either application/json or application/x-www-form-urlencoded format. Always ensure the correct **Content-Type** header is sent.
* All responses are in JSON format.
* All request parameters marked as **required** are mandatory.
* The `string` type for all ​ request ​ parameters have a maximum length of 255 characters unless otherwise stated.
* Submitted text strings should always be UTF-8 encoded.
* You should **​ always**​ URL encode any parameter values sent via the GET method.

### Status Codes

All status codes are standard HTTP status codes. Those listed below are used in this API:

`2xx` - Success of some kind

`4xx` - Error occurred on client's part

`5xx` - Error occurred on server's part

| **Status Code** | **Description** |
| :--- | :--- |
| 200 | OK |
| 400 | Bad Request |
| 401 | Authentication Failure |
| 403 | Forbidden |
| 404 | Resource Not Found |
| 405 | Method Not Allowed |
| 500 | Internal Server Error |
| 503 | Service Unavailable |

{% hint style="info" %}
Along with a non 2xx HTTP status code, all errors will return a JSON body, as below.
{% endhint %}

```javascript
{
    "status": "error",
    "msg": <HUMAN_READABLE_ERROR_MESSAGE>,
    "data": <RELATED_DATA_IF_APPLICABLE>
}
```

