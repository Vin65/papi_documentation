# Products

## Get a list Products

> To get a list of products, use this code:

```ruby
require 'net/http'
require 'rubygems'
require 'json'

uri = URI('http://marketservices.vin65.com/products')
req = Net::HTTP::Post.new(uri, initheader = {'Content-Type' =>'application/json', 'Authorization' => "Bearer [auth_token]"})
http = Net::HTTP.new(uri.host, 80)
resp = http.request(req)
products = JSON.parse(resp.body)['products']
```

```shell
curl -X "GET" "http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/products" \
	-H "Authorization: Bearer [auth_token]" \
	-H "Content-Type: application/json" \
	-d "{}"
```


> Example Response Headers

```headers
HTTP/1.1 200 OK
Cache-Control: max-age=0, private, must-revalidate
Content-Type: application/json; charset=utf-8
Date: Sat, 23 Jan 2016 20:30:18 GMT
ETag: W/"f2f61edcecf302459979f9deb67b38e4"
Server: nginx/1.4.6 (Ubuntu)
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
X-Request-Id: f7e972a7-9966-4e1f-85b7-e9e2beb3522c
X-Runtime: 0.094200
X-XSS-Protection: 1; mode=block
transfer-encoding: chunked
Connection: Close
```

> Example Response Body

```json
{
	"products": [{
		"id": 1,
		"alcohol_percent": 14.1,
		"brand": "Test Brand",
		"description": "test description",
		"name": "Test Product",
		"price": 29.99,
		"product_type": "wine",
		"product_uuid": "892dc682-925b-4c4c-b07a-5a46dede9aaf",
		"region": "California",
		"sku": "ABC123",
		"status": "available",
		"teaser": "test teaser",
		"varietal": "merlot",
		"vintage": 2015,
		"volume_in_liters": 0.75,
		"weight_in_kg": 10.0,
		"acid": null,
		"appellation": null,
		"bottling_date": null,
		"fermentation": null,
		"harvest_date": null,
		"ph": null,
		"production_amount": null,
		"residual_sugar": null,
		"sugar": null,
		"tannin": null,
		"wine_type": null,
		"unit_description": null,
		"vineyard_designation": null,
		"company": {
			"id": 2,
			"name": "Pinewines Winery",
			"company_type": "winery",
			"website_uuid": "66272648-1E0B-4E34-F09B-81477A31B25F"
		},
		"images": [],
		"notes": [],
		"ratings": []
	}]
}
```

Vin65 Market Services uses a temporary authorization token. You your email/password credentials to Authenticate yourself and obtain a new authorization token and then you can optionally cache the token until it expires.

All requests (other that the authenticate request) will require an Authorization header that uses an active Authorization token.

### HTTP Request

`GET http://marketservices.vin65.com/products/products`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
name      | false    | Name of Product
sku       | false    | SKU of Product

<aside class="success">
Remember — all requests must contain an Authorization Token in the headers.
</aside>

### Example Request URL
`http://marketservices.vin65.com/products/products?sku=ABC123`

### Errors
Code | Message               | Description
---- | --------------------- | -----------
401  | Unauthorized          | Authentication failed
404  | Not Found             | Not Found
429  | Too Many Requests     | Too many requests from this IP. Please wait and try again later
500  | Internal Server Error | Internal Server Error


## Get a Specific Product

> To get a specific product, use this code:

```ruby
require 'net/http'
require 'rubygems'
require 'json'

uri = URI('http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/products/1')
req = Net::HTTP::Post.new(uri, initheader = {'Content-Type' =>'application/json', 'Authorization' => "Bearer [auth_token]"})
http = Net::HTTP.new(uri.host, 80)
resp = http.request(req)
product = JSON.parse(resp.body)['product']
```

```shell
curl -X "GET" "http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/products/1" \
	-H "Authorization: Bearer [auth_token]" \
	-H "Content-Type: application/json" \
	-d "{}"
```

> Example Response Body

```json
{
	"product": {
		"id": 1,
		"alcohol_percent": 14.1,
		"brand": "Test Brand",
		"description": "test description",
		"name": "Test Product",
		"price": 29.99,
		"product_type": "wine",
		"product_uuid": "892dc682-925b-4c4c-b07a-5a46dede9aaf",
		"region": "California",
		"sku": "ABC123",
		"status": "available",
		"teaser": "test teaser",
		"varietal": "merlot",
		"vintage": 2015,
		"volume_in_liters": 0.75,
		"weight_in_kg": 10.0,
		"acid": null,
		"appellation": null,
		"bottling_date": null,
		"fermentation": null,
		"harvest_date": null,
		"ph": null,
		"production_amount": null,
		"residual_sugar": null,
		"sugar": null,
		"tannin": null,
		"wine_type": null,
		"unit_description": null,
		"vineyard_designation": null,
		"company": {
			"id": 2,
			"name": "Pinewines Winery",
			"company_type": "winery",
			"website_uuid": "66272648-1E0B-4E34-F09B-81477A31B25F"
		},
		"images": [],
		"notes": [],
		"ratings": []
	}
}
```

This endpoint retrieves a specific product.

### HTTP Request

`GET http://marketservices.vin65.com/products/{id}`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
id        | true     | id of product

<aside class="success">
Remember — all requests must contain an Authorization Token in the headers.
</aside>
