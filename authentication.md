# Authentication

Bi-directional request/response authentication occurs by generating a keyed-hash message authentication code \(HMAC-SHA256\).

A signature is created by using a sorted string of every parameter in the request \(apart from the `api_key​` and​ `signature​` parameters\) with the following format “**​\[PARAMETER\]​=\[value\]​&**” \(parameter key should be upper-cased and value should be used as supplied\).

After it's properly formatted, ensure the full string is UTF-8 encoded and then create a HMAC-SHA256 signature utilising your Payment Assist secret key and output to lowercase hexits.

When the customer is redirected back to your failure/success URL, we will append relevant parameters to the URL and also include a signature created with your secret key. You should generate the signature of the request client-side and compare our signature to your generated one before considering the request legitimate.

{% hint style="warning" %}
Note: when using GET parameters in your callback URL, these **should be removed** prior to generating the signature for authentication purposes. Signatures are generated on our side using only the parameters we append.
{% endhint %}

### PHP Example:

```php
    /**
     * @param array $params - key/value pairs of request payload
     * @param string $secret - your API secret
     * @return string
     */
    function generateSignature($params, $secret) {
        ksort($params);
        $str = '';
        foreach($params as $k=>$v) {
          $k = strtoupper($k);
          if ($k !== 'SIGNATURE' && $k !== 'API_KEY') {
            $str .= $k . '=' . $v . '&';
          }
        }
        $signature = hash_hmac('sha256', $str, $secret, false);
        return $signature;
    }
```

{% hint style="info" %}
Note: each dealer/branch will require it's own API key and secret. If you're integrating a multi-tenant system \(such as a dealer management tool\) then you will need to store individual credentials for each of your local users.
{% endhint %}

