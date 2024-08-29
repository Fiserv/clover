---
title: "(TA token Pilot) Create a TransArmor token"
slug: "ta-token-pilot-create-a-transarmor-token"
excerpt: ""
hidden: true
metadata: 
  description: "Learn how to create TransArmor tokens in the Clover network for multi-pay and recurring payments."
  image: []
  robots: "index"
createdAt: "Wed Aug 07 2024 06:45:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Aug 14 2024 10:37:41 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--Add a top nav throughout the pilot doc content (v2.2: grayscale, no overlap)-->\n<div><!--div set-->\n <div class=\"top-container\">\n    <div class=\"topnav\">\n      <a href=\"https://docs.clover.com/docs/use-transarmor-token\">TransArmor token overview</a>\n      <a href=\"https://docs.clover.com/docs/ta-token-pilot-create-a-transarmor-token\">Create a TransArmor token</a>\n      <a href=\"https://docs.clover.com/docs/ta-pilot-use-existing-transarmor-tokens\">Use existing TransArmor tokens</a>\n      <a href=\"https://docs.clover.com/reference/ta-token-pilot-transarmor-token-api-index\">TransArmor token API Index</a>\n    </div><!--end topnav-->\n  </div><!--end top-container-->\n</div>\n\n<!--css-->\n<style>\n/* Add a background color to the top navigation */\n.topnav {\n  font-family: 'Graphik-Regular', sans-serif;\n  background-color: #5D5D5D;\n  overflow: hidden;\n}\n\n/* Style the links inside the navigation bar */\n.topnav a {\n  font-family: 'Graphik-Regular', sans-serif;\n  float: left;\n  color: #f2f2f2;\n  text-align: center;\n  padding: 10px 12px;\n  text-decoration: none;\n  font-size: 12px;\n}\n\n/* Change the color of links on hover */\n.topnav a:hover {\n  background-color: #D8D8D8;\n  color: black;\n}\n\n/* Add a color to the active/current link */\n.topnav a.active {\n  background-color: #5D5D5D;\n  color: white;\n}\n</style>"
}
[/block]


In the initial release, the TransArmor (TA) token feature is available to a limited set of merchants. During the migration period, your APIs must support both TA tokens and legacy single-pay tokens. 

## Prerequisites

1. Set up a [sandbox developer account](https://docs.clover.com/docs/setup-clover-sandbox-account).
2. [Create an app in the sandbox](https://docs.clover.com/docs/creating-a-sandbox-app). See also [Ecommerce app permissions](https://docs.clover.com/docs/ecommerce-app-permissions).

## Steps

1. [Generate a PAKMS key](https://docs.clover.com/docs/ecommerce-generating-a-card-token#generate-a-pakms-key).
2. Create a single-use card token using [v1/token](https://docs.clover.com/reference/createtoken-1). See the [create a card token](https://docs.clover.com/docs/create-a-card-token)  tutorial for more information. 

In the response, a single-pay clover token or c-token(clv_1ABCDefgHI23jKL4m5nOPqR) returns.

## Use create a charge to generate a TA token

Send a POST request to the [v1/charges](https://docs.clover.com/reference/createcharge-1) endpoint.

1. Enter values in the following required parameters in the request:
   1. `amount`
   2. `currency`
   3. `source`  (clv\_ token - obtained from the response of v1/token)
2. In the `intent` attribute, select the **save_credentials_on_file**.
3. Under the `stored_credentials` object, select  **FIRST ** in `sequence`.

In the response, a multi-pay TransArmor token and a multipay c-token return. You can use this token for recurring and multi-pay transactions. 

### Request example

```Text cURL
curl --request POST \
     --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
     --header 'Accept: application/json' \
     --header 'Authorization: Bearer 7aacxxxx-xxxx-xxxx-xxxx-xxxxxxxxcae2' \
     --header 'Content-Type: application/json' \
     --header 'x-forwarded-for: {client_ip}' \
     --data '{
    "ecomind":"ecom"
    "amount": 122,
    "currency": "USD",
    "capture": false,
    "source": "clv_1ABCDefgHI23jKL4m5nOPqR",
    "intent": "save_credential_on_file",
    "stored_credentials": {
        "initiator": "MERCHANT",
        "sequence": "FIRST",
        "is_scheduled": false
     }'
```

### Response example

```Text JSON
{
    "id": "WZ1E7AQ16S5DY",
    "amount": "amount": 122,
    "payment_method_details": "card",
    "amount_refunded": 0,
    "currency": "USD",
    "created": 1721846264976,
    "captured": false,
    "ref_num": "420600610870",
    "auth_code": "OK6564",
    "outcome": {
        "network_status": "approved_by_network",
        "type": "authorized"
    },
    "status": "succeeded",
    "source": {
        "id": "clv_1ABCDefgHI23jKL4m5nOPqR",
        "address_line1_check": "pass",
        "address_zip": "11747",
        "address_zip_check": "pass",
        "brand": "VISA",
        "exp_month": "02",
        "exp_year": "2026",
        "first6": "400551",
        "last4": "0004"
    },
    "external_reference_id": "8KMRJY0S5RQ1R",
    "saved_credentials_on_file": {
        "tokenType": "TRANSARMOR",
        "value": "88************58"
    }
}
```

## Use pay for an order to generate a TA token

Send a POST request to [v1/orders/{orderId}/pay](https://docs.clover.com/reference/postordersidpay-1) endpoint.

1. Enter values in the following required parameters in the request:
   1. `orderId`
   2. `source` (clv\_ token - obtained from the response of v1/token)
2. In the `intent` attribute, select the **save_credentials_on_file**.
3. Under the `stored_credentials` object, select **FIRST ** in `sequence`.

In the response, a multi-pay TransArmor token and a multipay c-token return. You can use this token for recurring and multi-pay transactions.

### Request example

```Text cURL
curl --location 'https://scl-dev1.dev.clover.com/v1/orders/3NHSD5ESJE0JE/pay' \
--header 'Authorization: Bearer XXX' \
--header 'X-Clover-Merchant-Id: A2J94WZSZW851' \
--header 'Content-Type: application/json' \
--data '{
    "source": "clv_1ABCDefgHI23jKL4m5nOPqR",
    "intent": "save_credential_on_file",
    "stored_credentials": {
        "initiator": "MERCHANT",
        "sequence": "FIRST",
        "is_scheduled": false
    }
}'
```

### Response example

```Text JSON
{
    "id": "3NHSD5ESJE0JE",
    "saved_credentials_on_file": {
        "tokenType": "TRANSARMOR",
        "value": "12***********004"
    }
}
```
