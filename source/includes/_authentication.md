# Authentication
Vin65 Market Services uses a temporary authorization token. You your email/password credentials to Authenticate yourself and obtain a new authorization token and then you can optionally cache the token until it expires.

All requests (other that the authenticate request) will require an Authorization header that uses an active Authorization token.


### HTTP Request

`POST http://vin65-plb-papi-298085473.us-west-2.elb.amazonaws.com/auth`

### Body Parameters

Parameter | Required  | Example          | Description
--------- | --------- | ---------------- | -----------
email     | true      | test@example.com | Name of Product
password  | true      | 12345678         | SKU of Product

`Authorization: Beaer [auth_token]`

<aside class="notice">
You must replace <code>[auth_token]</code> with your authorization token that you obtain from thr authenticate request.
</aside>


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
