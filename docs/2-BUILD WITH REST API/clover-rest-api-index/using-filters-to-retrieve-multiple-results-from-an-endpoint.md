---
title: "Use filters to retrieve multiple results from an endpoint"
slug: "using-filters-to-retrieve-multiple-results-from-an-endpoint"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to use the `in` operator with the `filter` query parameter in your query strings to retrieve multiple results from Clover customers, orders, payments, and other filterable endpoints."
  image: 
    - "https://files.readme.io/deaa3f6-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Jul 24 2020 21:34:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:23 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n  <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


## Use an`in` operator

Use an `in` operator with the `filter` parameter in your query strings to retrieve multiple results from the customers, orders, payments, and other filterable endpoints without having to fetch the items one at a time. 

## Query syntax

The full query syntax is `{{baseUrl}}/v3/merchants/{{mId}}/{{category}}?filter=id in ('UUID','UUID2','...UUID100')`

```text Query example
// Get a specific list of payments

https://sandbox.dev.clover.com/v3/merchants/J0W118EPG42WE1/payments?filter=id in ('CAB2S7XMQWXZ0',
'09C7AVKDN0Y6M','9DMB0EN7MTGG6','4RFE9NFRW3ZW2','0ZNYGJSGLAHE8', 'HASPS123ZSKPM','B3VFPNG321218',
'D1SVMJP0CY8HH','AWRE3VEAKRD1Q')
```

> 📘 NOTE
> 
> There is no minimum number of items for a request; however, Clover recommends retrieving no more than 100 items per query to avoid hitting limits and performance issues.
