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

You can use the Rotessa API to access Rotessa API endpoints, which allows you to manage customers and transactions in the Rotessa system.

We have language bindings for Shell and Ruby, you can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

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
