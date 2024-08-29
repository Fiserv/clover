---
title: "Capture a charge"
slug: "capture-a-charge-tutorial"
excerpt: ""
hidden: false
metadata: 
  description: "Use the capture a charge endpoint to retrieve details of an existing charge, previously created using the create a charge endpoint."
  image: []
  robots: "index"
createdAt: "Mon Jul 18 2022 23:18:36 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Use the [Capture a charge](ref:capturecharge) endpoint to retrieve details of an existing charge, previously created using the [Create a charge](ref:createcharge) endpoint. To return a charge, use the charge identifier (chargeId) from the create a charge request. `ChargeId` also returns when a charge is first created or refunded.

## Path parameters

Path parameter to use when capturing a charge:

| Object     | Type   | Description                                         | Required |
| :--------- | :----- | :-------------------------------------------------- | :------- |
| `chargeId` | string | Universally unique identifier (UUID) of the charge. | Required |

## Body parameters

Body parameters to use when capturing a charge:

[block:parameters]
{
  "data": {
    "h-0": "Object",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "`amount`",
    "0-1": "int64",
    "0-2": "Charge amount in the smallest monetary unit of the merchant's currency. If you do not specify an amount, the total of the original charge is captured.  \nFormat: Cents",
    "1-0": "`receipt_email`",
    "1-1": "string",
    "1-2": "Email address to which the charge receipt is sent. This value overrides any previously-specified email address for the charge.  \nNote: Receipts are not sent in the sandbox environment.",
    "2-0": "`level2`",
    "2-1": "object",
    "2-2": "Additional data for purchase card transactions (US only). See [Level 2 data](doc:understanding-level-2-data)."
  },
  "cols": 3,
  "rows": 3,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


### Request and response examples

Request and response samples when running [Capture a charge](ref:capturecharge):

```curl cURL Request
curl --request POST \
     --url' https://scl-sandbox.dev.clover.com/v1/charges/chargeId/capture' \
     --header 'Accept: application/json' \
     --header 'Authorization: Bearer ab86a5e8-48f3-b3bd-8c45-d415e9867833' \
     --header 'Content-Type: application/json'
     --header 'x-forwarded-for: {client_ip}' \
```
```json JSON Response
{
  "id": "1AB2CDEF3G4H",
  "amount": 10,
  "currency": "usd",
  "created": 1656626930000,
  "captured": false,
  "customer": "ABCDEF12G3H45",
  "ref_num": "218100500005",
  "auth_code": "OK0974",
  "order": "12A34BBCCDDEE",
  "outcome": {
    "network_status": "approved_by_network",
    "type": "authorized"
  },
  "paid": true,
  "status": "succeeded",
  "source": {
    "id": "clv_1ABCD23efghI45JklmN6o7p",
    "brand": "VISA",
    "first6": "123456",
    "last4": "1234"
  }
  }
```

## Responses

The following table describes the possible responses when running the capture a charge endpoint:

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
