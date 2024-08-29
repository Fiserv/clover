---
title: "Use expandable fields"
slug: "expanding-fields"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to use the `expand` query parameter to expand fields in Clover REST API responses, including which fields are expandable for a given resource and how to limit expansions."
  image: 
    - "https://files.readme.io/0c39a41-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Sep 07 2018 03:07:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:24 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n    <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


# Use the `expand` query parameter

You can use the `expand` query parameter to expand specific fields in the [API Reference](https://sandbox.dev.clover.com/api_docs). When you specify the fields to expand, the server retrieves the related fields and provides additional information as an expanded response, for example, related object nested within the parent.

> 🚧 IMPORTANT
> 
> Limit expansions to a maximum of three fields per API call. This allows us to continually provide quick API response times and reduce undue load.

# Example 1—`categories` for an inventory item are expanded

```curl Request for an item with categories expanded
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/{mId}/items/{Item_ID}?expand=categories" --header "Authorization: Bearer {API_Token}" | python -mjson.tool

{
    "id": "Z0EPYQ2R5TQ5Y",
    "hidden": false,
    "name": "My Food Truck",
    "alternateName": "",
    "code": "024463061095",
    "price": 150,
    "priceType": "FIXED",
    "defaultTaxRates": true,
    "unitName": "",
    "isRevenue": true,
    "categories": {
        "elements": [
            {
                "id": "MHH9XR2YXZ4T4",
                "name": "Food",
                "sortOrder": "0"
            }
        ]
    }
}
```

# Example 2—Multiple fields are expanded

To expand multiple fields in a request, separate the fields with a percent-encoded comma (`%2C`). In the following example, the response expands both the `tags` and `categories` fields.

```curl Request with expanded tags and categories fields
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/{mId}/items/{Item_ID}?expand=tags%2Ccategories" --header "Authorization: Bearer {API_Token}" | python -mjson.tool

{
    "cost": 0,
    "defaultTaxRates": true,
    "hidden": false,
    "id": "AK5ESN5YR8YWY",
    "isRevenue": true,
    "modifiedTime": 1432671908000,
    "name": "Pizza",
    "price": 1499,
    "priceType": "FIXED",
    "tags": {
        "elements": [
            {
                "id": "HYQ5Z74KS9E6W",
                "name": "Hot"
            }
        ]
    },
    "categories": {
        "elements": [
            {
                "id": "1JZPWY014VPEP",
                "name": "Italian",
                "sortOrder": 1
            },
            {
                "id": "0AJNZP04JXB4G",
                "name": "From the Oven",
                "sortOrder": 0
            }
        ]
    }
}
```

# Example 3—Two levels of fields are expanded

Two levels of fields can be expanded by specifying a dotted field path. For example, when querying an order, you can expand the `lineItems` in the order and the `taxRates` of each item.

```curl Request with nested fields expanded
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/{mId}/orders/{Order_ID}?expand=lineItems.taxRates" --header "Authorization: Bearer {API_Token}" | python -mjson.tool

...
{
    "clientCreatedTime": "1389389735000",
    "createdTime": "1389389736000",
    "employee": "id",
    "groupLineItems": "true",
    "id": "QGSS9P64219CM",
    "lineItems": {
        "elements": [
            {
                "createdTime": "1389389734000",
                "id": "VGQRH14DBR7JC",
                "name": "Bangers and Mash",
                "price": "1000",
                "printed": "true",
                "taxRates": {
                    "elements": [
                        {
                            "id": "VSA19B84VG1GT",
                            "isDefault": "true",
                            "name": "VAT",
                            "rate": "1500000"
                        },
                        {
                            "id": "BTHZCAXV6Z5R8",
                            "isDefault": "true",
                            "name": "Zero Tax",
                            "rate": "0"
                        }
                    ]
                }
            }
        ]
    },
    "manualTransaction": "false",
    "payType": "FULL",
    "state": "locked",
    "taxRemoved": "false",
    "total": "1000"
}
...
```
