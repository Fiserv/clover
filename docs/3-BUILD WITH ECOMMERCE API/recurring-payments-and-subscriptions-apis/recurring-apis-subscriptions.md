---
title: "Recurring Payment APIs - Configure subscriptions"
slug: "recurring-apis-subscriptions"
excerpt: ""
hidden: false
createdAt: "Fri Jan 14 2022 20:25:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:34:24 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Ecommerce - Recurring APIs include two APIs—Plan and Subscription. The Subscriptions API for ecommerce lets you create subscriptions for plans that merchants can use on their Clover Merchant dashboard. Each subscription associates a customer to a plan to identify:

- Who is billed for the subscription?
- Whether credit card on file (COF) is present?
- What is the amount of the scheduled payment?
- What are the dates to take a scheduled payment?

Using this information, the subscription generates an invoice for each payment. 

A configured subscription is deactivated if the customer's invoice payment fails after five attempts. Invoice payments can fail if the customer's information or card data is invalid or missing, for example, if there is no card-on-file during payment.

## Work with the Subscriptions API

You can use subscriptions API to:

- [Create a subscription](https://docs.clover.com/docs/recurring-apis-subscriptions#create-a-subscription)
- [Retrieve a subscription](https://docs.clover.com/docs/recurring-apis-subscriptions#retrieve-a-subscription)
- [Edit a subscription](https://docs.clover.com/docs/recurring-apis-subscriptions#edit-a-subscription)
- [Cancel subscription](https://docs.clover.com/docs/recurring-apis-subscriptions#delete-a-subscription)

## Create a subscription

Define subscriptions for the set of plans to initiate automatic payments. See [Create subscription under a plan](https://docs.clover.com/reference/createsubscription)  API for more information on creating a subscription.

### Prerequisites

- Customer's universally unique identifier (UUID)
- Customer's card-on-file details

### Steps

1. Send a `POST` request to the `recurring/v1/plans/{planId}/subscriptions` endpoint, including the `planId` parameter.
2. Set the `Authorization` header as your OAuth-generated `access_token`.
3. Note the `subscriptionId` from the response to edit or delete the subscription.

### Required header parameters

| Field                  | Description                      | Required/Optional |
| :--------------------- | :------------------------------- | :---------------- |
| `Authorization`        | Bearer token                     | Required          |
| `X-Clover-Merchant-Id` | Clover merchant identifier (mId) | Required          |

### Required path parameters

| Field    | Description                                     | Required/Optional |
| :------- | :---------------------------------------------- | :---------------- |
| `planId` | Universally unique identifier (UUID) of a plan. | Required          |

### Request body parameters

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "h-2": "Required / Optional",
    "0-0": "`startDate`",
    "0-1": "Start date of the subscription plan in [ISO-8601 format](https://www.iso.org/iso-8601-date-and-time-format.html).  \nFor example, September 7, 2023, displays as 20230907 or with delimiters as 2023-09-07. Time displays in hours, minutes, and seconds, as 12:07:22.",
    "0-2": "Optional",
    "1-0": "`collectionMethod`",
    "1-1": "Method for collecting payment.  \nCurrently, `CHARGE_AUTOMATICALLY` is the only method allowed.",
    "1-2": "Required",
    "2-0": "`endDate`",
    "2-1": "End date of the subscription plan in [ISO-8601 format](https://www.iso.org/iso-8601-date-and-time-format.html).",
    "2-2": "Optional",
    "3-0": "`softDescriptor`",
    "3-1": "Information about the business that processed the charge.  \nSee [Set soft descriptors](doc:setting-soft-descriptors).",
    "3-2": "Optional",
    "4-0": "`note`",
    "4-1": "Subscription note. If available, it overrides the plan's note test.",
    "4-2": "Optional",
    "5-0": "`tipAmount`",
    "5-1": "Tip amount. If available, it overrides the plan's amount.",
    "5-2": "Optional",
    "6-0": "`amount`",
    "6-1": "Amount of the subscription. If available, it overrides the plan's amount.",
    "6-2": "Optional",
    "7-0": "`active`",
    "7-1": "Indicates whether the subscription is currently active.  \nValues:  \n  \n- True  \n- False",
    "7-2": "Optional",
    "8-0": "`taxRateUuids`",
    "8-1": "Universally unique identifiers (UUIDs) of the tax rate. If available, it overrides the plan's subscription.  \nLength: Maximum length of combined UUIDs is more than 255 characters.",
    "8-2": "Optional",
    "9-0": "`customerId`",
    "9-1": "Customer identifier (ID).",
    "9-2": "Required"
  },
  "cols": 3,
  "rows": 10,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


### Sample request and response

```curl cURL request
curl --request POST \ 
  --url 'https://sandbox.dev.clover.com/recurring/v1/plans/{planId}/subscriptions' \
  --header 'accept: application/json' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'X-Clover-Merchant-Id: {mId}'
  --header 'content-Type: application/json' \
  --data-raw '{
    "customerId" : "{customerId}",
    "collectionMethod" : "CHARGE_AUTOMATICALLY",
    "startDate": "2021-12-24T12:08:56.235-0700",
    "endDate": "2022-12-24T12:08:56.235-0700",
    "softDescriptor": { "dbaName": "ccc" },
    "taxRateUuids": [ "1ABC2DE3F4GHI", "2ABC4DE6F8JKL" ],
    "tipAmount": 7
}'
```
```json JSON response
{
  "id": "{subscriptionId}",
  "customerUuid": "{customerId}",
  "collectionMethod": "CHARGE_AUTOMATICALLY",
  "active": true,
  "tipAmount": 7,
  "amount": 200,
  "total": 200,
  "note": "This is a note",
  "softDescriptor": {
    "dbaName": "ccc"
  },
  "taxRateUuids": [
    "1ABC2DE3F4GHI",
    "2ABC4DE6F8JKL"
  ],
  "startDate": "2021-12-24@19:08:56.235+0000",
  "endDate": "2022-12-24@19:08:56.235+0000",
  "createdTime": "2021-12-03@22:04:15.896+0000",
  "modifiedTime": "2021-12-03@22:04:15.900+0000",
  "plan": {
    "name": "Recurring_plan 2",
    "amount": 200,
    "active": false,
    "interval": "MONTH",
    "intervalCount": 1,
    "note": "This is a note",
    "createdTime": "2021-10-16@17:39:08.000+0000",
    "modifiedTime": "2021-10-18@23:06:58.000+0000",
    "id": "{planId}",
   "merchantId": "A1B2C3D4EFG56",
  "developerAppId": "A1BCD2EFG34HI", 
    "object": "plan"
  },
  "object": "subscription"
}
```

## Retrieve a subscription

You can view only the subscriptions that you created. See the [Get subscription](https://docs.clover.com/reference/getsubscription) API for more information.

### Prerequisites

- Customer's universally unique identifier (UUID)
- Customer's card-on-file details

### Steps

1. Send a `GET` request to the `recurring/v1/subscriptions/{subscriptionId}` endpoint.
2. Set the `Authorization` header as your OAuth-generated `access_token`.

### Required header parameters

| Field                  | Description                      | Required/Optional |
| :--------------------- | :------------------------------- | :---------------- |
| `Authorization`        | Bearer token                     | Required          |
| `X-Clover-Merchant-Id` | Clover merchant identifier (mId) | Required          |

### Required path parameters

| Field            | Description                                                       | Required/Optional |
| :--------------- | :---------------------------------------------------------------- | :---------------- |
| `subscriptionId` | Universally unique identifier (UUID) of a subscription in a plan. | Required          |

### Sample request and response

```curl cURL request
curl --request GET \
  --url 'https://sandbox.dev.clover.com/recurring/v1/subscriptions/{subscriptionId}' \
  --header 'accept: application/json' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'X-Clover-Merchant-Id: {mId}' \
  --header 'content-Type: application/json' \
}'
```
```json JSON response
{
  "id": "{subscriptionId}",
  "customerUuid": "{customerUuid}",
  "collectionMethod": "CHARGE_AUTOMATICALLY",
  "active": false,
  "amount": 200,
  "total": 200,
  "note": "This is a note",
  "additionalCharges": [],
  "startDate": "2021-10-21@21:08:04.000+0000",
  "createdTime": "2021-10-21@21:08:04.000+0000",
  "modifiedTime": "2021-10-21@21:08:04.000+0000",
  "plan": {
    "name": "Recurring_plan 2",
    "amount": 200,
    "active": false,
    "interval": "MONTH",
    "intervalCount": 1,
    "note": "This is a note",
    "createdTime": "2021-10-16@17:39:08.000+0000",
    "modifiedTime": "2021-10-18@23:06:58.000+0000",
    "id": "{planId}",
    "merchantId": "{mId}",
    "developerAppId": "{deAppId}",
    "object": "plan"
  },
  "object": "subscription"
}
```

## Retrieve all subscriptions

You can view the list of all subscriptions for a merchant. See the [Get all subscriptions](https://docs.clover.com/reference/getallsubscriptions) API for more information.

### Steps

1. Send a `GET` request to the `recurring/v1/subscriptions` endpoint, including the `subscriptionId` path parameter.
2. Set the `Authorization` header as your OAuth-generated `access_token`.

### Required header parameters

| Field                  | Description                      | Required/Optional |
| :--------------------- | :------------------------------- | :---------------- |
| `Authorization`        | Bearer token                     | Required          |
| `X-Clover-Merchant-Id` | Clover merchant identifier (mId) | Required          |

### Sample request and response

```curl cURL request
curl --request GET \
--url 'https://sandbox.dev.clover.com/recurring/v1/subscriptions' \
--header 'X-Clover-Merchant-Id: {mId}'\
--header 'accept: application/json' \
--header 'Authorization: Bearer {access_token}' \
```
```json JSON response
[
  {
    "id": "{subscriptionId}",
    "customerUuid": "{customerUuid}",
    "collectionMethod": "CHARGE_AUTOMATICALLY",
    "active": true,
    "amount": 212,
    "additionalCharges": [],
    "startDate": "2023-12-16T00:00:00.000+0000",
    "lastRunDate": "2023-12-16T00:00:04.000+0000",
    "createdTime": "2023-12-15T11:22:26.000+0000",
    "modifiedTime": "2023-12-16T00:11:03.000+0000",
    "plan": {
      "name": "tete",
      "amount": 212,
      "active": true,
      "interval": "WEEK",
      "intervalCount": 2,
      "createdTime": "2023-12-15T11:20:17.000+0000",
      "modifiedTime": "2023-12-15T11:20:17.000+0000",
      "id": "KA5KQNVR9B8JT",
      "merchantId": "{mId}"
      "developerAppId": "{deAppId}",
      "object": "plan"
    },
    "object": "subscription"
  },
  {
    "id": "{subscriptionId}",
    "customerUuid": "{customerUuid}",
    "collectionMethod": "CHARGE_AUTOMATICALLY",
    "active": true,
    "amount": 21,
    "additionalCharges": [],
    "startDate": "2023-11-21T00:00:00.000+0000",
    "lastRunDate": "2023-11-21T01:00:28.000+0000",
    "createdTime": "2023-11-20T09:42:09.000+0000",
    "modifiedTime": "2023-11-21T01:04:13.000+0000",
    "plan": {
      "name": "plann",
      "amount": 21,
      "active": true,
      "interval": "YEAR",
      "intervalCount": 2,
      "createdTime": "2023-11-20T09:18:23.000+0000",
      "modifiedTime": "2023-11-20T09:18:23.000+0000",
      "id": "KGAK0626DY5YT",
      "merchantId": "{mId}",
      "developerAppId": "{deAppId}",
      "object": "plan"
    },
    "object": "subscription"
  },
  {
    "id": "{subscriptionId}",
    "customerUuid": "{customerUuid}",
    "collectionMethod": "CHARGE_AUTOMATICALLY",
    "active": true,
    "amount": 21,
    "additionalCharges": [],
    "startDate": "2023-11-21T09:18:23.000+0000",
    "endDate": "2024-11-20T09:18:23.000+0000",
    "lastRunDate": "2023-11-21T01:00:28.000+0000",
    "createdTime": "2023-11-20T09:22:05.000+0000",
    "modifiedTime": "2023-11-21T01:02:53.000+0000",
    "plan": {
      "name": "plann",
      "amount": 21,
      "active": true,
      "interval": "YEAR",
      "intervalCount": 2,
      "createdTime": "2023-11-20T09:18:23.000+0000",
      "modifiedTime": "2023-11-20T09:18:23.000+0000",
      "id": "{subscriptionId}",
      "merchantId": "{mId}",
      "developerAppId": "{deAppId}",
      "object": "plan"
    },
    "object": "subscription"
  },
  {
    "id": "{subscriptionId}",
    "customerUuid": "{customerUuid}",
    "collectionMethod": "CHARGE_AUTOMATICALLY",
    "active": true,
    "amount": 214,
    "additionalCharges": [],
    "startDate": "2023-11-15T00:00:00.000+0000",
    "lastRunDate": "2023-12-12T01:00:02.000+0000",
    "createdTime": "2023-11-14T08:49:43.000+0000",
    "modifiedTime": "2023-12-12T01:00:11.000+0000",
    "plan": {
      "name": "plan07",
      "amount": 214,
      "active": true,
      "interval": "MONTH",
      "intervalCount": 1,
      "createdTime": "2023-11-01T05:06:16.000+0000",
      "modifiedTime": "2023-11-01T05:06:16.000+0000",
      "id": "52YGETCNV8VPG",
      "merchantId": "{mId}",
      "developerAppId": "{deAppId}",
      "object": "plan"
    },
    "object": "subscription"
  },
  {
    "id": "{subscriptionId}",
    "customerUuid": "{customerUuid}",
    "collectionMethod": "CHARGE_AUTOMATICALLY",
    "active": true,
    "amount": 214,
    "additionalCharges": [],
    "startDate": "2023-11-02T00:00:00.000+0000",
    "lastRunDate": "2023-11-29T00:01:10.000+0000",
    "createdTime": "2023-11-01T05:07:42.000+0000",
    "modifiedTime": "2023-11-29T00:09:29.000+0000",
    "plan": {
      "name": "plan07",
      "amount": 214,
      "active": true,
      "interval": "MONTH",
      "intervalCount": 1,
      "createdTime": "2023-11-01T05:06:16.000+0000",
      "modifiedTime": "2023-11-01T05:06:16.000+0000",
      "id": "52YGETCNV8VPG",
      "merchantId": "{mId}",
      "developerAppId": "{deAppId}",
      "object": "plan"
    },
    "object": "subscription"
  }
]

```

## Edit a subscription

You can edit the subscriptions that you created. See the [Edit a subscription](https://docs.clover.com/reference/update) API for more information. Subscription changes only impact invoices that are created after the subscription changes are made.

> 🚧 Important
> 
> If the customer payment method changes, you must revoke the existing card-on-file (COF) and add a new one. See ​​[Save a card for future transactions](https://docs.clover.com/docs/ecommerce-saving-card).

### Prerequisites

- Customer's universally unique identifier (UUID)
- Customer's card-on-file details

### Steps

1. Send a `PUT` request to the `recurring/v1/subscriptions/{subscriptionId} `endpoint, including the `subscriptionId` path parameter.
2. Set the `Authorization` header as your OAuth-generated `access_token`.

### Required header parameters

| Field                  | Description                      | Required/Optional |
| :--------------------- | :------------------------------- | :---------------- |
| `Authorization`        | Bearer token                     | Required          |
| `X-Clover-Merchant-Id` | Clover merchant identifier (mId) | Required          |

### Required path parameters

| Field            | Description                                                       | Required/Optional |
| :--------------- | :---------------------------------------------------------------- | :---------------- |
| `subscriptionId` | Universally unique identifier (UUID) of a subscription in a plan. | Required          |

### Editable fields

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Editable?",
    "0-0": "`active`",
    "0-1": "Yes",
    "1-0": "`amount`",
    "1-1": "Yes",
    "2-0": "`note`",
    "2-1": "Yes",
    "3-0": "`taxRateUuids`",
    "3-1": "Yes",
    "4-0": "`startDate`",
    "4-1": "Yes  \n**Note:** Only a future subscription's start date is editable.",
    "5-0": "`endDate`",
    "5-1": "Yes"
  },
  "cols": 2,
  "rows": 6,
  "align": [
    "left",
    "left"
  ]
}
[/block]


### Sample request and response

```curl cURL request
curl --request PUT \
  --url 'https://sandbox.dev.clover.com/recurring/v1/subsriptions/{subscriptionId}' \
  --header 'accept: application/json' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'content-Type: application/json' \
  --data-raw '{
    "note" : "This is a revised note"
}'
```
```json JSON response
{
  "id": "{subscriptionId}",
  "customerUuid": "{customerUuid}",
  "collectionMethod": "CHARGE_AUTOMATICALLY",
  "active": true,
  "amount": 100,
  "total": 100,
  "note": "This is a revised note",
  "additionalCharges": [],
  "startDate": "2021-10-15@22:40:24.000+0000",
  "lastRunDate": "2021-11-13@00:00:03.000+0000",
  "createdTime": "2021-10-15@22:40:24.000+0000",
  "modifiedTime": "2021-12-06@14:42:59.291+0000",
  "plan": {
    "name": "API Plan 001",
    "amount": 100,
    "active": true,
    "interval": "MONTH",
    "intervalCount": 1,
    "note": "This is a note",
    "createdTime": "2021-10-15@22:31:56.000+0000",
    "modifiedTime": "2021-10-15@22:31:56.000+0000",
    "id": "{planId}",
  "merchantId": "A1B2C3D4EFG56",
  "developerAppId": "A1BCD2EFG34HI",
    "object": "plan"
  },
  "object": "subscription"
}
```

## Cancel a subscription

You can only cancel subscriptions that you created. See [Delete subscription](https://docs.clover.com/reference/delete) for more information on deleting a subscription. 

### Prerequisites

- Customer's universally unique identifier (UUID)
- Customer's card-on-file details

### Steps

1. Send a `PUT` request to the `recurring/v1/subscriptions/{subscriptionId} `endpoint, including the `subscriptionId` path parameter.
2. Set the `Authorization` header as your OAuth-generated `access_token`.
3. Set the `"Active":` field to `false`.

### Required header parameters

| Field                  | Description                      | Required/Optional |
| :--------------------- | :------------------------------- | :---------------- |
| `Authorization`        | Bearer token                     | Required          |
| `X-Clover-Merchant-Id` | Clover merchant identifier (mId) | Required          |

### Required path parameters

| Field            | Description                                                       | Required/Optional |
| :--------------- | :---------------------------------------------------------------- | :---------------- |
| `subscriptionId` | Universally unique identifier (UUID) of a subscription in a plan. | Required          |

### Sample request and response

```curl cURL request
curl --request PUT \
  --url 'https://sandbox.dev.clover.com/recurring/v1/subsriptions/{subscriptionId}' \
  --header 'accept: application/json' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'content-Type: application/json' \
  --data-raw '{
    "active" : "false" 
}'
```
```json JSON response
{
  "id": "{subscriptionId}",
  "customerUuid": "{customerUuid}",
  "collectionMethod": "CHARGE_AUTOMATICALLY",
    "active": false,
  "amount": 100,
  "total": 100,
  "note": "This is a note",
  "additionalCharges": [],
  "startDate": "2021-10-18@19:27:16.000+0000",
  "lastRunDate": "2021-11-16@00:00:01.000+0000",
  "createdTime": "2021-10-18@19:27:16.000+0000",
  "modifiedTime": "2021-12-06@14:54:00.973+0000",
  "plan": {
    "name": "API Plan 001",
    "amount": 100,
    "active": true,
    "interval": "MONTH",
    "intervalCount": 1,
    "note": "This is a note",
    "createdTime": "2021-10-15@22:31:56.000+0000",
    "modifiedTime": "2021-10-15@22:31:56.000+0000",
    "id": "{planId}",
 "merchantId": "A1B2C3D4EFG56",
  "developerAppId": "A1BCD2EFG34HI",
    "object": "plan"
  },
  "object": "subscription"
}
```

## See also

[Recurring Payments APIs - Configure Plans](doc:working-with-recurring-payments-and-subscriptions)
