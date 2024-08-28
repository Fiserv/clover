---
title: "Get charges"
slug: "get-charges"
excerpt: ""
hidden: false
metadata: 
  description: "The get charges endpoint retrieves details of existing charges previously created using the create a charge endpoint."
  image: []
  robots: "index"
createdAt: "Mon Jul 18 2022 22:07:12 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 12 2024 12:04:22 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<!--JIRA DS-6034; Added query parameters 7.12.2024-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The [Get charges](ref:getcharges) endpoint retrieves details of existing charges previously created using the [Create a charge](ref:createcharge) endpoint.

## Request example

The following is a sample request when issuing the [Get charges](ref:getcharges) endpoint:

```curl
curl --request GET \
     --url https://scl-sandbox.dev.clover.com/v1/charges \
     --header 'Accept: application/json' \
     --header 'Authorization: Bearer ab867xxxx-xxxx-xxxx-xxxx-xxxxxxxxcae2'
```

# Query Parameters

The following table describes the query parameters to use with the [Get charges](ref:getcharges) endpoint:

[block:parameters]
{
  "data": {
    "h-0": "Object",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "`created`",
    "0-1": "string",
    "0-2": "Displays results based on an open or closed-ended date and time range. Each filter part requires the parameter name, such as created or status_transitions, a comparison operator (`gt, gte, lt, or lte`), and a date-time or `Unix timestamp` (in milliseconds).  \nThe query string uses one of the following formats: {`parameterName}.{comparisonOperator`}=`yyyy-MM-dd HH:mm:ss`  \nor  \n{`parameterName`}.{`comparisonOperator`}={`timestamp`}  \nFor example, to filter the results for objects created after January 12, 2021 but before January 15 at 3 PM, add the following to the request: `created.gt=2021-01-12` & `created.lte=2021-01-15 15:00:00`.",
    "1-0": "`customer`",
    "1-1": "string",
    "1-2": "Returns charges associated with the provided customer ID o `customerId`.",
    "2-0": "`ending_before`",
    "2-1": "string",
    "2-2": "Cursor used in pagination. The ending_before object ID sets your place in the list. For example, if you receive 100 objects in a list starting with obj_bar, add ending_before=obj_bar in your subsequent request to retrieve the previous page of the list.",
    "3-0": "`expand`",
    "3-1": "array of strings",
    "3-2": "Additional information provided as an expanded response, for example, a related object nested within the parent. See [Use expandable fields.](https://docs.clover.com/docs/expanding-fields).",
    "4-0": "`limit`",
    "4-1": "integer",
    "4-2": "Number of objects returned by the request, ranging between 1 and 100.  \nDefault: 10",
    "5-0": "`starting_after`",
    "5-1": "string",
    "5-2": "Cursor used in pagination. The starting_after object ID sets your place in the list. For example, if you receive 100 objects in a list starting with obj_foo, add starting_after=obj_foo in your subsequent request to retrieve the next page of the list.",
    "6-0": "`threeds_validation_result`",
    "6-1": "string",
    "6-2": "EMV® 3-D Secure (3DS) authentication result. 3-D Secure is a protocol that provides an additional security layer for online credit and debit card-not-present (CNP) transactions.",
    "7-0": "`is_threeds`",
    "7-1": "string",
    "7-2": "Indicates whether the transaction is 3-D Secure authenticated."
  },
  "cols": 3,
  "rows": 8,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Created Option parameters

The following options appear when you select the `OPTION 1` under the `created` parameter. 

| Object | Type      | Description                                                                            |
| :----- | :-------- | :------------------------------------------------------------------------------------- |
| `gt`   | date-time | Displays results when the created field is greater than the current value.             |
| `gte`  | date-time | Displays results when the created field is greater than or equal to the current value. |
| `lt`   | date-time | Displays results when the created field is less than the current value.                |
| `lte`  | date-time | Displays results when the created field is less than or equal to the current value.    |

## Response example

The following is a sample response when running the [Get charges](ref:getcharges) endpoint:

```java JSON
{
  "object": "list",
  "url": "/v1/charges",
  "data": [
    {
      "id": "WBKGFT6X1VB1G",
      "amount": 214,
      "currency": "usd",
      "created": 1719882650000,
      "captured": false,
      "customer": "ADFRQ4R2YAYBY",
      "ref_num": "1287124121",
      "auth_code": "446057",
      "order": "WFCWS95Z8E4GR",
      "outcome": {
        "network_status": "approved_by_network",
        "type": "authorized"
      },
      "paid": true,
      "status": "succeeded",
      "source": {
        "id": "clv_1T7xxxx-xxxx-xxxx-xxxx-xxxxxxxxcae2",
        "brand": "DISCOVER",
        "first6": "601136",
        "last4": "6668"
      },
      "amount_captured": 214
    },
    {
      "id": "3QYJA61J9YYRY",
      "amount": 212,
      "currency": "usd",
      "created": 1719619573000,
      "captured": false,
      "customer": "AEJPTN7HH3RY2",
      "ref_num": "484331764",
      "auth_code": "482883",
      "order": "ZZVRJB0J7ZGPC",
      "outcome": {
        "network_status": "approved_by_network",
        "type": "authorized"
      },
      "paid": true,
      "status": "succeeded",
      "source": {
        "id": "clv_1T7xxxx-xxxx-xxxx-xxxx-xxxxxxxxcae2",
        "brand": "DISCOVER",
        "first6": "651000",
        "last4": "0810"
      },
      "amount_captured": 212
    }
  ]
}
```

## Responses

The following table describes the possible responses when running the [Get charges](https://docs.clover.com/reference/getcharges) endpoint:

[block:parameters]
{
  "data": {
    "h-0": "Message",
    "h-1": "Description",
    "h-2": "Variable",
    "h-3": "Description",
    "0-0": "`200`",
    "0-1": "string",
    "0-2": "",
    "0-3": "Returns the charge object with any captured value set to true.",
    "1-0": "`400 Bad Request`",
    "1-1": "string",
    "1-2": "charge",
    "1-3": "Returns when a card-related error occurs. Indicates the unique ID of the failed charge.",
    "2-0": "`400 Bad Request`",
    "2-1": "string",
    "2-2": "code",
    "2-3": "Returns additional information about the error that you can use to provide user-friendly handling of the issue.",
    "3-0": "`400 Bad Request`",
    "3-1": "string",
    "3-2": "decline_code",
    "3-3": "Returns when a card issuer declined the transaction. Includes the reason for the decline if specified by the card issuer.",
    "4-0": "`400 Bad Request`",
    "4-1": "string",
    "4-2": "doc_url",
    "4-3": "Returns a link for more information about the reported error code.",
    "5-0": "`400 Bad Request`",
    "5-1": "string",
    "5-2": "message",
    "5-3": "Provides detailed information about the error code. For card-related errors, use this information to inform users.",
    "6-0": "`400 Bad Request`",
    "6-1": "string",
    "6-2": "param",
    "6-3": "If the error is related to a specific parameter, this value lists the parameter. You can inform users of a particular issue in the entered card information.",
    "7-0": "`400 Bad Request`",
    "7-1": "string",
    "7-2": "type",
    "7-3": "Returned error type:  \n  \n- `api_connection_error`  \n- `api_error`  \n- `authentication_error`  \n- `card_error`  \n- `idempotency_error`  \n- `invalid_request_error`  \n- `rate_limit_error`"
  },
  "cols": 4,
  "rows": 8,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]
