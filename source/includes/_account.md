# Account

## Retrieve Account Details

```ruby
require 'uri'
require 'net/http'

url = URI("https://www.narro.co/api/v1/account")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["accept"] = 'application/json'
request["authorization"] = 'Bearer <access_token>'

response = http.request(request)
puts response.read_body
```

```javascript
var request = require("request");

var options = {
    method: 'GET',
    url: 'https://www.narro.co/api/v1/account',
    headers: {
        authorization: 'Bearer <access_token>',
        accept: 'application/json'
    }
};

request(options, function (error, response, body) {
    if (error) throw new Error(error);
    console.log(body);
});
```

```shell
curl --request GET \
    --url https://www.narro.co/api/v1/account\
    --header 'accept: application/json' \
    --header 'authorization: Bearer <access_token>'
```

> Example response:

```json
{
    "confirmed": true,
    "created": "2015-12-02T02:11:53.250Z",
    "email": "foo@example.com",
    "id": "accountid123456789",
    "image": "",
    "modified": "2016-02-28T20:18:24.349Z",
    "pro": true,
    "vanity": "vanity123",
    "voices": [
        {
            "gender": "Male",
            "language": "en-US",
            "name": "Joey"
        },
        {
            "gender": "Female",
            "language": "en-US",
            "name": "Ava"
        }
    ]
}
```

Retrieves the details of the authenticating user's account.

See [an example request in _many_ languages](https://api.apiembed.com/?source=https://github.com/NarroApp/docs/raw/master/source/har/account.json&targets=all).

### HTTP Request

`GET https://www.narro.co/api/v1/account`

### Attributes

Name | Type | Description
---- | ---- | -----------
confirmed | boolean | Indicated whether the account has been confirmed via email
created | timestamp | Creation date, formatted to ISO datetime
email | string | Account's recorded email address
id | string | Unique ID for this account resource
image | string | Optional image used in account's public podcast syndication
modified | timestamp | Date of last modification, formatted to ISO datetime
pro | boolean | Indicates whether the account is Pro-level
vanity | string | Unique ID used for the account's public podcast URL
voices | array | Chosen voices to be used for readings under this account
