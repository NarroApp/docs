---
title: Narro API Reference Docs

language_tabs:
  - shell: curl
  - ruby: Ruby
  - javascript: Node.js

toc_footers:
  - <a href='https://www.narro.co/oauth2/clients'>Register Your Client/Application</a>
  - <a href='https://github.com/NarroApp/docs'>Contribute to these docs on GitHub</a>
  - <a href='https://www.narro.co/developer/terms'>API Terms of Service</a>
  - <a href='http://status.narro.co'>Status Page</a>

includes:
  - authentication
  - account
  - articles
  - search
  - fit
  - errors

search: true
---

# Introduction

~~~shell
# API endpoint:
'https://www.narro.co/api/v1'
~~~

~~~ruby
# API endpoint:
'https://www.narro.co/api/v1'
~~~

~~~javascript
// API endpoint:
'https://www.narro.co/api/v1'
~~~

Welcome to the Narro API documentation! You can use our API to access articles and readings, as well as submit them on behalf of customers.

The Narro API is organized around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support [cross-origin resource sharing](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing), allowing you to interact securely with our API from a client-side web application (though you should never expose your secret API key in any public website's client-side code). [JSON](http://www.json.org/) is returned by all API responses, including errors, although [our API libraries](https://github.com/narroapp) convert responses to appropriate language-specific objects.

This API documentation is openly hosted [on GitHub](https://github.com/NarroApp/docs), which means you can contribute or edit by submitting a pull request.
