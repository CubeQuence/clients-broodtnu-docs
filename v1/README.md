# API v1

This describes the resources that make up the official LunchBox REST API. If you have any problems or requests, please contact [LunchBox Support](https://lunchbox.nl/contact).

### Overview

* Schema
* Authentication
* Parameters
* Root endpoint
* Client Errors
* HTTP redirects
* HTTP verbs
* CORS

### Schema

All API access is over HTTPS, and accessed from `https://api.lunchbox.nl`. All data is sent and received as JSON.

```http
curl -i https://api.lunchbox.nl/ping
HTTP/1.1 200 OK
Server: nginx
Date: Fri, 12 Oct 2012 23:33:14 GMT
Content-Type: application/json; charset=utf-8
Connection: keep-alive
Status: 200 OK
ETag: "a00049ba79152d03380c34652f2cb612"
Content-Length: 5
Cache-Control: max-age=0, private, must-revalidate
X-Content-Type-Options: nosniff
```

Blank fields are included as `null` instead of being omitted.

All timestamps return in ISO 8601 format:

```text
YYYY-MM-DDTHH:MM:SSZ
```

We use the `CEST (GMT+1)` time zone.

### Authentication

To authenticate trough the LunchBox  ****API, we use `Bearer` tokens. These can be used in the following way.

#### Bearer token \(sent in a header\)

```bash
curl -H "Authorization: token BEARER-TOKEN" https://api.lunchbox.nl
```

#### Failed login

Authenticating with invalid credentials will return `401 Unauthorized`:

```bash
curl -H "Authorization: token fooBar" https://api.lunchbox.nl/products
HTTP/1.1 401 Unauthorized
{
  "message": "Bad credentials",
  "documentation_url": "https://developer.github.com/v3"
}
```

### Parameters

Many API methods take optional parameters. For `GET` requests, any parameters not specified as a segment in the path can be passed as an HTTP query string parameter:

```bash
curl "https://api.lunchbox.nl/products/12?foo=Bar"
```

In this example, the '12' value is provided for the `:productId` parameter in the path while `:foo` is passed in the query string.

For `POST`, `PATCH`, `PUT`, and `DELETE` requests, parameters not included in the URL should be encoded as JSON with a Content-Type of `application/json`:

```bash
curl -d '{"items":["12"]}' https://api.lunchbox.nl/cart
```

### Root endpoint

You can issue a `GET` request to the root endpoint to get all the endpoint categories that the  API supports:

```bash
curl https://api.lunchbox.nl
```

### Client errors

There are three possible types of client errors on API calls that receive request bodies:

1. Sending invalid JSON will result in a `400 Bad Request` response.

   ```http
   HTTP/1.1 400 Bad Request
   Content-Length: 35

   {"message":"Problems parsing JSON"}
   ```

2. Sending the wrong type of JSON values will result in a `400 Bad Request` response.

   ```http
   HTTP/1.1 400 Bad Request
   Content-Length: 40

   {"message":"Body should be a JSON object"}
   ```

3. Sending invalid fields will result in a `422 Unprocessable Entity` response.

   ```http
   HTTP/1.1 422 Unprocessable Entity
   Content-Length: 149

   {
     "message": "Validation Failed",
     "errors": [
       {
         "resource": "Issue",
         "field": "title",
         "code": "missing_field"
       }
     ]
   }
   ```

All error objects have resource and field properties so that your client can tell what the problem is. There's also an error code to let you know what is wrong with the field. These are the possible validation error codes:

| Error Name | Description |
| :--- | :--- |
| `missing` | This means a resource does not exist. |
| `missing_field` | This means a required field on a resource has not been set. |
| `invalid` | This means the formatting of a field is invalid. The documentation for that resource should be able to give you more specific information. |
| `already_exists` | This means another resource has the same value as this field. This can happen in resources that must have some unique key \(such as Label names\). |

Resources may also send custom validation errors \(where `code` is `custom`\). Custom errors will always have a `message` field describing the error, and most errors will also include a `documentation_url` field pointing to some content that might help you resolve the error.

### HTTP redirects

The API uses HTTP redirection where appropriate. Clients should assume that any request may result in a redirection. Receiving an HTTP redirection is _**not**_ an error and clients should follow that redirect. Redirect responses will have a `Location` header field which contains the URI of the resource to which the client should repeat the requests.

| Status Code | Description |
| :--- | :--- |
| `301` | Permanent redirection. The URI you used to make the request has been superseded by the one specified in the `Location` header field. This and all future requests to this resource should be directed to the new URI. |
| `302`, `307` | Temporary redirection. The request should be repeated verbatim to the URI specified in the `Location` header field but clients should continue to use the original URI for future requests. |

Other redirection status codes may be used in accordance with the HTTP 1.1 spec.

### HTTP verbs

Where possible, we strive to use the appropriate HTTP verbs for each action.

| Verb | Description |
| :--- | :--- |
| `HEAD` | Can be issued against any resource to get just the HTTP header info. |
| `GET` | Used for retrieving resources. |
| `POST` | Used for creating resources. |
| `PATCH` | Used for updating resources with partial JSON data. For instance, an Issue resource has `title` and `body` attributes. A PATCH request may accept one or more of the attributes to update the resource. PATCH is a relatively new and uncommon HTTP verb, so resource endpoints also accept `POST` requests. |
| `DELETE` | Used for deleting resources. |

### CORS

The API supports Cross Origin Resource Sharing \(CORS\) for AJAX requests from any origin. You can read the [CORS W3C Recommendation](http://www.w3.org/TR/cors/), or [this intro](http://code.google.com/p/html5security/wiki/CrossOriginRequestSecurity) from the HTML 5 Security Guide.

Here's a sample request sent from a browser hitting `http://example.com`:

```text
curl -i https://api.lunchbox.nl -H "Origin: http://example.com"
HTTP/1.1 302 Found
Access-Control-Allow-Origin: *
Access-Control-Expose-Headers: ETag, Link, X-GitHub-OTP, X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset, X-OAuth-Scopes, X-Accepted-OAuth-Scopes, X-Poll-Interval
```

This is what the CORS preflight request looks like:

```text
curl -i https://api.lunchbox.nl -H "Origin: http://example.com" -X OPTIONS
HTTP/1.1 204 No Content
Access-Control-Allow-Origin: *
Access-Control-Allow-Headers: Authorization, Content-Type, If-Match, If-Modified-Since, If-None-Match, If-Unmodified-Since, X-GitHub-OTP, X-Requested-With
Access-Control-Allow-Methods: GET, POST, PATCH, PUT, DELETE
Access-Control-Expose-Headers: ETag, Link, X-GitHub-OTP, X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset, X-OAuth-Scopes, X-Accepted-OAuth-Scopes, X-Poll-Interval
Access-Control-Max-Age: 86400
```





