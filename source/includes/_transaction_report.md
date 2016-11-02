# Transaction Report

The transaction report endpoint is the main interface by which your system can determine the current state of payments processed by Rotessa. The transaction report is limited to transcations 3 years into the futre or 1000 transactions, whichever comes first.

## Show Transaction Report
The endpoint provides 3 parameters which can be queried.


```shell
curl -X GET \
     -H 'Content-Type: application/json' \
     -H 'Authorization: Token token="sS0md0PLYj9sgQ6RJgN1nQ"' \
     -d '{{"start_date":'2017-05-12', "end_date":"2017-06-12", "filter":"All"}' \
     https://client.rotessa.com/v1/transaction_report.json
```

> The above command returns JSON structured like this:

```json
{
  "response": [
    {
      "id": 123456,
      "customer_id": 1,
      "custom_identifier": "Mikey"
      "amount": "120.00",
      "process_date": "2015-05-12",
      "status": "Pending",
      "status_reason": null,
      "transaction_schedule_id": 1,
      "created_at": "2015-05-12T23:04:00.000-05:00",
      "updated_at": "2015-05-12T23:04:00.000-05:00"
    },
    {
      "id": 123457,
      "customer_id": 1,
      "custom_identifier": "Mikey"
      "amount": "120.00",
      "process_date": "2015-05-19",
      "status": "Approved",
      "status_reason": null,
      "transaction_schedule_id": 2,
      "created_at": "2015-05-28T23:36:50.000-05:00",
      "updated_at": "2015-05-28T23:40:57.000-05:00"
    },
    {
      "id": 123458,
      "customer_id": 1,
      "custom_identifier": "Mikey"
      "amount": "120.00",
      "process_date": "2015-06-02",
      "status": "Future",
      "status_reason": null,
      "transaction_schedule_id": 3,
      "created_at": null,
      "updated_at": null
    },
    {
      "id": 123459,
      "customer_id": 1,
      "custom_identifier": "Mikey"
      "amount": "120.00",
      "process_date": "2015-06-09",
      "status": "Future",
      "status_reason": null,
      "transaction_schedule_id": 4,
      "created_at": null,
      "updated_at": null
    },

```


### HTTP Request

`POST https://api.rotessa.com/v1/transaction_report`


Parameter | Description
--------- | -------
start_date | The earliest process date of the list of transactions.
end_date | The last process date of the list of transactions. Optional
status | Filter by the given financial status of the transactions.

The `status` parameter can be one of the following values.

Parameter | Description
--------- | -------
'All' | Return all the transactions. This is the default value.
'Pending' | Only pending transactions. These are transactions still being processed by Rotessa.
'Approved' | Only approved transactions. These are considered successful transactions.
'Declined' | Only declined transactions. These are failed transactions.
'Chargeback' | Only chargeback transactions. These are failed transactions.


