---
title: "Create a card token"
slug: "create-a-card-token"
excerpt: ""
hidden: true
createdAt: "Wed Jul 24 2024 09:27:53 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Aug 06 2024 06:49:16 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

A card token is a unique, single-use code that represents a customer’s credit card details. It securely processes payments without exposing the actual card information or directly handling sensitive card information.

# Prerequisites

1. Set up a [sandbox developer account](https://docs.clover.com/docs/setup-clover-sandbox-account).
2. [Create an app in the sandbox](https://docs.clover.com/docs/creating-a-sandbox-app). See also [Ecommerce app permissions](https://docs.clover.com/docs/ecommerce-app-permissions).

# Steps

1. [Generate a PAKMS key](https://docs.clover.com/docs/ecommerce-generating-a-card-token#generate-a-pakms-key).
2. Send a POST request to the `/v1/tokens` endpoint. See [Create a card token](https://docs.clover.com/reference/create-card-token).
3. Enter information in the required fields.

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "h-2": "Require/Optional",
    "0-0": "`number`",
    "0-1": "Card primary account number (PAN). To minimize your app's payment card industry (PCI) compliance burden, use `encrypted_pan` instead.",
    "0-2": "Required",
    "1-0": "`encrypted_pan`",
    "1-1": "Encrypted card primary account number (PAN). ",
    "1-2": "Optional",
    "2-0": "`exp_month`",
    "2-1": "Card expiration month in 2-digit format.  \nFormat: mm",
    "2-2": "Required",
    "3-0": "`exp_year`",
    "3-1": "Card expiration year in 2- or 4-digit format.  \nFormat: yy or yyyy",
    "3-2": "Required",
    "4-0": "`cvv`",
    "4-1": "Card verification value (CVV). A 3-digit value printed on a card.",
    "4-2": "Required",
    "5-0": "`last4`",
    "5-1": "Last 4 numbers of the primary account number.",
    "5-2": "Optional",
    "6-0": "`first6`",
    "6-1": "First 6 numbers of the primary account number.",
    "6-2": "Optional",
    "7-0": "`country`",
    "7-1": "2-character country code.",
    "7-2": "Optional",
    "8-0": "`brand`",
    "8-1": "Card brand.",
    "8-2": "Optional",
    "9-0": "`name`",
    "9-1": "Cardholder's full name on the card.",
    "9-2": "Optional",
    "10-0": "`address_line1`",
    "10-1": "First line of the address. Can include the street address, PO box, or company name.",
    "10-2": "Optional",
    "11-0": "`address_line2`",
    "11-1": "Second line of the address. Can include the apartment, suite, unit, or building number.",
    "11-2": "Optional",
    "12-0": "`address_city`",
    "12-1": "City of the customer address. Can include district, suburb, town, or village.",
    "12-2": "Optional",
    "13-0": "`address_state`",
    "13-1": "State of the customer address. Can include county, province, or region.",
    "13-2": "Optional",
    "14-0": "`address_zip`",
    "14-1": "State of the customer address. Can include county, province, or region.",
    "14-2": "Optional",
    "15-0": "`address_country`",
    "15-1": "Billing address country, if provided.",
    "15-2": "Optional",
    "16-0": "`apikey`",
    "16-1": "Universally unique identifier (ID) of the API.",
    "16-2": "Required"
  },
  "cols": 3,
  "rows": 17,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


A single-use card token is returned. The token is alphanumeric and begins with clv\_. Example: clv_1ABCDefgHI23jKL4m5nOPqR

4. Use the card token for a single payment for [create a charge](https://docs.clover.com/reference/createcharge) or [pay for an order](https://docs.clover.com/reference/postordersidpay) endpoint.

## Request example

```Text cURL
curl --request POST \
     --url https://token-sandbox.dev.clover.com/v1/tokens \
     --header 'accept: application/json' \
     --header 'apikey: 7aacxxxx-xxxx-xxxx-xxxx-xxxxxxxxcae2' \
     --header 'content-type: application/json' \
     --data '
{
  "card": {
    "brand": "MC",
    "number": "5000-0000-0000-1236",
    "exp_month": "12",
    "exp_year": "2025",
    "cvv": "121"
  }
}
'
```

## Response example

```Text json
{
  "id": "clv_1ABCDefgHI23jKL4m5nOPqR",
  "object": "token",
  "card": {
    "exp_month": "12",
    "exp_year": "2025",
    "first6": "542418",
    "last4": "3333",
    "brand": "VISA"
  }
}
```
