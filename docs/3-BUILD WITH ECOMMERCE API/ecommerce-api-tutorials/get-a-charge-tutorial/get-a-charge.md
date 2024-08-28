---
title: "Get a charge"
slug: "get-a-charge"
excerpt: ""
hidden: false
metadata: 
  description: "The get a charge endpoint retrieves details of an existing charge previously created using the create a charge endpoint."
  image: []
  robots: "index"
createdAt: "Mon Jul 18 2022 22:03:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


The [Get a charge](ref:getchargescharge) endpoint retrieves details of an existing charge previously created using the [Create a charge](ref:createcharge) endpoint. To return a charge, use the charge identifier (`chargeId`) that was returned from the create a charge request. a `ChargeId` is also returned when a charge is first created or if it is refunded.

## Request example

The following is a sample request when issuing the [Get a charge](ref:getchargescharge) endpoint:

```curl
curl --request GET \
     --url 'https://scl-sandbox.dev.clover.com/v1/charges/6CK2MJSF87X2M' \
     --header 'Accept: application/json'\
```

## Path parameter

The following table describes the path parameter to use with the [Get a charge](ref:getchargescharge) endpoint:

| Object     | Type   | Description                                                                        |
| :--------- | :----- | :--------------------------------------------------------------------------------- |
| `chargeId` | string | Required. Universally unique identifier (UUID) of the charge you want to retrieve. |

## Query parameter

The following table describes the query parameter to use when using the [Get a charge](ref:getchargescharge) endpoint:

| Object   | Type             | Description                                                           |
| :------- | :--------------- | :-------------------------------------------------------------------- |
| `expand` | array of strings | Indicates the fields to display in  response to expanding the fields. |

## Response example

The following is a sample response when running [Get a charge](ref:getchargescharge) endpoint:

```java JSON
{
  "object": "list",
  "url": "/v1/charges",
  "data": [
    {
      "id": "1AB2CDEF34G5H",
      "amount": 214,
      "currency": "usd",
      "created": 123456789123,
      "captured": false,
      "ref_num": 987654321,
      "auth_code": "123456",
      "order": A1BCDD3EF4JKL,
      "outcome": {
        "network_status": "approved_by_network",
        "type": "authorized"
      },
      "paid": true,
      "status": "succeeded",
      "source": {
        "id": "clv_1AAAAAAbCdefJK2l3MnoPQ4r",
        "brand": "DISCOVER",
        "first6": “123456,
        "last4": “4321”
      },
      "amount_captured": 214
    }
```

## Responses

The following table describes the possible responses when running the Get a charge endpoint:

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
    "0-3": "Returns the charge object with any captured value set to `true`.",
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
    "7-3": "Returned error type:  \n- `api_connection_error`  \n- `api_error`  \n- `authentication_error`  \n- `card_error`  \n- `idempotency_error`  \n- `invalid_request_error`  \n- `rate_limit_error`"
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
