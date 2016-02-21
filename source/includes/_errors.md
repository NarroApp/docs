# Errors

The Narro API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is malformed
401 | Unauthorized -- Your API key is incorrect or absent
403 | Forbidden -- The resouce requested is not accessible by general API consumers
404 | Not Found -- The specified resource could not be found
405 | Method Not Allowed -- You tried to access a resouce with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | Gone -- The resouce requested has been removed from our servers
429 | Too Many Requests -- Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
