# Authentication / Authorization

{% api-method method="post" host="https://api.broodt.nu" path="/auth/register" %}
{% api-method-summary %}
Register Account
{% endapi-method-summary %}

{% api-method-description %}
Create a user account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="password" type="string" required=true %}
min:8 - User Password
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=true %}
max:255\|unique - User Email
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
max:50\|alpha\_num - User Name
{% endapi-method-parameter %}

{% api-method-parameter name="captcha\_response" type="string" required=true %}
The response of Google reCaptcha V2 Checkbox
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Account successfully created.
{% endapi-method-response-example-description %}

```javascript
{
  "name": "fooBar",
  "email": "fooBar@example.com",
  "updated_at": "2019-04-26 18:15:31",
  "created_at": "2019-04-26 18:15:31",
  "id": 1
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
No or invalid captcha\_respond provided
{% endapi-method-response-example-description %}

```javascript
{
  "error": "invalid captcha"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
Incorrect or empty fields passed
{% endapi-method-response-example-description %}

```javascript
{
  "captcha_response": [
    "The captcha response field is required."
  ],
  "name": [
    "The name field is required."
  ],
  "email": [
    "The email field is required."
  ],
  "password": [
    "The password field is required."
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.broodt.nu" path="/auth/login" %}
{% api-method-summary %}
Login
{% endapi-method-summary %}

{% api-method-description %}
Generate an 'access\_token' and 'refresh\_token'
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="email" type="string" required=true %}
max:255\|unique - User Email
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
min:8 - User Password
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Login successful
{% endapi-method-response-example-description %}

```javascript
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3Q6ODA4MCIsImF1ZCI6Imh0dHBzOlwvXC9icm9vZHQubnUiLCJzdWIiOjIsInN1Yl9pcCI6Ils6OjFdIiwiaWF0IjoxNTU2Mjk5MjIxLCJleHAiOjE1NTYzMDAxMjF9.YG8YcS4TxqOwOSPTaOtkFkKoaH4hjaFTwdE63cWexCKaKMdx9ewmTPCFcfDa4uSTJG9RixskFEwU0MjvBppyCg",
  "refresh_token": "wLVJkrwcT3YQHAjs2KKyY3f81PTssZuT"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Invalid credentials
{% endapi-method-response-example-description %}

```javascript
{
  "errors": {
    "email or password": [
      "is invalid"
    ]
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
Incorrect or empty fields passed
{% endapi-method-response-example-description %}

```javascript
{
  "email": [
    "The email field is required."
  ],
  "password": [
    "The password field is required."
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.broodt.nu" path="/auth/login" %}
{% api-method-summary %}
Logout
{% endapi-method-summary %}

{% api-method-description %}
Revoke the 'refresh\_token'
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="refresh\_token" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Refresh successful
{% endapi-method-response-example-description %}

```javascript
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3Q6ODA4MCIsImF1ZCI6Imh0dHBzOlwvXC9icm9vZHQubnUiLCJzdWIiOjIsInN1Yl9pcCI6Ils6OjFdIiwiaWF0IjoxNTU2Mjk5NTcwLCJleHAiOjE1NTYzMDA0NzB9.RG2iYZd1pEiMqWuPhJ833cG_VWn07P_0vDBp1ub0KM8NQS88_8OsCsn_Mm_nzs4eoxKJmf0HbIo21H4a_Qovrg",
  "refresh_token": "kDIWC3L7n053qsXiB7a7OifIz6FehwUu"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
Incorrect or empty fields passed
{% endapi-method-response-example-description %}

```javascript
{
  "refresh_token": [
    "The refresh token field is required."
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.broodt.nu" path="/auth/verify" %}
{% api-method-summary %}
Verify Email
{% endapi-method-summary %}

{% api-method-description %}
Activate your account
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="verify\_email\_token" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}
Account verification successful
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
Incorrect or empty fields passed
{% endapi-method-response-example-description %}

```javascript
{
  "verify_email_token": [
    "The selected verify email token is invalid."
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.broodt.nu" path="/auth/reset/request" %}
{% api-method-summary %}
Request Reset Password
{% endapi-method-summary %}

{% api-method-description %}
Request a password reset link
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="captcha\_response" type="string" required=true %}
The response of Google reCaptcha V2 Checkbox
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=true %}
max:255\|unique - Email
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}
Reset request sent
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
Incorrect or empty fields passed
{% endapi-method-response-example-description %}

```javascript
{
  "email": [
    "The selected email is invalid."
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.broodt.nu" path="/auth/request" %}
{% api-method-summary %}
Reset Password
{% endapi-method-summary %}

{% api-method-description %}
Reset the users password
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="password" type="string" required=true %}
min:8 - Password
{% endapi-method-parameter %}

{% api-method-parameter name="reset\_password\_token" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}
Password reset successful
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "reset_password_token": [
    "The selected reset password token is invalid."
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



