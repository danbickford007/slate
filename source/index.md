---
title: API Reference

language_tabs:
  - shell
  - ruby

toc_footers:
  - <a href='/settings'>Sign Up for a Developer Key</a>
  - <a href='http://www.licensearch.com'>Back to portal.</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to licensearch.com. An api for business license information in the following states.

<a href='http://www.licensearch.com'>Back to portal.</a>
|
<a href='http://www.github.com/danbickford007/licensearch-gem'>RUBY GEM</a>

* Florida
* Georgia 

More states will be added in the future.

# Authentication

> To authorize, use this code:

A note: queries to the API via the ruby gem does not require authentication for each request.

```ruby
require 'licensearch'

Florida.auth
```

```shell
# With shell, you can just pass the correct header with each request
curl -i 'http://www.licensearch.com/api/auth?token=mytoken'
```

> {secret: abc123}

```shell
# Then use this token for every request after for a 60 minute period.
curl -i 'http://www.licensearch.com/api/florida/business/count?token=mytoken&secret=abc123'
```
```ruby
require 'licensearch'

Florida::Business.count
```


> {count: 1234567}

Licensearch.com uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://www.licensearch.com/settings).

Licensearch.com expects for the API key and secret to be included in all API requests to the server in a header that looks like the following:

`?token=mytoken&secret=abc123`

<aside class="notice">
You must replace <code>token</code> with your personal API key and <code>secret</code>with the temporary secret.
</aside>

# Business

## Get Business Count

```shell
# Then use this token for every request after for a 60 minute period.
curl -i '/api/florida/business/count'
```
```ruby
require 'licensearch'

Florida::Business.count
```


> The above command returns JSON structured like this:

```json
{
  "count": 1234
}
```


This endpoint count of businesses.

### HTTP Request

`GET http://www.licensearch.com/api/florida/business/count`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
active_only | false | If set to true, the result will filtered by businesses with active licenses.
inactive_only | false | If set to true, the result will filtered by businesses with inactive licenses.

<aside class="success">
Remember — setting both active_only and inactive_only will not return results!
</aside>

## Get all active businesses

```shell
# Retrieve array of active businesses in florida.
curl -i '/api/florida/business/active?page1'
```

> The above command returns JSON structured like this:

```json
 [
   {
     "id":29,
     "name":"A CORP.",
     "document_number":"484073",
     "ein":"59-1581183",
     "date_filed":"09/08/1975",
     "status":"ACTIVE",
     "last_event":"NAME CHANGE AMENDMENT",
     "principal_address":"\r\n\r\n\r\n14508 S. TAMIAMI TRAIL\r\n            FT MYERS, FL 33912\r\n\r\n    \r\n\r\n    \r\n\r\n",
     "mailing_address":null,"agent":"HUCKE, WILLIAM J\r\n",
     "state":"FL",
     "url":null
    }
 ] 
```

This endpoint retrieves a specific business.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET /api/florida/business/active?page=1`

### URL Parameters

Parameter | Description
--------- | -----------
page        integer : pagination



## Query for business - Florida

```shell
# Retrieve array of businesses matching criteria.
curl -i '/api/florida/business/query?name=abc'
```

> The above command returns JSON structured like this:

```json
 [
   {
     "id":29,
     "name":"A CORP.",
     "document_number":"484073",
     "ein":"59-1581183",
     "date_filed":"09/08/1975",
     "status":"ACTIVE",
     "last_event":"NAME CHANGE AMENDMENT",
     "principal_address":"\r\n\r\n\r\n14508 S. TAMIAMI TRAIL\r\n            FT MYERS, FL 33912\r\n\r\n    \r\n\r\n    \r\n\r\n",
     "mailing_address":null,"agent":"HUCKE, WILLIAM J\r\n",
     "state":"FL",
     "url":null
    }
 ] 
```

This endpoint retrieves a specific business.

### HTTP Request

`GET /api/florida/business/query?name=abc`

### URL Parameters

Parameter | Description
--------- | -----------
name      |  Business Name
document_number | Document Number
ein       | EIN
date_filed | The date business was filed
status    | ACTIVE or INACTIVE pertaining to business license
last_event | Last recorded activity of business
principal_address | Official Address
mailing_address | The mailing address
state     | Which state business is in
url       | URL of business 



## Query for business - Georgia

```shell
# Retrieve array of businesses matching criteria.
curl -i '/api/georgia/business/query?name=abc'
```

> The above command returns JSON structured like this:

```json
 [
   {
     "id":29,
     "name":"A CORP.",
     "document_number":"484073",
     "ein":"59-1581183",
     "date_filed":"09/08/1975",
     "status":"ACTIVE",
     "last_event":"NAME CHANGE AMENDMENT",
     "principal_address":"\r\n\r\n\r\n14508 S. TAMIAMI TRAIL\r\n            FT MYERS, FL 33912\r\n\r\n    \r\n\r\n    \r\n\r\n",
     "mailing_address":null,"agent":"HUCKE, WILLIAM J\r\n",
     "state":"FL",
     "url":null
    }
 ] 
```

This endpoint retrieves a specific business.

### HTTP Request

`GET /api/georgia/business/query?name=abc`

### URL Parameters

Parameter | Description
--------- | -----------
name      |  Business Name
business_type | Document Number
naics_code | NAICS Code 
principal_address | Main Address
state | State formed in
control_number | Control Number
status | Status
date_formed | Date Business Formed
agent | Registered Agent
address | Registered Address
