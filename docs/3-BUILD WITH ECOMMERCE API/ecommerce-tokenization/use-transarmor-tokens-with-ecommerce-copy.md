---
title: "Use TransArmor tokens with Ecommerce (COPY)"
slug: "use-transarmor-tokens-with-ecommerce-copy"
excerpt: ""
hidden: true
createdAt: "Wed Aug 07 2024 05:59:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Aug 08 2024 19:20:11 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=\"Learn how to use TransArmor tokens in the Clover network for multi-pay and recurring payments.\">\n\n<!--DS-6327--> "
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

TransArmor tokens provide an additional layer of security to protect cardholder data during transactions and reduce the regeneration of payment tokens. In Clover, you can create and use an existing transarmor token to [create a charge](https://docs.clover.com/reference/createcharge) endpoint.

# Create a TransArmor token

You can create a new <<glossary:TransArmor token>> using the existing [create a card token](https://docs.clover.com/reference/create-card-token) endpoint flow.

## Prerequisites

1. Set up a [sandbox developer account](https://docs.clover.com/docs/setup-clover-sandbox-account).
2. [Create an app in the sandbox](https://docs.clover.com/docs/creating-a-sandbox-app). See also [Ecommerce app permissions](https://docs.clover.com/docs/ecommerce-app-permissions).

## Steps

1. [Generate a PAKMS key](https://docs.clover.com/docs/ecommerce-generating-a-card-token#generate-a-pakms-key).
2. Create a single-use token using [Create a card token](https://docs.clover.com/reference/create-card-token). See the [Create a card token](<>)  tutorial for more information. In the response, a single-pay clover token or c-token(clv_a1B4jhfu234h46hvh) is returned.

## Use create a charge to generate a TA token

Send a POST request to the [v1/charges](https://docs.clover.com/reference/createcharge) endpoint.

1. Enter values in the following required parameters in the request:
   1. `amount`
   2. `currency`
   3. `source` 
2. In the `intent` attribute, select the **save_credentials_on_file**.
3. From the `stored_credentials` object, select the **FIRST ** in the `sequence`.

In the response, a multi-pay transarmor token and a multipay c-token return. You can use this token for recurring and multi-pay transactions. 

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
    "source": "clv_1TSTS*****************66",
    "intent": "save_credential_on_file",
    "stored_credentials": {
        "initiator": "MERCHANT",
        "sequence": "FIRST",
        "is_scheduled": false
     }'
```

### Response example

```Text Json
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
        "id": "clv_1TSTS*****************66",
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

Send a POST request to [v1/orders/{orderId}/pay](https://docs.clover.com/reference/postordersidpay) endpoint.

1. Enter values in the following required parameters in the request:
   1. `orderId`
   2. `source`
2. In the `intent` attribute, select the **save_credentials_on_file**.
3. From the `stored_credentials` object, select the **FIRST ** in the `sequence`.

In the response, a multi-pay transarmor token and a multipay c-token return. You can use this token for recurring and multi-pay transactions.

### Request example

```Text cURL
curl --location 'https://scl-dev1.dev.clover.com/v1/orders/3NHSD5ESJE0JE/pay' \
--header 'Authorization: Bearer XXX' \
--header 'X-Clover-Merchant-Id: A2J94WZSZW851' \
--header 'Content-Type: application/json' \
--data '{
    "source": "clv_1T********************S2",
    "intent": "save_credential_on_file",
    "stored_credentials": {
        "initiator": "MERCHANT",
        "sequence": "FIRST",
        "is_scheduled": false
    }
}'
```

### Response example

```Text Json
{
    "id": "3NHSD5ESJE0JE",
…
    "saved_credentials_on_file": {
        "tokenType": "TRANSARMOR",
        "value": "12***********004"
    }
…
}
```

# Use existing TransArmor tokens

Use your existing <<glossary:TransArmor token>> to create a charge in the Clover Ecommerce network. 

## Prerequisites

1. Set up a [sandbox developer account](https://docs.clover.com/docs/setup-clover-sandbox-account).
2. [Create an app in the sandbox](https://docs.clover.com/docs/creating-a-sandbox-app). See also [Ecommerce app permissions](https://docs.clover.com/docs/ecommerce-app-permissions).
3. An existing valid TA token.

## Steps

1. [Generate a PAKMS key](https://docs.clover.com/docs/ecommerce-generating-a-card-token#generate-a-pakms-key).
2. Send a POST request to the `v1/token` endpoint to generate a token.
3. Expand the `external_token` object.
4. Enter information in the required fields.

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "h-2": "Require/Optional",
    "0-0": "`token_value`",
    "0-1": "Value of the TransArmor token.",
    "0-2": "Required",
    "1-0": "`exp_month`",
    "1-1": "Card expiration month in 2-digit format.  \nFormat: mm",
    "1-2": "Required",
    "2-0": "`exp_year`",
    "2-1": "Card expiration year in 2- or 4-digit format.  \nFormat: yy or yyyy",
    "2-2": "Required",
    "3-0": "`apikey`",
    "3-1": "Universally unique identifier (ID) of the API.  \nThe public API key is associated with the specific merchant and developer app.",
    "3-2": "Required",
    "4-0": "`name`",
    "4-1": "Cardholder's full name on the card.",
    "4-2": "Optional",
    "5-0": "`brand`",
    "5-1": "Card brand.",
    "5-2": "Optional",
    "6-0": "`first6`",
    "6-1": "First 6 numbers of the primary account number.",
    "6-2": "Optional",
    "7-0": "`last4`",
    "7-1": "Last 4 numbers of the primary account number.",
    "7-2": "Optional",
    "8-0": "`address_line1`",
    "8-1": "First line of the address. Can include the street address, PO box, or company name.",
    "8-2": "Optional",
    "9-0": "`address_line2`",
    "9-1": "Second line of the address. Can include the apartment, suite, unit, or building number.",
    "9-2": "Optional",
    "10-0": "`address_city`",
    "10-1": "City of the customer address. Can include district, suburb, town, or village.",
    "10-2": "Optional",
    "11-0": "`address_state`",
    "11-1": "State of the customer address. Can include county, province, or region.",
    "11-2": "Optional",
    "12-0": "`address_zip`",
    "12-1": "State of the customer address. Can include county, province, or region.",
    "12-2": "Optional",
    "13-0": "`address_country`",
    "13-1": "Billing address country, if provided.",
    "13-2": "Optional",
    "14-0": "`transactionId`",
    "14-1": "Initial transaction identifier received from Rapid connect transaction response.",
    "14-2": "Optional"
  },
  "cols": 3,
  "rows": 15,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


A multi-use TransArmor token is returned in the response. The token is alphanumeric and begins with clv\_. Example: clv_1ABCDefgHI23jKL4m5nOPqR

## Request example

```Text cURL
curl --request POST \
     --url 'https://token-sandbox.dev.clover.com/v1/tokens' \
     --header 'apikey: xxx' 
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '{
  "external_token": {
    "token_type": "TRANSARMOR",
    "transarmor_token_attribute": {
      "exp_month": "12",
      "exp_year": "2027"
    },
    "token_value": 1234567890
  }
}
'
```

## Response example

```Text json
{  
    "id": "clv_1********************kgN",  
    "object": "token",  
    "": {  
        "last4": ""  
    }  
}
```

## Use create a charge with an existing TA token

Send a POST request to the [v1/charges](https://docs.clover.com/reference/createcharge) endpoint.

1. Enter values in the following required parameters in the request:
   1. `amount`
   2. `currency`
   3. `source` 
2. In the `intent` attribute, select the **save_credentials_on_file**.
3. From the `stored_credentials` object, select the **SUBSEQUENT** in the `sequence`.

In the response, a multi-pay transarmor token returns. You can use this token for recurring and multi-pay transactions. 

### Request example

```curl
curl --request POST \
     --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
     --header 'Accept: application/json' \
     --header 'Authorization: Bearer ab86****-****-****-****-*****9867833' \
     --header 'Content-Type: application/json' \
     --header 'x-forwarded-for: {client_ip}' \
     --data '{
    "ecomind":"ecom"
    "amount": 122,
    "currency": "USD",
    "capture": false,
    "source": "clv_1********************kgN",
    "stored_credentials": {
        "initiator": "MERCHANT",
        "sequence": "SUBSEQUENT",
        "is_scheduled": false
     }'
```

### Response example

```curl json
{
  "id": "ABDFEFG1HIJK2", 
  "amount": 122,
  "payment_method_details": "card",
  "amount_refunded": 0,
  "currency": "usd",
  "created": 123456789123,
  "captured": true,
  "ref_num": 987654321,
  "auth_code": 123456,
  "outcome": {
    "network_status": "approved_by_network",
    "type": "authorized"
  },
  "paid": true,
  "status": "succeeded",
  "source": {
    "id": "clv_1********************kgN",
    "brand": "DISCOVER",
    "exp_month": 12,
    "exp_year": 2025,
    "first6": 112233,
    "last4": 1111
  },
  "stored_credentials": {
        "initiator": "MERCHANT",
        "sequence": "SUBSEQUENT",
        "is_scheduled": false
     }'
  "ecomind": "ecom"
}

```

## Use pay for an order with an existing TA token

Send a POST request to [v1/orders/{orderId}/pay](https://docs.clover.com/reference/postordersidpay) endpoint.

1. Enter values in the following required parameters in the request:
   1. `orderId`
   2. `source`
2. In the `intent` attribute, select the **save_credentials_on_file**.
3. From the `stored_credentials` object, select the **SUBSEQUENT ** in the `sequence`.

### Request example

```Text cURL
curl --location 'https://scl-dev1.dev.clover.com/v1/orders/3NHSD5ESJE0JE/pay' \
--header 'Authorization: Bearer XXX' \
--header 'X-Clover-Merchant-Id: A2J94WZSZW851' \
--header 'Content-Type: application/json' \
--data '{
    "source": "clv_1********************kgN",
    "intent": "save_credential_on_file",
    "stored_credentials": {
        "initiator": "MERCHANT",
        "sequence": "FIRST",
        "is_scheduled": false
    }
}'
```

### Response example

```Text Json
{
    "id": "3NHSD5ESJE0JE",
…
    "saved_credentials_on_file": {
        "tokenType": "TRANSARMOR",
        "value": "122754**********"
    }
…
}
```
