---
title: API Reference

language_tabs:
  - shell


toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the SimplyEmail API! You can use our API to access SimplyEmail API endpoints, which can get and search for emails on the web that have been scrapped. 

We have language bindings in Shell and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# SimplyEmail Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Config

## Version

```shell
curl "http://example.com/api/version?token=447xadjtxla1elkbw9e6ojb5rd2ueaufm8r59kp7"
```

> The above command returns JSON structured like this:

```json
{
  "version": "v1.4.2"
}
```

This API call gets the current version of the SimplyEmail endpoint.
Authetication is required for even a version request.

### HTTP Request

`GET http://example.com/api/version?token=447xadjtxla1elkbw9e6ojb5rd2ueaufm8r59kp7`

### Query Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
Token |  | True | Required for auth

<aside class="success">
Remember — authentication is required for all calls!
</aside>


# Reporting

## All Reporting 

```shell
curl "curl https://0.0.0.0:1337/api/reporting?
token=447xadjtxla1elkbw9e6ojb5rd2ueaufm8r59kp7"
```

> The above command returns JSON structured like this:

```json
{
  "reports": [
    {
      "domain": "example.com", 
      "emails_domain": 5, 
      "emails_found": 9, 
      "emails_unique": 5, 
      "end_time": "02/07/2016 11:34:33", 
      "modules_enabled_key": 0, 
      "search_id": 2072016113418, 
      "start_time": "02/07/2016 11:34:18"
    }, 
    {
      "domain": "example1.com", 
      "emails_domain": 44, 
      "emails_found": 59, 
      "emails_unique": 44, 
      "end_time": "02/07/2016 11:35:11", 
      "modules_enabled_key": 0, 
      "search_id": 2072016113454, 
      "start_time": "02/07/2016 11:34:54"
    }
  ]
}
```

This API call returns all the search reports conducted in the DB.
This will allow corelation to emails obtained during a search via search_id. 

### HTTP Request

`GET https://0.0.0.0:1337/api/reporting`

### URL Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
Token |  | True | Required for auth


## Domain Search

```shell
curl "curl https://0.0.0.0:1337/api/reporting/domain/
example.com?token=447xadjtxla1elkbw9e6ojb5rd2ueaufm8r59kp7"
```

> The above command returns JSON structured like this:

```json
{
  "reports": [
    {
      "domain": "example.com", 
      "emails_domain": 5, 
      "emails_found": 9, 
      "emails_unique": 5, 
      "end_time": "02/07/2016 11:34:33", 
      "modules_enabled_key": 0, 
      "search_id": 2072016113418, 
      "start_time": "02/07/2016 11:34:18"
    }, 
    {
      "domain": "example.com", 
      "emails_domain": 44, 
      "emails_found": 59, 
      "emails_unique": 44, 
      "end_time": "02/07/2016 11:35:11", 
      "modules_enabled_key": 0, 
      "search_id": 2072016113454, 
      "start_time": "02/07/2016 11:34:54"
    }
  ]
}
```

This API call returns all the search reports conducted in the DB
related to the supplied domain.

### HTTP Request

`GET https://0.0.0.0:1337/api/reporting/domain/<DOMAIN>`

### URL Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
Token |  | True | Required for auth
Domain | | True | Domain name to search reports for.





# Domains

## All Domains

```shell
curl "curl https://0.0.0.0:1337/api/domain?
token=447xadjtxla1elkbw9e6ojb5rd2ueaufm8r59kp7"
```

> The above command returns JSON structured like this:

```json
{
  "domains": [
    {
      "allows_verification": 0, 
      "domain": "example1.com", 
      "email_count": 6, 
      "instances_scraped": 0, 
      "last_scrapped": "02/07/2016 11:34:18", 
      "pattern": "{first}", 
      "webmail": 0
    }, 
    {
      "allows_verification": 0, 
      "domain": "example2.com", 
      "email_count": 44, 
      "instances_scraped": 0, 
      "last_scrapped": "02/07/2016 11:34:54", 
      "pattern": "{first}{last}", 
      "webmail": 0
    }, 
    {
      "allows_verification": 0, 
      "domain": "example3.com", 
      "email_count": 0, 
      "instances_scraped": 0, 
      "last_scrapped": "03/07/2016 00:48:26", 
      "pattern": "", 
      "webmail": 0
    }
  ]
}
```

