# Transaction Schedules

Transaction schedules are the method by which recurring or one time payments are scheduled in Rotessa for a customer. Payments require a schedule date, which must be at least 2 business days in the future, as well as a frequency.

Frequency | Description
--------- | -------
"Once" | One time payment.
"Weekly" | Every week.
"Every Other Week" | Every two weeks.
"Monthly" | Every month.
"Every Other Month" | Every two months.
"Quarterly" | Every 3 months.
"Semi-Annually" | Every six months.
"Yearly" | Once a year.

Transaction schedules have an optional installments parameter that allow you to schedule a set number of payments. To schedule payments indefinitely simply omit this parameter and Rotessa will continue withdrawing funds until the schedule is cancelled.

## Create A Transaction Schedule

```shell
curl -X POST \
     -H 'Content-Type: application/json' \
     -H 'Authorization: Token token="sS0md0PLYj9sgQ6RJgN1nQ"' \
     -d '{"transaction_schedule": {"customer_id":1, "amount":100, "frequency":"Monthly", "process_date": "May 24, 2015", "comment":"Membership fees"}}' \
     https://client.rotessa.com/v1/transaction_schedules.json
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



