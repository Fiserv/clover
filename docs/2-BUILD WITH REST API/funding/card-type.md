---
title: "Funding API—card_types"
slug: "card-type"
excerpt: ""
hidden: false
metadata: 
  description: "The **card_types** endpoint in the Funding API returns a report of the amount funded by credit card type (MC, AMEX, DISC, MC, VISA)."
  image: []
  robots: "index"
createdAt: "Wed Jun 08 2022 21:24:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 06 2024 00:13:12 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


# Description

The **card_types** endpoint returns a report of the amount funded by credit card type (American Express<sup>®</sup>, Discovery<sup>®</sup>, Mastercard<sup>®</sup> and Visa<sup>®</sup>).

## Endpoint

```html GET
GET v3/merchants/{mid}/reports/deposits/batch/{dateFunded}/card_types
```
```text HTTPS
https://clover.com/v3/merchants/{mId}/reports/deposits/batch/{dateFunded}/card_types
```
```curl
curl --location --request GET 'https://www.clover.com/v3/merchants/{mId}/reports/deposits/batch/{dateFunded}/card_types' \
--header 'Authorization: Bearer <Token>'
```

## Requests

### Path Parameter

| Name         | Type   | Description                  | Maximum Length |
| :----------- | :----- | :--------------------------- | :------------- |
| `mId`        | String | Indicates the merchant's ID. | 13 characters. |
| `dateFunded` | Long   | Date the was funded.         |                |

### Header

| Name         | Description                                                       |
| :----------- | :---------------------------------------------------------------- |
| Bearer Token | Authorization token required for getting deposits for the`{mId}.` |

## Responses

The following are the responses that might occur when running the `card_types` endpoint.

[block:parameters]
{
  "data": {
    "h-0": "Message",
    "h-1": "Description",
    "h-2": "Example",
    "0-0": "`200`",
    "0-1": "Indicates a valid response.",
    "0-2": "Refer to [200 response](doc:card-type#200-response)",
    "1-0": "`400`  \n(BadRequestException)",
    "1-1": "The request is invalid, and subsequent calls will continue to fail.",
    "1-2": "`{\n    \"message\": \"Platform Not Supported\"\n}`",
    "2-0": "`400`  \n(DomainException)",
    "2-1": "This occurred because of an incomplete/empty filter query parameter.",
    "2-2": "`{\n    \"message\": \"Please specify a time window for this query.\"\n}`",
    "3-0": "`400`  \n(ParseException)",
    "3-1": "This occurs if the filter query is not a timestamp.",
    "3-2": "`{\n    \"message\": \"Unable to parse filter: ''\"\n}`",
    "4-0": "`401`",
    "4-1": "Indicates an invalid bearer token was provided when attempting to authorize funding details of a merchant `'{mId}'.`",
    "4-2": "`{\n    \"message\": \"401 Unauthorized\"\n}`",
    "5-0": "`405`",
    "5-1": "Indicates an incorrect base URL.",
    "5-2": "`405 GET not allowed`",
    "6-0": "`500 `",
    "6-1": "This typically occurs if a query exceeds a time limit.",
    "6-2": "`Internal server Error`"
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


## 200 responses

### 200 response: North America

The following 200 response is for North American (NA) merchants.

```text
{
    "cardTypes": {
        "elements": [
            {
                "name": "UPI CREDIT",
                "amount": 12378,
                "productCode": "98"
            },
            {
                "name": "DISCOVER",
                "amount": 30012,
                "productCode": "3"
            }
        ]
    },
    "total": 42390
}
```

# Examples

## Card types

The following `card_types` example provides a breakdown by card type.

```html
v3/merchants/TP5871RSSQ90Y/reports/deposits/batch/1638432000000/card_types 

{
  "cardTypes": {
    "elements": [ {
        "name": "MASTR-CARD", 
        "amount": 46269, 
        "productCode": "1"
      }, {
        "name": "VISA", 
        "amount": 189749, 
        "productCode": "2"
      }, {
        "name": "DISCOVER", 
        "amount": 8867, 
        "productCode": "3"
      }, {
        "name": "AMEX ACQ", 
        "amount": 6263, 
        "productCode": "7"
      }
    ]
  }, 
  "total": 251148
}
```
