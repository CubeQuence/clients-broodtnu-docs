# Endpoints

### +General Endpoints

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

### Auth Endpoints

{% api-method method="post" host="https://api.broodt.nu" path="/auth/register" %}
{% api-method-summary %}
Register
{% endapi-method-summary %}

{% api-method-description %}
Create a user account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="captcha\_response" type="string" required=true %}
The response of the recaptcha checkbox
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
max:50\|alpha\_num
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=true %}
max:255\|unique
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
min:8
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

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
No or invalid captcha is provided
{% endapi-method-response-example-description %}

```javascript
{
  "error": "invalid captcha"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
Not all required fields are passed
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
Login to your account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="email" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

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
Invalid credentials are passed
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
Not all required fields are passed
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

{% api-method method="post" host="https://api.broodt.nu" path="/auth/logout" %}
{% api-method-summary %}
Logout
{% endapi-method-summary %}

{% api-method-description %}
Revoke the \`refresh\_token\`.
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

{% endapi-method-response-example-description %}

```javascript
{
  "success": true
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
Not all required fields are passed
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

{% api-method method="post" host="https://api.broodt.nu" path="/auth/refresh" %}
{% api-method-summary %}
Refresh
{% endapi-method-summary %}

{% api-method-description %}
Refresh \`access\_token\` and get a new \`refresh\_token\`.
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
Not all required fields are passed
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

### User Endpoints

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

{% api-method method="delete" host="https://api.broodt.nu" path="/user" %}
{% api-method-summary %}
Delete Profile
{% endapi-method-summary %}

{% api-method-description %}
Delete the profile of the logged in user.
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
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

