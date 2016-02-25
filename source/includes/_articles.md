# Articles

## Retrieve an Article

```ruby
require 'uri'
require 'net/http'

url = URI("https://www.narro.co/api/v1/articles/56ca50f7c1dac403006bb309")

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
    url: 'https://www.narro.co/api/v1/articles/56ca50f7c1dac403006bb309',
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
    --url https://www.narro.co/api/v1/articles/56ca50f7c1dac403006bb309 \
    --header 'accept: application/json' \
    --header 'authorization: Bearer <access_token>'
```

> Example response:

```json
{
    "_id": "56ca50f7c1dac403006bb309",
    "accountId": "540cc8cb48e3e80200000001",
    "active": true,
    "canonical": "https://en.wikipedia.org/wiki/Banksia_aemula",
    "created": "2016-02-22T00:06:44.746Z",
    "description": "Banksia aemula\nBanksia elatior\nR. Br.\nBanksia aemula, commonly known as the wallum banksia, is a lignotuberous shrub of the family Proteaceae . Found ...",
    "favicon": "/static/favicon/wikipedia.ico",
    "hardURL": "https://en.wikipedia.org/wiki/Banksia_aemula",
    "image": null,
    "lang": "en-US",
    "links": [
        {
            "_id": "56ca5114c1dac403006bb347",
            "href": "/wiki/Lignotuber",
            "text": "lignotuberous"
        },
        {
            "_id": "56ca5114c1dac403006bb346",
            "href": "/wiki/Shrub",
            "text": "shrub"
        }
    ],
    "modified": "2016-02-22T00:06:44.746Z",
    "mp3Length": 1394.99102,
    "mp3URL": "https://s3.amazonaws.com/nareta-articles/audio/540cc8cb48e3e80200000001/86c88170-26a7-4de2-c98e-c7356b77b2aa.mp3",
    "preview": false,
    "star": false,
    "title": "Banksia aemula",
    "topics": [
        {
            "_id": "56ca5114c1dac403006bb30f",
            "score": 1,
            "stem": "banksia"
        },
        {
            "_id": "56ca5114c1dac403006bb30e",
            "score": 0.7,
            "stem": "aemula"
        },
        {
            "_id": "56ca5114c1dac403006bb30d",
            "score": 0.3142857142857143,
            "stem": "speci"
        },
        {
            "_id": "56ca5114c1dac403006bb30c",
            "score": 0.2,
            "stem": "flower"
        }
    ],
    "url": "https://en.wikipedia.org/wiki/Banksia_aemula",
    "via": "ifttt",
    "voiceName": "Salli"
}
```

Retrieves the details of an article that has previously been created. Supply the unique article ID that was returned from your previous request, and Narro will return the corresponding article information. A subset of this information is returned when creating or listing the article.

