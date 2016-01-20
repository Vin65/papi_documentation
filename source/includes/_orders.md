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
orders = JSON.parse(resp.body)['orders']
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
	"orders":[{
		"id":1,
		"order_number":"12345"
	}]
}
```

### HTTP Request

`GET http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/orders`

### Query Parameters

Parameter    | Description
------------ | ----------------------
order_number | Order Number of Order

<aside class="success">
Remember — all requests must contain an Authorization Token in the headers.
</aside>

## Get a Specific Order

```ruby
require 'net/http'
require 'rubygems'
require 'json'

uri = URI('http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/orders/1')
req = Net::HTTP::Post.new(uri, initheader = {'Content-Type' =>'application/json', 'Authorization' => "Bearer [auth_token]"})
http = Net::HTTP.new(uri.host, 80)
resp = http.request(req)
order = JSON.parse(resp.body)['order']
```


```shell
curl -X "GET" "http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/orders/1" \
	-H "Authorization: Bearer [auth_token]" \
	-H "Content-Type: application/json" \
	-d "{}"
```

> The above command returns JSON structured like this:

```json
{```json
{
	"order":{
		"id":1,
		"order_number":"12345"
	}
}
```

This endpoint retrieves a specific order.

### HTTP Request

`GET http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/orders/{id}`

### URL Parameters

Parameter | Description
--------- | -------------------------------
ID        | The ID of the order to retrieve
