# Transaction Schedules
## Create A Transaction Schedule

```shell
curl -X POST \
     -H 'Content-Type: application/json' \
     -H 'Authorization: Token token="sS0md0PLYj9sgQ6RJgN1nQ"' \
     -d '{"transaction_schedule": {"customer_id":1, "amount":100, "frequency":"Monthly", "process_date": "May 24, 2015", "comment":"Membership fees"}}' \
     http://api.lvh.me:3000/v1/transaction_schedules.json
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "amount": "100.00",
    "frequency": "Monthly",
    "process_date": "2015-05-24",
    "installments": null,
    "comment": "Membership fees",
    "next_process_date": "2015-05-24",
    "created_at": "2015-05-16T14:43:22.101-05:00",
    "updated_at": "2015-05-16T14:43:22.101-05:00",
    "financial_transactions": []
  }
}
```

This endpoint creates a transaction schedule for a customer.

### HTTP Request

`POST https://api.rotessa.com/v1/transaction_schedules`

### Post Parameters

Parameter | Default | Description
--------- | ------- | -----------
customer_id | - | ID of customer
amount | - | Amount for schedule
frequency | - | Frequecy of transaction. Valid values are as follows: 'Once', 'Weekly', 'Every Other Week', 'Monthly', 'Every Other Month', 'Quarterly', 'Semi-Annually', 'Yearly'
installments | - | The number of installments. If value is excluded, schedule is indefinite.
comment | - | Optional comment for schedule.


<aside class="success">
When creating schedules you must specify a process date of at least 2 business days in the future.
</aside>



