---
title: API Reference

language_tabs:
  - shell
  - ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Vin65 Market Services API Documentation site. Here you will find information on how to authenticate and interact with this API.

# Authentication

> To Authenticate and retreive a new authorization token, use this code:

```shell
curl --data "email=supplier@example.com&password=12345678" http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/auth
```

```ruby
require 'net/http'
require 'rubygems'
require 'json'

uri = URI('http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/auth')
req = Net::HTTP::Post.new(uri, initheader = {'Content-Type' =>'application/json'})
req.body = {email: 'supplier@example.com', password: '12345678'}.to_json
http = Net::HTTP.new(uri.host, 80)
resp = http.request(req)
if resp.code == '201'
  token = JSON.parse(resp.body)['token']
else
  token = ''
end
```
> The above command returns JSON structured like this:

```json
{
	"token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE0NTM0MTExNzEsInV1aWQiOiJhODczNTA3Zi0yYThjLTQ2NDAtOThmYy1iZWU2MjVhYzZkZjcifQ.NbqSfsh2GdAr2cSyS0mKw9AE8wKUCgdgfubIbIsWhKNx1qm5uIxUMhfukL5Ha6jc0VuCABzx5L2ZdcYNRgtnhA",
	"created_at": "2016-01-20T21:19:31.000Z",
	"expires_at": "2016-01-21T21:19:31.000Z",
	"status": "Active"
}
```

Vin65 Market Services uses a temporary authorization token. You your email/password credentials to Authenticate yourself and obtain a new authorization token and then you can optionally cache the token until it expires.

All requests (other that the authenticate request) will require an Authorization header that uses an active Authorization token.

`Authorization: Beaer [auth_token]`

<aside class="notice">
You must replace <code>[auth_token]</code> with your authorization token that you obtain from thr authenticate request.
</aside>

# Products

## Get a list Products

```ruby
require 'net/http'
require 'rubygems'
require 'json'

uri = URI('http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/products')
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
}```


### HTTP Request

`GET http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/products`

### Query Parameters

Parameter | in | Description
--------- | ------- | -----------
name | URL | Name of Product
sku | URL | SKU of Product

<aside class="success">
Remember — all requests must contain an Authorization Token in the headers.
</aside>

## Get a Specific Product

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve
