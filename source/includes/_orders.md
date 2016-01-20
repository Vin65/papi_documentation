# Orders

## Get a list Orders

```ruby
require 'net/http'
require 'rubygems'
require 'json'

uri = URI('http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/orders')
req = Net::HTTP::Post.new(uri, initheader = {'Content-Type' =>'application/json', 'Authorization' => "Bearer [auth_token]"})
http = Net::HTTP.new(uri.host, 80)
resp = http.request(req)
products = JSON.parse(resp.body)['products']
```

```shell
curl -X "GET" "http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/orders" \
	-H "Authorization: Bearer [auth_token]" \
	-H "Content-Type: application/json" \
	-d "{}"
```

> The above command returns JSON structured like this:

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


### HTTP Request

`GET http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/products`

### Query Parameters

Parameter  | Description
--------- | ------- | -----------
name  | Name of Product
sku | SKU of Product

<aside class="success">
Remember — all requests must contain an Authorization Token in the headers.
</aside>

## Get a Specific Product

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

> The above command returns JSON structured like this:

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

`GET http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/products/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the product to retrieve
