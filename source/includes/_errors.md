# Errors

<aside class="notice">This section will provide errors for each API call that users should use during API programing.</aside>

The SimplyEmail API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request may be messed up?
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- The API call requested is hidden for administrator / su tokens only
404 | Not Found -- The specified call could not be found
405 | Method Not Allowed -- You tried to access a kitten with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | No data to return -- The call did not return any data
418 | I'm a teapot
490 | Too Many Requests -- You're requesting too many kittens! Slow down!
491 | Gone -- The API call is not active on this endpoint.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
