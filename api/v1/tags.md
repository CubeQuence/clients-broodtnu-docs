# Tags

{% api-method method="get" host="https://api.broodt.nu" path="/tags" %}
{% api-method-summary %}
Show all tags
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
  {
    "id": 1,
    "name": "Vegetarisch",
    "color": "green"
  },
  {
    "id": 2,
    "name": "Vis",
    "color": "blue"
  },
  {
    "id": 3,
    "name": "Kip",
    "color": "grey"
  },
  {
    "id": 4,
    "name": "Varken",
    "color": "pink"
  },
  {
    "id": 5,
    "name": "Koe",
    "color": "brown"
  }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.broodt.nu" path="/tags/{tag\_id\'s}" %}
{% api-method-summary %}
Show specific tag\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Show specific tag\(s\). Multiple can be selected by a comma separated list.
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

```javascript
[
  {
    "id": 1,
    "name": "Vegetarisch",
    "color": "green"
  },
  {
    "id": 2,
    "name": "Vis",
    "color": "blue"
  }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.broodt.nu" path="/tags/{tag\_id\'s}/products" %}
{% api-method-summary %}
Show all products with tag\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Show all products containing specified tag\(s\).
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
    "id": 4,
    "name": "Modi rerum.",
    "description": "Saepe eos aut sunt.",
    "img_url": "https:\/\/lorempixel.com\/640\/480\/?83780",
    "price": 2.5,
    "tags": [
      1,
      4
    ],
    "recommended_addons": [
      24,
      21
    ]
  }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