This API call returns all the search domains that
have been searched. This supports building a 
domain list.

### HTTP Request

`GET https://0.0.0.0:1337/api/domain`

### URL Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
Token |  | True | Required for auth


## Target Domain

```shell
curl "curl https://0.0.0.0:1337/api/domain/example3.com
?token=447xadjtxla1elkbw9e6ojb5rd2ueaufm8r59kp7"
```

> The above command returns JSON structured like this:

```json
{
  "domain": {
    "allows_verification": 0, 
    "domain": "example3.com", 
    "email_count": 6, 
    "instances_scraped": 0, 
    "last_scrapped": "02/07/2016 11:34:18", 
    "pattern": "{first}", 
    "webmail": 0
  }
}
```

This API call returns a specfic domain 
supplied by user. This returns a JSON object
with all the required doman info

### HTTP Request

`GET https://0.0.0.0:1337/api/domain/example3.com`

### URL Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
Token |  | True | Required for auth
Domain | | True | The target domain requested





# Emails

## All Emails

```shell
curl "curl https://0.0.0.0:1337/api/email?
token=447xadjtxla1elkbw9e6ojb5rd2ueaufm8r59kp7"
```

> The above command returns JSON structured like this:

```json
{
  "emails": [
    {
      "domain": "example.com", 
      "email_address": "info@example.com", 
      "email_verified": 0, 
      "first_name": "", 
      "first_seen": "02/07/2016 11:34:33", 
      "instances_seen": 3, 
      "last_name": "", 
      "last_seen": "02/07/2016 20:41:40", 
      "name_generated_email": 0, 
      "score": 0
    }, 
    {
      "domain": "example.com", 
      "email_address": "fef@example.com", 
      "email_verified": 0, 
      "first_name": "", 
      "first_seen": "02/07/2016 11:34:33", 
      "instances_seen": 3, 
      "last_name": "", 
      "last_seen": "02/07/2016 20:41:40", 
      "name_generated_email": 0, 
      "score": 0
    }, 
    {
      "domain": "example.com", 
      "email_address": "dall@example.com", 
      "email_verified": 0, 
      "first_name": "", 
      "first_seen": "02/07/2016 11:34:33", 
      "instances_seen": 1, 
      "last_name": "", 
      "last_seen": "02/07/2016 20:41:40", 
      "name_generated_email": 0, 
      "score": 0
    }
  ]
}
```

This API call returns all the emails in the 
db. This call is offten not public due to
mlarge backends.

### HTTP Request

`GET https://0.0.0.0:1337/api/email`

### URL Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
Token |  | True | Required for auth


## Target Email

```shell
curl "curl https://0.0.0.0:1337/api/email/info@example.com?
token=447xadjtxla1elkbw9e6ojb5rd2ueaufm8r59kp7"
```

> The above command returns JSON structured like this:

```json
{
  "email": {
    "domain": "example.com", 
    "email_address": "info@example.com", 
    "email_verified": 0, 
    "first_name": "", 
    "first_seen": "02/07/2016 11:34:33", 
    "instances_seen": 3, 
    "last_name": "", 
    "last_seen": "02/07/2016 20:41:40", 
    "name_generated_email": 0, 
    "score": 0
  }
}
```

This API call returns all the emails in the 
db. This call is offten not public due to
mlarge backends.

### HTTP Request

`GET https://0.0.0.0:1337/api/email/<EMAIL@ADDR.COM>`

### URL Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
Token |  | True | Required for auth
Email Address | | True | User supplied email to inspect





