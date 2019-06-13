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
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.broodt.nu" path="/auth/sessions" %}
{% api-method-summary %}
List Sessions
{% endapi-method-summary %}

{% api-method-description %}
List user sessions
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
'Bearer ' + access\_token
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
  {
    "id": "928aee20-8e06-11e9-9218-c789fc71b3f6",
    "user_ip": "127.0.0.1",
    "user_agent": "insomnia/6.5.4",
    "refresh_token_expires": "2019-06-13 19:25:49",
    "created_at": "2019-06-13 19:10:49"
  },
  {
    "id": "93148ac0-8e06-11e9-86c4-dd9e86aebd5a",
    "user_ip": "127.0.0.1",
    "user_agent": "insomnia/6.5.4",
    "refresh_token_expires": "2019-06-13 19:25:50",
    "created_at": "2019-06-13 19:10:50"
  },
  {
    "id": "95ebdb80-8e06-11e9-8c27-418ff0d42235",
    "user_ip": "127.0.0.1",
    "user_agent": "insomnia/6.5.4",
    "refresh_token_expires": "2019-06-13 19:25:54",
    "created_at": "2019-06-13 19:10:54"
  }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.broodt.nu" path="/auth/sessions" %}
{% api-method-summary %}
Revoke Session
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
'Bearer ' + access\_token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="session\_uuid" type="string" required=true %}
The id of the session to revoke
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Session not found
{% endapi-method-response-example-description %}

```javascript
{
  "message": "not found"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

