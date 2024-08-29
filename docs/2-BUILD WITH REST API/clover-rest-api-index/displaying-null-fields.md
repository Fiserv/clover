---
title: "Display null fields"
slug: "displaying-null-fields"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to display all possible fields in Clover REST API responses by setting the `return_null_fields` query parameter to true."
  image: 
    - "https://files.readme.io/7707d31-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Sep 07 2018 03:08:47 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:24 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to the partner \ndoc. -->"
}
[/block]


[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n   <!--Latin America-->\n    <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


To have a response display all possible fields, set the `return_null_fields` query parameter to `true`.

```curl Response with null fields
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/{mId}/orders/{Order_ID}?return_null_fields=true"  --header "Authorization:Bearer {API_Token}" | python -mjson.tool

{
   "id": "[Order ID]",
   "currency": "USD",
   "employee": {
      "id": "0YN6A3WJ5BEZJ"
   },
   "total": 152,
   "title": "5",
   "note": null,
   "orderType": {
       "id": "2ZPZHQG2Z64NM",
       "labelKey": null,
       "label": null,
       "taxable": null,
       "isDefault": null,
       "isDeleted": null
   },
   "taxRemoved": false,
   "isVat": false,
   "state": "locked",
   "manualTransaction": true,
   "groupLineItems": true,
   "testMode": false,
   "payType": null,
   "createdTime": 1373613867000,
   "clientCreatedTime": 1373613795000,
   "modifiedTime": 1373613868000,
   "serviceCharge": null
}
```
