---
title: Rotessa API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://client.rotessa.com/signups/signup', target=_blank>Sign Up to acquire a developer key.</a>

includes:
  - customers
  - transaction_schedules
  - errors

search: true
---

# Introduction

The Rotessa API allows access to the core Rotessa platform. The endpoints allow you to manage customers and transactions in the Rotessa system.

You can view code examples on the right.

# Authentication

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "rotessa_endpoint"
  -H "Authorization: Token token=\"your_api_key\""
```

> Make sure to replace `your_api_key` with your API key.

Rotessa uses API keys to allow access to the API. You can acquire an API key by logging in to Roessa and generating a new API key under API Keys.

Rotessa expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Token token="your_api_key"`

<aside class="notice">
You must replace `your_api_key` with your personal API key.
</aside>
