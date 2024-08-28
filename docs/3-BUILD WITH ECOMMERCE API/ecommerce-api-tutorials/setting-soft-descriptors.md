---
title: "Set soft descriptors"
slug: "setting-soft-descriptors"
excerpt: ""
hidden: false
metadata: 
  description: "Soft descriptors let merchants provide customers with information about the business that processed a charge with the Ecommerce API."
  image: []
  robots: "index"
createdAt: "Wed Mar 24 2021 21:09:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Soft descriptors let merchants provide customers with information about the business that processed a charge with the Ecommerce API. These descriptors appear on the customer's card statements and can include the  doing business as (DBA) name, address, and contact information. 

## Confirm merchant availability

Some Clover merchants are unable to process soft descriptors, and attempts to include them will return a warning in these cases. Before requesting a charge, you can check if a merchant is able to use soft descriptors with the `/v3/merchants/{mId}/ecomm_payment_configs` or the [create a charge](https://docs.clover.com/reference/createcharge) endpoint. The response for a merchant that supports soft descriptors will include the following property.

```json
{
  "softDescriptors": {
    "supported": true
  }
}
```

## Parameters

The following table describes the `softDescriptors` parameter:

[block:parameters]
{
  "data": {
    "h-0": "Object",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "`dba_name`",
    "0-1": "string",
    "0-2": "This is the DBA (_Doing business as_) name. This could be a merchant name, product, or service. Limited to 38 alphanumeric characters.",
    "1-0": "`street`",
    "1-1": "string",
    "1-2": "This is the merchant's street address.",
    "2-0": "`city`",
    "2-1": "string",
    "2-2": "This is the merchant's city.",
    "3-0": "`region`",
    "3-1": "string",
    "3-2": "This is the merchant's state as a two-character postal abbreviation (US only).",
    "4-0": "`postal_code`",
    "4-1": "string",
    "4-2": "This is the merchant's postal code.",
    "5-0": "`country_code`",
    "5-1": "string",
    "5-2": "Merchant's country as a three-digit code (refer to the [Country code reference](doc:country-code-reference)).",
    "6-0": "`merchant_contact_info`",
    "6-1": "string",
    "6-2": "Merchant's phone number or email address. This is limited to thirteen characters for both Discover<sup>®</sup> and Visa<sup>®</sup> transactions."
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


## Add soft descriptors

When constructing a charge request, include the `soft_descriptor` object and any of the properties you want to appear on the statement, for example:

```json
{
    "amount": 3900,
    "currency": "usd",
    "source": "{cardToken}",
    "soft_descriptor": {
      "dba_name": "Clover",
      "street": "415 N Mathilda Ave",
      "city": "Sunnyvale",
      "region": "CA",
      "postal_code": "94085",
      "country_code": "840",
      "merchant_contact_info": "9015559928"
    }
}
```
