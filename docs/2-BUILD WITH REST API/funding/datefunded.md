---
title: "Funding API—dateFunded"
slug: "datefunded"
excerpt: ""
hidden: false
metadata: 
  description: "The `dateFunded` endpoint in the Funding API returns available deposit information for a specific date."
  image: []
  robots: "index"
createdAt: "Wed Jun 08 2022 20:41:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 06 2024 00:12:26 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


# Description

The `dateFunded` endpoint returns available deposit information for a specific date.

## Endpoint

```html GET
GET v3/merchants/{mid}/reports/deposits/batch/{dateFunded}
```
```text HTTPS
https://clover.com/v3/merchants/{mId}/reports/deposits/batch/{dateFunded}
```
```curl
curl --location --request GET 'http://www.clover.com/v3/merchants/{mId}/reports/deposits/batch/{dateFunded}' \
--header 'Authorization: Bearer <Token>'
```

## Requests

### Path Parameter

| Name         | Type   | Description                      | Max Length    |
| :----------- | :----- | :------------------------------- | :------------ |
| `mId`        | String | Indicates the merchant's ID.     | 13 characters |
| `dateFunded` | Long   | Date the transaction was funded. |               |

## Responses

The following are the responses that might occur when running the `dateFunded` endpoint.

[block:parameters]
{
  "data": {
    "h-0": "Message",
    "h-1": "Description",
    "h-2": "Example",
    "0-0": "`200`",
    "0-1": "Indicates a valid response.",
    "0-2": "Refer to [200 response](doc:datefunded#200-response)",
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
    "4-1": "Indicates an invalid bearer token was provided when attempting to authorize funding details of a merchant `{mId}.`",
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


## 200 response

```html
{
    "dateFunded": 1635134400000,
    "startDate": 1635134400000,
    "endDate": 1635134400000,
    "amountSubmitted": 0,
    "transfers": 9,
    "amountTransferred": -15200,
    "paidByOthers": 0,
    "chargeBackDetails": {
        "rows": {
            "elements": [
                {
                    "name": "Reversals",
                    "majorCatCode": "3",
                    "amount": -300,
                    "count": 1,
                    "categoryKey": "com.clover.reporting.funding.cat.reversals"
                },
                {
                    "name": "Chargebacks",
                    "majorCatCode": "12",
                    "amount": -1500,
                    "count": 1,
                    "categoryKey": "com.clover.reporting.funding.cat.chargebacks"
                }
            ]
        },
        "amount": -1800
    },
    "feesDetails": {
        "rows": {
            "elements": [
                {
                    "name": "Fees",
                    "majorCatCode": "6",
                    "amount": -10000,
                    "count": 2,
                    "categoryKey": "com.clover.reporting.funding.cat.fees"
                },
                {
                    "name": "Processing Service Charges",
                    "majorCatCode": "11",
                    "amount": -500,
                    "count": 1,
                    "categoryKey": "com.clover.reporting.funding.cat.service_charge"
                },
                {
                    "name": "Adjustments",
                    "majorCatCode": "2",
                    "amount": -2400,
                    "count": 3,
                    "categoryKey": "com.clover.reporting.funding.cat.adjustments"
                },
                {
                    "name": "Interchange Charges",
                    "majorCatCode": "7",
                    "amount": -500,
                    "count": 1,
                    "categoryKey": "com.clover.reporting.funding.cat.interchange_charges"
                }
            ]
        },
        "amount": -13400
    },
    "taxDetails": {
        "rows": {
            "elements": []
        },
        "amount": 0
    }
}
```

# Examples

## North American merchants

The following is an example of the `dateFunded` endpoint for North America merchants:

```html
v3/merchants/TP5871RSSQ90Y/reports/deposits/batch/1638432000000
{
   "dateFunded":1638432000000,
   "startDate":1638432000000,
   "endDate":1638432000000,
   "amountSubmitted":251148,
   "transfers":120,
   "amountTransferred":31542,
   "paidByOthers":0,
   "chargeBackDetails":{
      "rows":{
         "elements":[
            
         ]
      },
      "amount":0
   },
   "feesDetails":{
      "rows":{
         "elements":[
            {
               "name":"Interchange Charges",
               "majorCatCode":"12",
               "amount":-172290,
               "count":87,
               "categoryKey":"com.clover.reporting.funding.cat.interchange_charges"
            },
            {
               "name":"Fees",
               "majorCatCode":"30",
               "amount":-41666,
               "count":21,
               "categoryKey":"com.clover.reporting.funding.cat.fees"
            },
            {
               "name":"Processing Service Charges",
               "majorCatCode":"13",
               "amount":-5650,
               "count":8,
               "categoryKey":"com.clover.reporting.funding.cat.service_charge"
            }
         ]
      },
      "amount":-219606
   },

    "taxDetails":{
       "rows":{
          "elements":[


                  ]
               },
               "amount":0
            }

         }
```
