# General

{% api-method method="get" host="https://api.broodt.nu" path="/" %}
{% api-method-summary %}
Root
{% endapi-method-summary %}

{% api-method-description %}
Show the available endpoints
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "documentation_url": "https://docs.broodt.nu"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.broodt.nu" path="/meta" %}
{% api-method-summary %}
Meta
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
  "captcha_public_key": "6Lf2QaAUAAAAAO_gyyQadNMJHvvTI2X607eqDRmY",
  "jwt_public_key": "-----BEGIN PUBLIC KEY-----\nMFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBAL5YuQ9ibofjYCFzY4UCs21nhEJHOjtk\nEQaQqW5ajI4NNIvXxyyKfa8\/znLkl8dmvF5i5dX7Q2sDv1cV7xQj0tMCAwEAAQ==\n-----END PUBLIC KEY-----"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="head" host="https://api.broodt.nu" path="/foo/bar" %}
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
If no \`access\_token\` is provided.
{% endapi-method-response-example-description %}

```javascript
{
  "error": "Access_token not provided."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
If the \`access\_token\` is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "error": "Access_token has invalid signature."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
If the \`access\_token\` has expired.
{% endapi-method-response-example-description %}

```javascript
{
  "error": "Access_token has expired."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

