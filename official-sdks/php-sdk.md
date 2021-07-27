---
description: Official PHP SDK for the Payment Assist Partner API
---

# PHP SDK

### Github

[https://github.com/paymentassist/paymentassist-php](https://github.com/paymentassist/paymentassist-php)

### Dependencies

* PHP &gt;= 5.3 \(PHP7 recommended\)
* PHP JSON extension
* PHP cURL extension

### Installation

Install with Composer:

`composer require paymentassist/paymentassist-php`

Install via Git:

`git clone git@github.com:paymentassist/paymentassist-php.git`

### Usage

```php
$params = [
    'f_name' => 'Jane',
    's_name' => 'Bloggs',
    ...
];

$credentials = array('api_key'=>'YOUR-KEY', 'secret'=>'YOUR-SECRET');
$pa = new \PaymentAssist\ApiClient($credentials);
$result = $pa->request('/begin', 'POST', $params);
print_r($result);
```