See [an example request in _many_ languages](https://api.apiembed.com/?source=https://github.com/NarroApp/docs/raw/master/source/har/article.json&targets=all).

### HTTP Request

`GET https://www.narro.co/api/v1/articles/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the article to retrieve

### Attributes

Name | Type | Description
---- | ---- | -----------
_id | string | Unique ID for this article resource
active | boolean | Indicates whether this article is available in the user's podcast feed
canonical | string | Extracted canonical URL for this article (Absent for plain-text readings)
created | timestamp | 
description | string |
favicon | string | Path to the article's publisher's favicon (Absent for plain-text readings)
hardURL | string | URL of this article, stripped of query parameters (Absent for plain-text readings)
image | string | If found during extraction, an image representing the article
lang | string | Detected language of this article
links | object | Extracted links from the article text, each comprising an href string and text sring (Absent for plain-text readings)
modified | timestamp | 
mp3URL | string | URL to the article's audio MP3 file
mp3Length | number | Length of article MP3, in seconds
preview | boolean | Indicates whether this article was read in "preview" mode, which truncates the reading
star | boolean | Indicates whether the user has starred or otherwise favorited this article
title | string | Extracted or provided article title
topics | object | Extracted topics from the article text, each comprising a score number and stem string
url | string | The original URL provided for this article (Absent for plain-text readings)
via | string | The source through which the article was submitted to Narro
voiceName | string | The voice used to read this article

## List All Articles

```ruby
require 'uri'
require 'net/http'

url = URI("https://www.narro.co/api/v1/articles?limit=1")

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
    url: 'https://www.narro.co/api/v1/articles',
    qs: {
        limit: '1'
    },
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
    --url 'https://www.narro.co/api/v1/articles?limit=1' \
    --header 'accept: application/json' \
    --header 'authorization: Bearer <access_token>'
```

> Example response:

```json
{
    "data": [
        {
            "_id": "56ca50f7c1dac403006bb309",
            "active": true,
            "canonical": "https://en.wikipedia.org/wiki/Banksia_aemula",
            "created": "2016-02-22T00:06:44.746Z",
            "description": "Banksia aemula\nBanksia elatior\nR. Br.\nBanksia aemula, commonly known as the wallum banksia, is a lignotuberous shrub of the family Proteaceae . Found ...",
            "favicon": "/static/favicon/wikipedia.ico",
            "hardURL": "https://en.wikipedia.org/wiki/Banksia_aemula",
            "image": null,
            "lang": "en-US",
            "modified": "2016-02-22T00:06:44.746Z",
            "mp3Length": 1394.99102,
            "mp3URL": "https://s3.amazonaws.com/nareta-articles/audio/540cc8cb48e3e80200000001/86c88170-26a7-4de2-c98e-c7356b77b2aa.mp3",
            "preview": false,
            "star": false,
            "title": "Banksia aemula",
            "url": "https://en.wikipedia.org/wiki/Banksia_aemula",
            "via": "ifttt",
            "voiceName": "Salli"
        }
    ],
    "meta": {
        "next": "/api/v1/articles?limit=20&skip=1"
    }
}
```

Returns a list of articles previously created by the user. The articles are returned in sorted order, with the most recent articles appearing first.

See [an example request in _many_ languages](https://api.apiembed.com/?source=https://github.com/NarroApp/docs/raw/master/source/har/articles.json&targets=all).

### HTTP Request

`GET https://www.narro.co/api/v1/articles`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
limit | 20 | If specified, resulting dataset will be limited to count.
skip | 0 | If specified, resulting dataset will skip first <n> records.

<aside class="info">
Remember — For attributes, see <a href="#retrieve-an-article">Retrieve an Article</a>. Article objects returned via this endpoint will not contain extracted links and topics.
</aside>

## Article Submission

~~~ruby
require 'uri'
require 'net/http'

url = URI("https://www.narro.co/api/v1/articles")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer <access_token>'
request.body = "{\"url\": \"https://www.narro.co/faq\", \"title\": \"My Optional, Custom Title\"}"

response = http.request(request)
puts response.read_body
~~~

~~~javascript
var request = require("request");

var options = { method: 'POST',
    url: 'https://www.narro.co/api/v1/articles',
    headers: {
        authorization: 'Bearer <access_token>',
        'content-type': 'application/json',
        accept: 'application/json'
    },
    body: {
        url: 'https://www.narro.co/faq',
        title: 'My Optional, Custom Title'
    },
    json: true
};

request(options, function (error, response, body) {
    if (error) throw new Error(error);
    console.log(body);
});
~~~

~~~shell
curl --request POST \
    --url https://www.narro.co/api/v1/articles \
    --header 'accept: application/json' \
    --header 'authorization: Bearer <access_token>' \
    --header 'content-type: application/json' \
    --data '{"url": "https://www.narro.co/faq", "title": "My Optional, Custom Title"}'
~~~

> Example response:

~~~json
{
    "data": [
        {
            "_id": "56ca50f7c1dac403006bb309"
        }
    ],
    "meta": {}
}
~~~

Create an article for any web page that you would like to hear! The article must be located at a publicly accessible URL. The article text will be automatically extracted, and read in the voice (or one of the voices in a selected rotation) selected by the user. The written language of the article will be automatically detected by sample, and an appropriate voice will be selected if the language is not native to the user.

See [an example article request in _many_ languages](https://api.apiembed.com/?source=https://github.com/NarroApp/docs/raw/master/source/har/createArticle.json&targets=all).
See [an example plain-text request in _many_ languages](https://api.apiembed.com/?source=https://github.com/NarroApp/docs/raw/master/source/har/createText.json&targets=all).

### HTTP Request

`POST https://www.narro.co/api/v1/articles`

### Body Parameters

Parameter | Type | Description
--------- | ---- | -----------
url | string | The publicly accessible URL for content to be read. This field is **required** unless `text` is specified.
title | string | If specified, this string will be used as the `title` of the resulting `article`.
text | string | If specified, this field's value will be read. This will override any content residing at the `url`. Please choose to pass _either_ `url` or `text`.