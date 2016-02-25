# Authentication

```ruby
require 'uri'
require 'net/http'

url = URI("https://www.narro.co/api/v1")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["authorization"] = 'Bearer <access_token>'

response = http.request(request)
puts response.read_body
```

```javascript
var request = require("request");

var options = {
    method: 'GET',
    url: 'https://www.narro.co/api/v1',
    headers: {
        authorization: 'Bearer <access_token>'
    }
};

request(options, function (error, response, body) {
    if (error) throw new Error(error);
    console.log(body);
});
```

```shell
curl --request GET \
    --url https://www.narro.co/api/v1 \
    --header 'authorization: Bearer <access_token>'
```

Narro API clients use the [OAuth2 flow](http://oauth.net/2/) to request an access token. Clients then use access tokens to access the API on behalf of Narro accounts. You can register a new Narro API client/application, view your applications, and generate credentials at our [developer portal](https://www.narro.co/oauth2/clients).

Narro expects the Bearer access token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <access_token>`

If you would like to view an example application/server implementing the OAuth2 flow with Narro's API, we have provided [an example in our platform_samples repository](https://github.com/NarroApp/platform-samples/tree/master/api/ruby/oauth2).
