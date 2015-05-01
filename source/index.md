---
title: Rotessa API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up to acquire a developer key.</a>

includes:
  - errors

search: true
---

# Introduction

You can use the Rotessa API to access Rotessa API endpoints, which allows you to manage customers and transactions in the Rotessa system.

We have language bindings for Shell and Ruby, you can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "rotessa_endpoint"
  -H "Token token=\"your_api_key\""
```

> Make sure to replace `your_api_key` with your API key.

Rotessa uses API keys to allow access to the API. You can acquire an API key by logging in to Roessa and generating a new API key under API Keys.

Rotessa expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Token token="your_api_key"`

<aside class="notice">
You must replace `your_api_key` with your personal API key.
</aside>

# Customers

## Get All Customers


```shell
curl "http://api.rotessa.com/api/customers"
  -H "Token token=\"your_api_key\""
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/3"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve

