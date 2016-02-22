# Authentication

```ruby
require 'rest_client'

access_token = '<access_token>'
RestClient.get('https://www.narro.co/api/v1',
    {:Authorization => 'Bearer ' + access_token,
    :accept => :json})
```

```javascript
var request = require('request');

request.get('https://www.narro.co/api/v1',
    {auth: {bearer: '<access_token>'}},
function(error, request, body) {
    console.log(error || body);
});
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://www.narro.co/api/v1" \
    -H "Authorization: Bearer <access_token>"
```

Narro API clients use the [OAuth2 flow](http://oauth.net/2/) to request an access token. Clients then use access tokens to access the API on behalf of Narro accounts. You can register a new Narro API client/application, view your applications, and generate credentials at our [developer portal](https://www.narro.co/oauth2/clients).

Narro expects the Bearer access token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <access_token>`

If you would like to view an example application/server implementing the OAuth2 flow with Narro's API, we have provided [an example in our platform_samples repository](https://github.com/NarroApp/platform-samples/tree/master/api/ruby/oauth2).
