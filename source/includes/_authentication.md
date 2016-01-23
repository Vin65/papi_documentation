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

> Example Response Headers

```headers
HTTP/1.1 201 Created
Cache-Control: max-age=0, private, must-revalidate
Content-Type: application/json; charset=utf-8
Date: Sat, 23 Jan 2016 19:43:28 GMT
ETag: W/"58faa33683c8bcf0322b9fe35476fcba"
Server: nginx/1.4.6 (Ubuntu)
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
X-Request-Id: 98413c49-84be-475c-a89e-0adba7b805a1
X-Runtime: 0.122787
X-XSS-Protection: 1; mode=block
Content-Length: 336
Connection: Close
```

> Example Response Body

```json
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJ1c2VyX2lkIjoyLCJleHAiOjE0NTM2NjQ2MDgsInV1aWQiOiJiMTUwMThkZi0zNDkzLTQ3YjQtODg3Yi1jNDYzZDc5NjhiOTEifQ.EdpkOXvNmCn_bD73FRtuPpLH0OieW7aUKMgjg3prXG4N3xoemaD2IrRw7GMYRb7QOuzD6Y-vbtZQ26Sz-gJnQQ",
  "created_at": "2016-01-23T19:43:28.000Z",
  "expires_at": "2016-01-24T19:43:28.000Z",
  "status": "Active"
}
```

Vin65 Market Services uses a temporary authorization token. You your email/password credentials to Authenticate yourself and obtain a new authorization token and then you can optionally cache the token until it expires.

All requests (other that the authenticate request) will require an Authorization header that uses an active Authorization token.

### HTTP Request

`POST http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/auth`

### Body Parameters

Parameter | Required  | Description
--------- | --------- | -----------
email     | true      | Email address of API client
password  | true      | Password address of API client

### Example Request Body
`{ email: 'test@example.com', password: '12345678' }</pre>`

### Errors
Code | Message               | Description
---- | --------------------- | -----------
401  | Unauthorized          | Authentication failed
404  | Not Found             | Not Found
429  | Too Many Requests     | Too many requests from this IP. Please wait and try again later
500  | Internal Server Error | Internal Server Error


Vin65 Market Services uses a temporary authorization token. You your email/password credentials to Authenticate yourself and obtain a new authorization token and then you can optionally cache the token until it expires.

All requests (other that the authenticate request) will require an Authorization header that uses an active Authorization token.
