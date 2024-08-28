---
title: "Apply filters"
slug: "applying-filters"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to apply filters to collections in Clover JSON responses using the filter query parameter, supporting standard comparison operators, and specifying multiple filter parameters."
  image: []
  robots: "index"
createdAt: "Fri Sep 07 2018 03:07:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:23 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n      <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to the partner \ndoc. -->"
}
[/block]


You can filter  collections with the `filter` query parameter that supports standard comparison operators, such as `=`, `>=`, and `!=`. You can specify multiple `filter` parameters by joining `filter` statements with an ampersand (`&`).

```curl Request filtered by clientCreatedTime
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/{mId}/orders?filter=clientCreatedTime>=[unix-time]&filter=clientCreatedTime<=[unix-time]" --header "Authorization: Bearer {API_Token}" | python -mjson.tool
```

To determine the parameters that can be filtered for a given method, see the [API Reference](https://sandbox.dev.clover.com/api_docs). The filterable fields are also returned with the request in the `X-Clover-Allowed-Filter-Fields` header.

```curl Request filtered by total and payType
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/{mId}/orders?filter=total>1000&filter=payType!=FULL" --header "Authorization: Bearer {API_Token}" | python -mjson.tool

{
    "elements": [
        {
            "clientCreatedTime": 1401286267000,
            "createdTime": 1401286268000,
            "currency": "USD",
            "employee": {
                "id": "QT0DES4CXR572"
            },
            "groupLineItems": true,
            "href": "https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/8WAD6KV8D90KR",
            "id": "8WAD6KV8D90KR",
            "isVat": false,
            "manualTransaction": false,
            "modifiedTime": 1401286463000,
            "payType": "SPLIT_CUSTOM",
            "state": "locked",
            "taxRemoved": false,
            "testMode": false,
            "total": 5293
        },
        {
            "clientCreatedTime": 1400106245000,
            "createdTime": 1400106245000,
            "currency": "USD",
            "employee": {
                "id": "QT0DES4CXR572"
            },
            "groupLineItems": true,
            "href": "https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/0S0JJYG231462",
            "id": "0S0JJYG231462",
            "isVat": false,
            "manualTransaction": false,
            "modifiedTime": 1400106366000,
            "payType": "SPLIT_CUSTOM",
            "state": "locked",
            "taxRemoved": false,
            "testMode": false,
            "total": 2829
        }
    ],
    "href": "https://apisandbox.dev.clover.com/v3/merchants/{mId}/orders?filter=total%3E1000&filter=payType!%3DFULL&limit=100"
}
```
