---
title: "Create a gift card token (COPY)"
slug: "ds-6326-create-a-gift-card-token"
excerpt: ""
hidden: true
createdAt: "Mon Aug 12 2024 09:08:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Aug 12 2024 09:14:00 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=\"Learn how to create a gift card token to create single pay token for single payments.\">\n\n<!--DS-5812-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

A gift card is a prepaid payment card used to make purchases at participating restaurants, stores, or online retailers. A gift card can have different denominations. You can redeem the value of these cards for services, merchandise, or even cash, depending on the terms and conditions set by the card issuer.

## Prerequisites

To process secure gift card payments, you need one of the following:

- Native gift card with a SCV (security code value). Clover Gift Card uses the integrated gift card solution payment gateway from Fiserv.
- Non-native gift card with an FCA (foreign access code). This is a non-Fiserv gift card or a gift card that does not use the Fiserv payment gateway.

## Steps

1. [Generate a PAKMS key](https://docs.clover.com/docs/ecommerce-generating-a-card-token#generate-a-pakms-key).
2. Send a POST request to the `/v1/tokens` endpoint. See [Create a gift card token](https://docs.clover.com/reference/create-giftcard-token).
3. Enter information in the required fields.

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "h-2": "Require/Optional",
    "0-0": "`card_number`",
    "0-1": "Gift card number.  \n Length: One of the following: 6-digit, 13-digit, 16-digit, or 19-digit",
    "0-2": "Required",
    "1-0": "`security_code`",
    "1-1": "Encrypted security code associated with the gift card.  \nLength: 4-8 characters",
    "1-2": "Optional",
    "2-0": "`foreign_access_code`",
    "2-1": "Foreign access code for merchants converting to CLGC (closed loop gift card) from an external gift card program, if applicable.",
    "2-2": "Required in case of non-Fiserv gift cards",
    "3-0": "`apikey`",
    "3-1": "Universally unique identifier (ID) of the API.  \nPublic API key associated with the specific merchant and developer app.",
    "3-2": "Required"
  },
  "cols": 3,
  "rows": 4,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


A single-use gift card token is returned in the response. The token is alphanumeric and begins with clv\_. Example:      clv_1TSTSECWntExtCdPXnbFjkgN

4. Use the gift card token for a single transaction to:
   - [Create a charge](https://docs.clover.com/reference/createcharge) 
   - [Pay for an order](https://docs.clover.com/reference/postordersidpay)
   - [Request gift card balance](https://docs.clover.com/reference/gift-card-balance-inquiry)
   - [Reload gift card](https://docs.clover.com/reference/gift-card-reload)
   - [Request cashout of gift card balance](https://docs.clover.com/reference/gift-card-cashout)
   - [Create and activate physical and virtual gift card](https://docs.clover.com/reference/gift-card-activation)

## Request example

```curl
curl --request POST \
     --url 'https://token-sandbox.dev.clover.com/v1/tokens' \
     --header 'apikey: xxx' 
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '{
  "gift_card": {
    "card_number": "98765441066",
    "security_code": "785577",
    "foreign_access_code": "67755"
  }
}'
```

## Response example

```curl

{  
    "id": "clv_1TSTSECWntExtCdPXnbFjkgN",  
    "object": "token",  
    "giftCard": {  
        "last4": "1066"  
    }  
}
```
