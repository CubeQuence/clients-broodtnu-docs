# Endpoints

{% api-method method="get" host="https://api.broodt.nu" path="/" %}
{% api-method-summary %}
Root
{% endapi-method-summary %}

{% api-method-description %}
Provide the documentation URL.
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

{% api-method method="get" host="https://api.broodt.nu" path="/ping" %}
{% api-method-summary %}
Ping
{% endapi-method-summary %}

{% api-method-description %}
Ping the API to check it is alive. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "time": "2019-04-25 21:13:19",
  "message": "pong"
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
  "captcha_key": "6Lf2QaAUAAAAAO_gyyQadNMJHvvTI2X607eqDRmY"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### User Endpoints

{% api-method method="get" host="https://api.broodt.nu" path="/user" %}
{% api-method-summary %}
View Profile
{% endapi-method-summary %}

{% api-method-description %}
Get the profile information of the logged in user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
Bearer fooBar
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "id": 1,
  "name": "Lavada Leuschke",
  "email": "jessika27@example.org",
  "created_at": "2019-04-25 13:45:58",
  "updated_at": "2019-04-25 13:45:58"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.broodt.nu" path="/user" %}
{% api-method-summary %}
Update Profile
{% endapi-method-summary %}

{% api-method-description %}
Update the profile information of the logged in user.           
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
Bearer fooBar
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

