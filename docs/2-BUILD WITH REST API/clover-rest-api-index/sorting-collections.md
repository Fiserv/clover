---
title: "Sort collections"
slug: "sorting-collections"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to sort collections in the Clover REST API JSON responses by adding the orderBy query parameter, specifying multiple fields separated by commas, and manually ordering by ascending or descending."
  image: 
    - "https://files.readme.io/b0c2549-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Sep 07 2018 03:06:46 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:23 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n    <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to the partner \ndoc. -->"
}
[/block]


Most JSON responses take the form of collections, which can be sorted by adding the `orderBy` query parameter. You can specify multiple fields by separating them with commas.

```curl Response ordered by modifiedTime and price
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/{mId}/items?orderBy=modifiedTime,price" --header "Authorization: Bearer {API_Token}" | python -mjson.tool

{
    "elements": [
        {
            "code": "",
            "defaultTaxRates": false,
            "hidden": false,
            "id": "V33H8XGTZCKNP",
            "isRevenue": true,
            "name": "Item Use",
            "price": 100,
            "priceType": "PER_UNIT",
            "unitName": "hr"
        },
        {
            "code": "",
            "defaultTaxRates": false,
            "hidden": false,
            "id": "EWKZEMNCBQQ9Y",
            "isRevenue": true,
            "name": "Nontax Item",
            "price": 100,
            "priceType": "FIXED",
            "unitName": "oz"
        },
...
```

The default sort order is descending by creation time. You can manually order by ascending or descending by inputting `%20ASC` or `%20DESC`, respectively.

```json Response by modifiedTime in ascending order
$ curl -s https://apisandbox.dev.clover.com/v3/merchants/{mId}/items?orderBy=modifiedTime%20ASC --header "Authorization: Bearer {API_Token}" | python -mjson.tool

{
  "elements": [ {
      "id": "1CF022RN5TGDM",
      "hidden": false,
      "name": "Pizza Slice",
      "price": 250,
      "priceType": "FIXED",
      "defaultTaxRates": true,
      "cost": 0,
      "isRevenue": true
    }, {
      "id": "SNGFTY41642NY",
      "hidden": false,
      "name": "Pork Rice Bowl with House Salad",
      "price": 1200,
      "priceType": "FIXED",
      "defaultTaxRates": true,
      "cost": 0,
      "isRevenue": true,
      "stockCount": 3
    },
...
```
