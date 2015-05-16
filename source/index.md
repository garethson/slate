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
  -H "Authorization: Token token=\"your_api_key\""
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
  -H "Authorization: Token token=\"your_api_key\""
```

> The above command returns JSON structured like this:

```json
{
  "response": [
    {
      "id": 1,
      "name": "Mike Smith",
      "identifier": "MikeSmith0001",
      "email": "mikesmith@test.com",
      "home_phone": "(204) 555 5555",
      "cell_phone": "(204) 555 4444",
      "bank_name": "Scotiabank",
      "created_at": "2015-02-10T23:50:45.000-06:00",
      "updated_at": "2015-02-10T23:50:45.000-06:00",
      "custom_identifier": "Mikey",
      "active": true,
      "address": {
        "address_1": "123 Main Street",
        "address_2": "Unit 4",
        "city": "Toronto",
        "province_code": "ON",
        "postal_code": "M1B 0B7"
      }
    },
    {
      "id": 2,
      "name": "Susan Johnson",
      "identifier": "SUSANJO0002",
      "email": "susan@test.com",
      "home_phone": "(204) 111 4321",
      "cell_phone": "(204) 111 1234",
      "bank_name": "Royal Bank",
      "created_at": "2015-02-10T23:50:45.000-06:00",
      "updated_at": "2015-02-10T23:50:45.000-06:00",
      "custom_identifier": "Suze-44",
      "active": true,
      "address": {
        "address_1": "234 Main Street",
        "address_2": "",
        "city": "Calgary",
        "province_code": "AB",
        "postal_code": "T1X 0L3"
      }
    }
  ],
  "count": 2
}
```

This endpoint retrieves all customers.

### HTTP Request

`GET https://api.rotessa.com/customers`

<!-- ### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted. -->

<aside class="success">
Remember — a happy customer is an authenticated customer!
</aside>

## Get a Specific Customer

```shell
curl "http://api.rotessa.com/api/customers/1.json"
  -H "Authorization: Token token=\"your_api_key\""
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "id": 1,
    "name": "Mike Smith",
    "identifier": "MikeSmith0001",
    "email": "mikesmith@test.com",
    "home_phone": "(204) 555 5555",
    "cell_phone": "(204) 555 4444",
    "bank_name": "Scotiabank",
    "created_at": "2015-02-10T23:50:45.000-06:00",
    "updated_at": "2015-02-10T23:50:45.000-06:00",
    "custom_identifier": "Mikey",
    "active": true,
    "address": {
      "address_1": "123 Main Street",
      "address_2": "Unit 4",
      "city": "Toronto",
      "province_code": "ON",
      "postal_code": "M1B 0B7"
    }
    "transaction_schedules": [
      {
        "amount": "120.00",
        "frequency": "Weekly",
        "process_date": "2015-05-12",
        "installments": 10,
        "comment": "Monthly Membership Fees",
        "next_process_date": "2015-05-19",
        "created_at": "2015-05-12T23:02:08.000-05:00",
        "updated_at": "2015-05-12T23:04:00.000-05:00"
      }
    ],
    "financial_transactions": [
      {
        "amount": "120.00",
        "process_date": "2015-05-12",
        "status": "Pending",
        "status_reason": null,
        "transaction_schedule_id": 33630,
        "created_at": "2015-05-12T23:04:00.000-05:00",
        "updated_at": "2015-05-12T23:04:00.000-05:00"
      }
    ]
  }
}
```

This endpoint retrieves a specific customer.

<aside class="warning">If you're not using an administrator API key, note that some customers will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://api.rotessa.com/api/customers/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the customer to retrieve












# Transaction Schedules

## Create A Transaction Schedule


```shell
curl -X POST \
     -H 'Content-Type: application/json' \
     -H 'Authorization: Token token="sS0md0PLYj9sgQ6RJgN1nQ"' \
     -d '{"transaction_schedule": {"firstName":"Kris", "lastName":"Jordan"}}' \
     http://api.lvh.me:3000/v1/transaction_schedules.json
```

> The above command returns JSON structured like this:

```json
{
  "response": [
    {
      "id": 1,
      "name": "Mike Smith",
      "identifier": "MikeSmith0001",
      "email": "mikesmith@test.com",
      "home_phone": "(204) 555 5555",
      "cell_phone": "(204) 555 4444",
      "bank_name": "Scotiabank",
      "created_at": "2015-02-10T23:50:45.000-06:00",
      "updated_at": "2015-02-10T23:50:45.000-06:00",
      "custom_identifier": "Mikey",
      "active": true,
      "address": {
        "address_1": "123 Main Street",
        "address_2": "Unit 4",
        "city": "Toronto",
        "province_code": "ON",
        "postal_code": "M1B 0B7"
      }
    }
  ],
  "count": 2
}
```

This endpoint creates a transaction schedule for a customer.

### HTTP Request

`POST https://api.rotessa.com/v1/transaction_schedules`

### Post Parameters

Parameter | Default | Description
--------- | ------- | -----------
amount | - | Amount for schedule
installments | 1 | The number of installments

<aside class="success">
When creating schedules you must blah.
</aside>







