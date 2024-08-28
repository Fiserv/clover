---
title: "Request inventory stock"
slug: "querying-inventory"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to request inventory stock in Clover by expanding the `itemStock` field when viewing items and updating the quantity field through item_stocks endpoints."
  image: 
    - "https://files.readme.io/414acef-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Sep 07 2018 22:24:11 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:24 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n     <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


The `quantity` field holds an item’s stock and is found by expanding `itemStock` when viewing items. This field can only be updated through [`item_stocks`](https://sandbox.dev.clover.com/api_docs/#inventory_ItemStocks) endpoints. The field supports whole or decimal numbers, both positive and negative.

```curl Request for stock of an item
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/{mId}/item_stocks/{Item_ID}" --header "Authorization: Bearer {API_Token}" | python -mjson.tool

{
  "item": {
    "id": "3Z29BX6C013XC"
  },
  "stockCount": 127,
  "quantity": 127
}
```

**Deprecated field**

The `stockCount` is a deprecated field that will always display `quantity` rounded to the nearest whole number. As a result, its use is discouraged. The following example shows how a decimal quantity value of `160.5` is rounded to `161` for the `stockCount` field.

```curl Update item stock with decimal quantity
$ cat /tmp/item_stocks.json
{
   "quantity": 160.5
}

$ curl -s -X POST "https://apisandbox.dev.clover.com/v3/merchants/{mId}/item_stocks/{Item_ID}" --header "Authorization: Bearer {API_Token}" --data "{Content from item_stocks.json}" | python -mjson.tool

{
  "item": {
    "id": "3Z29BX6C013XC"
  },
  "stockCount": 161,
  "quantity": 160.5
}
```
