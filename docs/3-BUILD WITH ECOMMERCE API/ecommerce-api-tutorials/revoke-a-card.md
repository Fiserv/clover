---
title: "Revoke a card"
slug: "revoke-a-card"
excerpt: ""
hidden: true
createdAt: "Wed Aug 03 2022 22:28:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 18 2023 10:12:57 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Europe</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Use the [Revoke a card](ref:revokecard) to remove a `source` from a customer's profile.

## Request example

The following is a sample request when issuing a [Revoke a card](ref:revokecard) endpoint:

```curl
curl --request DELETE \
     --url https://scl-sandbox.dev.clover.com/v1/customers/customerId/sources/cardId \
     --header 'Accept: application/json' \
     --header 'Authorization: Bearer ab86a5e8-48f3-b3bd-8c45-d415e9867833'
```

## Request Parameters

The following table describes the request parameters to use when using the Revoke a card endpoint:

| Object       | Type   | Description                           |
| :----------- | :----- | :------------------------------------ |
| `customerId` | string | Required. Unique customer ID.         |
| `cardId`     | string | Required. UUID of the card to revoke. |

## Response example

The following is a sample response when issuing a [Revoke a card](ref:revokecard).

```java
{
  "deleted": true,
  "id": "ND2EFTHF8HM34",
  "object": "deletedcard"
}
```

## Responses

The following table describes the possible responses when running this endpoint:

[block:parameters]
{
  "data": {
    "h-0": "Message",
    "h-1": "Description",
    "h-2": "Variable",
    "h-3": "Description",
    "0-0": "`200`",
    "0-1": "string",
    "0-2": "charge",
    "0-3": "Returns the charge object with any captured value set to `true`.",
    "1-0": "`400`",
    "1-1": "string",
    "1-2": "code",
    "1-3": "Provides additional information about the error that you can use to provide user-friendly handling of the issue.",
    "2-0": "`400`",
    "2-1": "string",
    "2-2": "decline_code",
    "2-3": "Returned when a card issuer declines the transaction. This includes the reason for the decline, if specified by the card issuer.",
    "3-0": "`400`",
    "3-1": "string",
    "3-2": "doc_url",
    "3-3": "Returns a URL for more information about the reported error code.",
    "4-0": "`400`",
    "4-1": "string",
    "4-2": "message",
    "4-3": "Provides detailed information about the error code. For card-related errors, this information can be used to inform users.",
    "5-0": "`400`",
    "5-1": "string",
    "5-2": "param",
    "5-3": "If the error is related to a specific parameter, this value lists the parameter, so that you can inform users entering card information of a particular problem with their entry.",
    "6-0": "`400`",
    "6-1": "string",
    "6-2": "type",
    "6-3": "Returned error type:  \n- `api_connection_error`  \n- `api_error`  \n- `authentication_error`  \n- `card_error`  \n- `idempotency_error`  \n- `invalid_request_error`  \n- `rate_limit_error`"
  },
  "cols": 4,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]
