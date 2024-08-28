---
title: "Recurring Payments APIs - Configure Plans"
slug: "working-with-recurring-payments-and-subscriptions"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to use Recurring Payments APIs to configure plans for merchants."
  image: []
  robots: "index"
createdAt: "Mon Oct 25 2021 19:13:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:32:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Ecommerce - Recurring APIs include two APIs -- Plan and Subscription. The Plans API for ecommerce lets you create recurring payment plans that merchants can use through their dashboards. With the Plans API, you can:

- Define a set of plans that lets customers initiate automatic payments.
- Set the fixed amount, periodic frequency, tax, convenience fees, tips, and so on for each plan.
- Include a consistent set of defined features in your apps and create several recurring payment plans.

## Work with the Plans API

You can use endpoints in the Plans API to:

- [Create a plan](https://docs.clover.com/docs/working-with-recurring-payments-and-subscriptions#create-a-plan)
- [Retrieve plans](https://docs.clover.com/docs/working-with-recurring-payments-and-subscriptions#retrieve-plans)
- [Search a plan](https://docs.clover.com/docs/working-with-recurring-payments-and-subscriptions#search-for-a-plan)
- [Edit a plan](https://docs.clover.com/docs/working-with-recurring-payments-and-subscriptions#edit-a-plan)
- [Deactivate a plan](https://docs.clover.com/docs/working-with-recurring-payments-and-subscriptions#deactivate-a-plan)

## Create a plan

[Create a plan](https://docs.clover.com/reference/create) lets your merchants define a set of plans to initiate automatic payments. You can create as many recurring payment plans as required.  
**Steps**

1. Send a `POST` request to the `recurring/v1/plans` endpoint.
2. Set the `Authorization` header as your OAuth-generated `access_token`.
3. Note the `id` (`planID`) to edit or delete the plan later.

### Required header parameters

| Field                  | Description                      | Required/Optional |
| :--------------------- | :------------------------------- | :---------------- |
| `authorization`        | Bearer token                     | Required          |
| `X-Clover-Merchant-Id` | Clover merchant identifier (mId) | Required          |

### Request body fields

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "h-2": "Required / Optional",
    "0-0": "`name`",
    "0-1": "Plan name. Cannot be null or blank.  \nLength:  \n  \n- Minimum 3 characters  \n- Maximum 127 characters",
    "0-2": "Required",
    "1-0": "`amount`",
    "1-1": "Plan amount",
    "1-2": "Required",
    "2-0": "`note`",
    "2-1": "Additional information or notes related to the plan.",
    "2-2": "Optional",
    "3-0": "`taxRateUuids`",
    "3-1": "Tax rate universally unique identifiers (UUIDs).",
    "3-2": "Optional",
    "4-0": "`tipAmount`",
    "4-1": "Amount paid in tips.",
    "4-2": "Optional",
    "5-0": "`interval`",
    "5-1": "Interval of the plan.  \nValues:  \n  \n- Day  \n- Week  \n- Month  \n- Year  \n  See the [Interval Matrix](https://docs.clover.com/docs/working-with-recurring-payments-and-subscriptions#interval-matrix)  table for details.",
    "5-2": "Required",
    "6-0": "`intervalCount`",
    "6-1": "Number of intervals in the plan.",
    "6-2": "Required"
  },
  "cols": 3,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


### Interval matrix

| UX Element    | Definition                           | API frequency | API interval |
| :------------ | :----------------------------------- | :------------ | :----------- |
| Daily         | Everyday                             | Day           | 1            |
| Weekly        | Every 7 days                         | Week          | 1            |
| Bi-weekly     | Every 14 days                        | Week          | 2            |
| Monthly       | Every month on the same date.        | Month         | 1            |
| Bi-monthly    | Every two months on the same date.   | Month         | 2            |
| Quarterly     | Every three months on the same date. | Month         | 3            |
| Four months   | Every four months on the same date.  | Month         | 4            |
| Semi-annually | Every six months on the same date.   | Month         | 6            |
| Annually      | Once a year on the same date.        | Year          | 1            |

### Sample request and response

```curl cURL request
curl  --request POST \
  --url 'https://sandbox.dev.clover.com/recurring/v1/plans' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'X-Clover-Merchant-Id: {mId}' \
  --header 'content-Type: application/json' \
  --data-raw '
{
    "name": "Monthly Plan",
    "amount": 1000, 
    "interval": "MONTH", 
    "intervalCount": 3, 
    "note": "This is your first plan",
    "taxRateUuids": [
        "1ABC2DE3F4GHI" 
    ],
    "tipAmount": 300
}
```
```json JSON response
{
  "name": "Monthly Plan",
  "taxRateUuids": [
    "1ABC2DE3F4GHI"
  ],
  "tipAmount": 300,
  "amount": 1000,
  "active": true,
  "interval": "MONTH",
  "intervalCount": 3,
  "note": "This is your first plan",
  "createdTime": "2023-09-19T10:02:59.476+0000",
  "modifiedTime": "2023-09-19T10:02:59.476+0000",
  "id": "JCYFCH8JS3YT2",
  "merchantId": "A1B2C3D4EFG56",
  "developerAppId": "A1BCD2EFG34HI",
  "object": "plan"
}
```

## Retrieve plans

You can retrieve plans to view plan details only for the plans that you created. See [Retrieve plans](https://docs.clover.com/reference/getplans) for more information on retrieving a recurring payment plan.

**Steps**

1. Send a `GET` request to the `recurring/v1/plans` endpoint, including the planId parameter.
2. Set the `Authorization` header as your OAuth-generated `access_token`.

### Required header parameters

| Field                  | Description                      | Required/Optional |
| :--------------------- | :------------------------------- | :---------------- |
| `authorization`        | Bearer token                     | Required          |
| `X-Clover-Merchant-Id` | Clover merchant identifier (mId) | Required          |

### Required path parameters

| Field    | Description                                     | Required/Optional |
| :------- | :---------------------------------------------- | :---------------- |
| `planId` | Universally unique identifier (UUID) of a plan. | Required          |

### Sample request and response

```curl cURL request
curl --request GET \
  --url 'https://sandbox.dev.clover.com/recurring/v1/plans/{planId}' \
  --header 'accept: application/json' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'X-Clover-Merchant-Id: {mId}'
  --header 'content-Type: application/json' \
```
```json JSON response
{
  "name": "Monthly Plan",
  "taxRateUuids": [
    "1ABC2DE3F4GHI"
  ],
  "tipAmount": 300,
  "amount": 1000,
  "active": true,
  "interval": "MONTH",
  "intervalCount": 1,
  "note": "This is a note",
  "createdTime": "2023-09-19T10:02:59.476+0000",
  "modifiedTime": "2023-09-19T10:02:59.476+0000",
  "id": "JCYFCH8JS3YT2",
  "merchantId": "A1B2C3D4EFG56",
  "developerAppId": "A1BCD2EFG34HI",
  "object": "plan"
}
```

## Search for a plan

You can search for a plan with specific features, such as interval and interval count. See [Get plan](https://docs.clover.com/reference/get) for more information.

**Steps**

1. Send a `GET` request to the `recurring/v1/plans` endpoint, including the `planId` parameter.
2. Set the `Authorization` header as your OAuth-generated `access_token`. 

### Required header parameters

| Field           | Description  | Required/Optional |
| :-------------- | :----------- | :---------------- |
| `authorization` | Bearer token | Required          |

### Required path parameters

| Field    | Description                                     | Required/Optional |
| :------- | :---------------------------------------------- | :---------------- |
| `planId` | Universally unique identifier (UUID) of a plan. | Required          |

### Sample request and response

The following example retrieves all plans that are set to a monthly frequency and an interval count of `1`. The list of plans meeting specified criteria is returned.

```curl cURL request
curl --request GET \
  --url 'https://sandbox.dev.clover.com/recurring/v1/plans?interval=MONTH&intervalCount=1' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'X-Clover-Merchant-Id: {mId}'
  --header 'content-Type: application/json' \
```
```json JSON response
curl --request GET \
    {
    "tipAmount": 300,
  "amount": 1000,
  "active": true,
  "interval": "MONTH",
  "intervalCount": 1,
  "note": "This is a note",
  "createdTime": "2023-09-19T10:02:59.476+0000",
  "modifiedTime": "2023-09-19T10:02:59.476+0000",
  "id": "JCYFCH8JS3YT2",
  "merchantId": "A1B2C3D4EFG56",
  "developerAppId": "A1BCD2EFG34HI",
  "object": "plan"
  },
  {
    "name": "Monthly Plan 2",
    "amount": 200,
    "active": false,
    "interval": "MONTH",
    "intervalCount": 1,
   ...
  },
  {
    "name": "Monthly API Plan",
    "amount": 100,
    "active": true,
    "interval": "MONTH",
    "intervalCount": 1,
    ...
  }
]
```

## Edit a plan

You can edit the plans that you created. See [Edit a plan](https://docs.clover.com/reference/editplan) for more information. The `interval` and `intervalCount` fields are not editable. To change these fields, you need to delete and recreate the plan.

**Steps**

1. Send a `PUT` request to the `recurring/v1/plans` endpoint, including  the `planId` parameter.
2. Set the `Authorization` header as your OAuth-generated `access_token`.

### Required header parameters

| Field                  | Description                      | Required/Optional |
| :--------------------- | :------------------------------- | :---------------- |
| `authorization`        | Bearer token                     | Required          |
| `X-Clover-Merchant-Id` | Clover merchant identifier (mId) | Required          |

### Required path parameters

| Field    | Description                                     | Required/Optional |
| :------- | :---------------------------------------------- | :---------------- |
| `planId` | Universally unique identifier (UUID) of a plan. | Required          |

### Editable fields

| Field           | Editable? |
| :-------------- | :-------- |
| `name`          | Yes       |
| `interval`      | No        |
| `intervalCount` | No        |
| `amount`        | Yes       |
| `tipAmount`     | Yes       |
| `note`          | Yes       |
| `taxRateUuids`  | Yes       |

### Sample request and response

```curl cURL request
curl --request PUT \ 
  --url 'https://sandbox.dev.clover.com/recurring/v1/plans/{planId}' \
  --header 'accept: application/json' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'X-Clover-Merchant-Id: {mId}'
  --header 'content-Type: application/json' \
  --data-raw '{
    "name": "Plan_name",
    "amount": "", 
    "active": true
}'
```
```json JSON response
{
  "name": "Recurring_plan 2",
  "amount": 200,
  "active": true,
  "interval": "MONTH",
  "intervalCount": 1,
  "note": "This is a note",
  "createdTime": "2023-09-19T10:02:59.476+0000",
  "modifiedTime": "2023-09-19T10:02:59.476+0000",
  "id": "JCYFCH8JS3YT2",
  "merchantId": "A1B2C3D4EFG56",
  "developerAppId": "A1BCD2EFG34HI",
  "object": "plan"
}
```

## Deactivate a plan

You can deactivate (cancel) plans you created if no active subscriptions are associated with them. See [Delete a plan](https://docs.clover.com/reference/editplan) for more information.

**Steps**

1. Send a `PUT` request to the `recurring/v1/plans` endpoint, including the planId parameter.
2. Set the `Authorization` header as your OAuth-generated `access_token`.
3. Set the `"active"`: field to `false`.

### Required header parameters

| Field                  | Description                      | Required/Optional |
| :--------------------- | :------------------------------- | :---------------- |
| `authorization`        | Bearer token                     | Required          |
| `X-Clover-Merchant-Id` | Clover merchant identifier (mId) | Required          |

### Required path parameters

| Field    | Description                                     | Required/Optional |
| :------- | :---------------------------------------------- | :---------------- |
| `planId` | Universally unique identifier (UUID) of a plan. | Required          |

### Sample request and response

```curl
curl --request PUT \ 
  --url 'https://sandbox.dev.clover.com/recurring/v1/plans/{planId}' \
  --header 'accept: application/json' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'X-Clover-Merchant-Id: {mId}'
  --header 'content-Type: application/json' \
  --data-raw '{
    "active": false
}'
```
```json JSON response
{
  "name": "Recurring_plan 2",
  "amount": 200,
  "active": false,
  "interval": "MONTH",
  "intervalCount": 1,
  "note": "This is a note",
  "createdTime": "2023-09-19T10:02:59.476+0000",
  "modifiedTime": "2023-09-19T10:02:59.476+0000",
  "id": "JCYFCH8JS3YT2",
  "merchantId": "A1B2C3D4EFG56",
  "developerAppId": "A1BCD2EFG34HI",
  "object": "plan"
}
```

## See also

[Recurring Payment APIs - Configure Subscriptions](doc:recurring-apis-subscriptions)
