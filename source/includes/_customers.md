# Customers

Customers represent individual customer accounts from which you which to withdraw funds.

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

## Create A Customer

```shell
curl -X POST \
     -H 'Content-Type: application/json' \
     -H 'Authorization: Token token="sS0md0PLYj9sgQ6RJgN1nQ"' \
     -d '{"custom_identifier": "asdf1234", "email": "test@rotessa.com", "name": "Mike Smith", "bank_name": "Scotiabank", "transit_number": "12345", "institution_number": "123", "account_number": "12345678", "address": { "address_1": "123 Main Street", "address_2": "Unit 4", "city": "Toronto", "province_code": "ON", "postal_code": "M1B 0B7" }}' \
     http://api.rotessa.com/v1/customers.json
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "name": "Mike Smith",
    "identifier": "MIKESMIT0001",
    "email": "test@rotessa.com",
    "home_phone": null,
    "cell_phone": null,
    "bank_name": "Scotiabank",
    "created_at": "2015-05-18T12:23:58.739-05:00",
    "updated_at": "2015-05-18T12:23:58.739-05:00",
    "custom_identifier": "asdf1234",
    "active": true,
    "address": {
          "address_1": "123 Main Street",
          "address_2": "Unit 4",
          "city": "Toronto",
          "province_code": "ON",
          "postal_code": "M1B 0B7"
    },
    "transaction_schedules": [],
    "financial_transactions": []
  }
}
```

This endpoint creates a new customer

### HTTP Request

`POST https://api.rotessa.com/v1/customers`

### Post Parameters

Parameter | Default | Description
--------- | ------- | -----------
name | - | Full name of customer
custom_identifier | - | Your own customer identifier. Must be unique.
email | - | Email address
home_phone | - | Home phone number
cell_phone | - | Cell phone number
bank_name | - | Bank name of customer
institution_number | - | Bank institution number
transit_number | - | Bank transit number
account_number | - | Bank account number
address | - | Customer address parameters.

