# Article to Fit

## Find a Fitting Article

```ruby
require 'uri'
require 'net/http'

url = URI("https://www.narro.co/api/v1/fit?time=60&topic=Trump")

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
    url: 'https://www.narro.co/api/v1/fit?time=60&topic=Trump',
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
    --url https://www.narro.co/api/v1/fit?time=60&topic=Trump\
    --header 'accept: application/json' \
    --header 'authorization: Bearer <access_token>'
```

> Example response:

```json
{
    "data": [
        {
            "active": true,
                "audio": {
                "length": 60.944333,
                "url": "https://s3.amazonaws.com/nareta-articles/audio/55af0a83157eed030000011e/61e7b167-b3f9-4d21-b2b2-2f184242b5cc.mp3",
                "voice": "Brian"
            
                },
            "created": "2015-08-06T14:51:26.342Z",
            "description": "In The Wall Street Journal, Joe Queenan says Donald Trump clearly works for Hillary. When Clinton wins, Trump gets to install luxury condos in the Washington Monument.",
            "favicon": null,
            "id": "55c3746e8f828f030000008b",
            "image": "http://si.wsj.net/public/resources/images/BN-JQ873_queena_D_20150731124328.jpg",
            "language": "Brian",
            "links": [],
            "location": "https://www.narro.co/article/55c3746e8f828f030000008b",
            "title": "Clearly, the Donald Works for Hillary",
            "url": "http://www.wsj.com/articles/clearly-the-donald-works-for-hillary-1438382894",
            "via": "web"
            
        }
    ],
    "meta": {
        "search": {
            "mp3Length": {
                "$gte": 55,
                "$lte": 65
            },
            "topics.stem": [
                "trump"
            ]
        }
    }
}
```

Given a topic and/or time, retrieve articles to fit. A topic can be any combination of words extracted from the article body. A time can be any integer, in seconds.

See [an example request in _many_ languages](https://api.apiembed.com/?source=https://github.com/NarroApp/docs/raw/master/source/har/fitArticles.json&targets=all).

### HTTP Request

`GET https://www.narro.co/api/v1/fit?time=60&topic=Trump`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
topic | | Resulting articles will contain this topic in their body text.
time | 60 | In seconds. If specified, resulting articles will have a listening time +/- 5 seconds of this time.

<aside class="info">
Remember — For attributes, see <a href="#retrieve-an-article">Retrieve an Article</a>. Article objects returned via this endpoint will not contain extracted links.
</aside>
