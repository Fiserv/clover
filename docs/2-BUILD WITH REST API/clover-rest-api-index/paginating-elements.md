---
title: "Add pagination requests"
slug: "paginating-elements"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to paginate Clover merchant data sets by adding query parameters, such as offset and limit, to your request to page through large result sets."
  image: 
    - "https://files.readme.io/b944e3c-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Sep 07 2018 03:08:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:24 GMT+0000 (Coordinated Universal Time)"
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


Clover merchant data sets can be very large. By default, REST API responses are returned 100 items at a time.

To ensure you are retrieving results as expected, add query parameters, such as `offset` and `limit`, to your request. These parameters can be used to page through large result sets. The default limit is 100 elements, and the hard limit is 1000. 

Offsets and limits cannot be used to paginate results in nested fields. If the result set for a nested field contains more than 100 items, the API limits the results to the first 100 items.

# Use `limit` and `offset`

The following example shows a request for three orders (`limit=3`) from a merchant's tenth order (`offset=10`).

```curl Request with limit and offset
curl --request GET \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders? \
limit=3&offset=10' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {auth_token}'
```

The response includes an array of order objects.

```json Sample response
{
  "elements": [ 
    {
      "href": "https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/VXQEY3VMTT74T", 
      "id": "VXQEY3VMTT74T",
      "currency": "USD",
      "paymentState": "OPEN",
      "taxRemoved": false,
      "isVat": false,
      "state": "open",
			...
    }, 
    {
      "href": "https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/KMAAH8QS60Z7A", 
      "id": "KMAAH8QS60Z7A", 
      "currency": "USD", 
      "paymentState": "OPEN", 
      "taxRemoved": false, 
      "isVat": false, 
      "state": "open", 
			...
    }, 
    {
      "href": "https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/9HWKT8NG6RA8A", 
      "id": "9HWKT8NG6RA8A", 
      "currency": "USD", 
      "paymentState": "OPEN", 
      "taxRemoved": false, 
      "isVat": false, 
      "state": "open", 
			...
    }
  ], 
  "http://sandbox.dev.clover.com/v3/merchants/7R56PZ0Z0EAB1/orders?filter=stateIS%20NOT%20NULL&offset=10&limit=3"

```
