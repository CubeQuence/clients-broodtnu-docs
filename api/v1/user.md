# User

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
'Bearer ' + access\_token
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
  "name": "fooBar",
  "email": "fooBar@example.com",
  "created_at": "2019-04-26 18:15:31",
  "updated_at": "2019-04-26 18:15:31"
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
{% api-method-parameter name="Authorization" type="string" required=true %}
'Bearer ' + access\_token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=false %}
min:8 - User Password
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}
max:255\|unique - User Email
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
max:50\|alpha\_num - User Password
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "id": 1,
  "name": "fooBar",
  "email": "fooBar@example.com",
  "created_at": "2019-04-26 18:15:31",
  "updated_at": "2019-04-26 18:15:31"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.broodt.nu" path="/user" %}
{% api-method-summary %}
Delete Profile
{% endapi-method-summary %}

{% api-method-description %}
Delete the profile of the logged in user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Authorization" type="string" required=true %}
'Bearer ' + access\_token
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

