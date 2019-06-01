# Products

{% api-method method="get" host="https://api.broodt.nu" path="/products" %}
{% api-method-summary %}
Show all products
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
'Bearer' + \`access\_token\`
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
    "name": "Atque sapiente.",
    "description": "Dolor ex vero ducimus mollitia.",
    "img_url": "https:\/\/lorempixel.com\/640\/480\/?16859",
    "price": 2.12,
    "tags": [
      2,
      2
    ],
    "recommended_addons": [
      4,
      4
    ]
  },
  {
    "id": 2,
    "name": "Est ut iusto.",
    "description": "Voluptas cumque non incidunt.",
    "img_url": "https:\/\/lorempixel.com\/640\/480\/?64897",
    "price": 0.16,
    "tags": [
      3,
      4
    ],
    "recommended_addons": [
      0,
      20
    ]
  }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.broodt.nu" path="/products/{product\_id\'s}" %}
{% api-method-summary %}
Show specific product\(s\)
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="product\_id\'s" type="string" required=true %}
Multiple products can be selected by a comma separated list.  
\(e.g. \`/products/1,2\`\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
'Bearer ' + \`access\_token\`
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
    "name": "Atque sapiente.",
    "description": "Dolor ex vero ducimus mollitia.",
    "img_url": "https:\/\/lorempixel.com\/640\/480\/?16859",
    "price": 2.12,
    "tags": [
      2,
      2
    ],
    "recommended_addons": [
      4,
      4
    ]
  },
  {
    "id": 2,
    "name": "Est ut iusto.",
    "description": "Voluptas cumque non incidunt.",
    "img_url": "https:\/\/lorempixel.com\/640\/480\/?64897",
    "price": 0.16,
    "tags": [
      3,
      4
    ],
    "recommended_addons": [
      0,
      20
    ]
  },
  {
    "id": 3,
    "name": "Error facilis.",
    "description": "Sint et qui fugit minima.",
    "img_url": "https:\/\/lorempixel.com\/640\/480\/?72148",
    "price": 0.43,
    "tags": [
      1,
      4
    ],
    "recommended_addons": [
      10,
      5
    ]
  }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.broodt.nu" path="/products" %}
{% api-method-summary %}
Create Product
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
'Bearer' + \`access\_token\`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="recommended\_addons" type="array" required=false %}
array\|integer\|distinct - Product Recommended
{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="array" required=false %}
array\|integer\|distinct - Product Tags
{% endapi-method-parameter %}

{% api-method-parameter name="price" type="integer" required=true %}
between:0,100\|numeric - Product Price
{% endapi-method-parameter %}

{% api-method-parameter name="img\_url" type="string" required=false %}
max:255\|url - Product cover image
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=true %}
min:3\|max:1000 - Product Description
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
max:255\|alpha\_space\|unique - Product Name
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Product Created
{% endapi-method-response-example-description %}

```javascript
{
  "name": "Broodje Kip",
  "description": "Verse Zalm",
  "img_url": "https:\/\/loremflickr.com\/320\/240\/food",
  "price": 4.01,
  "tags": [
    1
  ],
  "recommended_addons": [
    1
  ],
  "id": 3
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
Incorrect or empty fields passed
{% endapi-method-response-example-description %}

```javascript
{
  "name": [
    "The name field is required."
  ],
  "description": [
    "The description field is required."
  ],
  "price": [
    "The price field is required."
  ]

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.broodt.nu" path="/products/{product\_id}" %}
{% api-method-summary %}
Update Product
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="product\_id" type="string" required=true %}
\(e.g. \`/products/1\`\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
'Bearer ' + \`access\_token\`
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

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

{% api-method method="delete" host="https://api.broodt.nu" path="/products/{product\_id}" %}
{% api-method-summary %}
Delete product
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="product\_id" type="string" required=true %}
\(e.g. \`/products/1\`\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
'Bearer ' + \`access\_token\`
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}
Product deleted
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

