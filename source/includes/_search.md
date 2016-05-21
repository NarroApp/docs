# Search

## Search Articles

```ruby
require 'uri'
require 'net/http'

url = URI("https://www.narro.co/api/v1/search/articles?limit=2&term=Trump")

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
    url: 'https://www.narro.co/api/v1/search/articles?limit=2&term=Trump',
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
    --url https://www.narro.co/api/v1/search/articles?limit=2&term=Trump\
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
                "length": 332.956735,
                "url": "https://s3.amazonaws.com/nareta-articles/audio/540cc8cb48e3e80200000001/30460753-b4b5-468d-8a4d-dabcb384dc1a.mp3",
                "voice": "Salli",
                "rate": 1
            },
            "created": "2016-02-23T17:31:11.925Z",
            "description": "By Miranda Popkey \u00a0 \u00a0\n\u00a0\u00a0\nCyclone Winston, the second most powerful storm ever recorded in the South Pacific, made landfall in Fiji with 40-foot waves ...",
            "id": "56cc9751750df10300610bf7",
            "image": null,
            "language": "en-US",
            "links": [],
            "location": "https://www.narro.co/article/56cc9751750df10300610bf7",
            "preview": false,
            "title": "Email Fwd: Harper's Weekly Review",
            "url": "https://www.narro.co/article/56cc9751750df10300610bf7",
            "via": "email"
        },
        {
            "active": true,
            "audio": {
                "length": 65.201633,
                "url": "https://s3.amazonaws.com/nareta-articles/audio/540cc8cb48e3e80200000001/89a7eac8-9363-44ea-9624-0b107b4fe221.mp3",
                "voice": "Salli",
                "rate": 1
            },
            "created": "2016-02-11T20:10:43.653Z",
            "description": "by Brent Simmons\nIt Will Be Trump\nThe South Carolina primary is where the establishment fixes the errors of Iowa and New Hampshire. It's Lee Atwater's...",
            "id": "56bceac153625e03007f0172",
            "image": null,
            "language": "en-US",
            "links": [],
            "location": "https://www.narro.co/article/56bceac153625e03007f0172",
            "preview": false,
            "title": "It Will Be Trump",
            "url": "http://inessential.com/2016/02/11/it_will_be_trump",
            "via": "feed"
        }
    ],
    "meta": {
        "term": "Trump"
    }
}
```

Given a search term, retrieve the authenticating user's articles containing that term. A search term can be any combination of words extracted from the article body.

See [an example request in _many_ languages](https://api.apiembed.com/?source=https://github.com/NarroApp/docs/raw/master/source/har/searchArticles.json&targets=all).

### HTTP Request

`GET https://www.narro.co/api/v1/search/articles?limit=2&term=Trump`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
term | | Required in query string, resulting articles will contain this set of terms in their body text.
limit | 20 | If specified, resulting dataset will be limited to count.
skip | 0 | If specified, resulting dataset will skip first <n> records.

<aside class="info">
Remember — For attributes, see <a href="#retrieve-an-article">Retrieve an Article</a>. Article objects returned via this endpoint will not contain extracted links.
</aside>
