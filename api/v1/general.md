# General

{% api-method method="get" host="https://api.broodt.nu" path="/" %}
{% api-method-summary %}
Root
{% endapi-method-summary %}

{% api-method-description %}
Provide the front-end with required variables
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "time": "2019-06-13 18:54:18",
    "captcha_public_key": "6Lf2QaAUAAAAAO_gyyQadNMJHvvTI2X607eqDRmY",
    "jwt_public_key": "-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxYOZG/jbX3UcQLKRTqA/\n/gBQEhES1POCfzFromcZHdA6AOYl9OgmQdnQq3SNIMf/IZXTiQL6Z6GOVw98jke2\nOUxxoxOdQDl+mdlRpQtkZXW3urxlFfvXrwUJkuOI2UWbv3tf5eN9slNgMiLaKqhW\nLScqkjTjUH9vycaBb9PME7PNqzQWeTxiTa8tx5Yn3Vy1t1Lkg4EW4o4nEMczPfEC\ndDN65pMDfo1mMTJx6a6+4twcmj3Zsc+7NFZr29zBh84VAR/JILHS0hdxRXSlaZ4+\nmgjqegJuHVbKFVr7N7CikOLu6PSliruqt8qHE3uT2988Izt/DICUCC1hA/j0Ct7b\nvQIDAQAB\n-----END PUBLIC KEY-----"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="head" host="https://api.broodt.nu" path="/fooBar" %}
{% api-method-summary %}
Protected Request
{% endapi-method-summary %}

{% api-method-description %}
This is the default for an authenticated request.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer fooBar
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If no "access\_token" was provided.
{% endapi-method-response-example-description %}

```javascript
{
  "error": "access_token not provided"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
If the "access\_token" is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "error": "access_token invalid"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=402 %}
{% api-method-response-example-description %}
If the "access\_token" claim "sub\_ip" doesn't match the IP of the request origin.
{% endapi-method-response-example-description %}

```javascript
{
  "error": "access_token invalid"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
If the "access\_token" has expired.
{% endapi-method-response-example-description %}

```javascript
{
  "error": "access_token has expired"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

