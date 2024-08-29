---
title: "Ecommerce API: Accept payments flow"
slug: "ecommerce-api-payments-flow"
excerpt: ""
hidden: false
metadata: 
  description: "View the standard flow for accepting payments with the Ecommerce API, which involves tokenizing a customer card and using the token to pay for a charge or order."
  image: []
  robots: "index"
createdAt: "Wed Jul 10 2024 05:22:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 30 2024 08:40:16 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content=" View the standard flow for accepting payments with the Ecommerce API, which involves tokenizing a customer card and using the token to pay for a charge or order.>

<!--Steps tested and updated for DS-6762. -->

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

With the Clover Ecommerce API and SDKs, you can build seamless Payment Card Industry (PCI) compliant payment experiences for merchants with hosted iframe and API integrations. All payments and transactions with the Clover Ecommerce API are PCI compliant and require tokenized card information.

The standard flow for accepting payments with Ecommerce API consists of two steps:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b6abdca-acceptingpayments.png",
        "acceptingpayments.png",
        840
      ],
      "align": "center",
      "sizing": "50% ",
      "border": true,
      "caption": "Ecommerce API standard flow"
    }
  ]
}
[/block]


# Prerequisites

To tokenize a customer card, you need to encrypt a customer card as a `source` token using the Ecommerce API: [Create a card token](https://docs.clover.com/reference/create-card-token) endpoint. To use the endpoint, you need an API token or `apiAccessKey` from the Public Access Key Management Service (PAKMS). The PAKMS key identifies the merchant who is tokenizing the customers' cards. You can use the same static PAKMS key to tokenize multiple cards for that merchant.

- Generate an OAuth authorization code or `auth_token` with [specific permissions](doc:ecommerce-app-permissions). For more information, see [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth).
- Review the [Ecommerce API Reference](https://docs.clover.com/reference/createcharge) for additional steps to work with charges, customers, orders, refunds, and more.

# Step 1: Generate a PAKMS key

1. [Get an `OAuth2` token](https://docs.clover.com/docs/obtaining-an-oauth-token)  or `auth_token` that displays as `code` in the link (URL) of your test app connected with a test merchant in the sandbox.

   [block:image]{"images":[{"image":["https://files.readme.io/275397f-auth_code.png","","Test app install information"],"align":"center","border":true,"caption":"Test app install information"}]}[/block]
2. Send a GET request using Postman to the following URL using:

- `App ID` as the `client_id`,
- `App Secret` from the App Settings page as the `client_secret`, and
- Authorization code or `auth_token` as the `code`

```html API token request URL format
https://sandbox.dev.clover.com/oauth/token?client_id={appId}&client_secret={APP_SECRET}&code={AUTHORIZATION_CODE
```

```Text Example
https://sandbox.dev.clover.com/oauth/token?client_id=RKxxxxxxxxS9C&client_secret=d46dxxxx-xxxx-xxxx-xxxx-xxxxxxxx1b77&code=1ccdxxxx-xxxx-xxxx-xxxx-xxxxxxxea1b
```

In response, the Clover server displays an API `access token.` 

```json Response: access_token
{
   "access_token":"{API_TOKEN}"
}
```

```json Response example
{
    "access_token": "ce7exxxx-xxxx-xxxx-xxxx-xxxxxxxx4b24"
}
```

**Note: **All Ecommerce API endpoints require an OAuth-generated `access_token` with specific permissions.

3. Send a `GET` request to the `/v1/pakms/apikey` endpoint using the `access_token` as the Bearer token See [Retrieve an API key](ref:keys).

   [block:image]{"images":[{"image":["https://files.readme.io/1936510-BearerToken-AccessToken.png","",""],"align":"center","sizing":"60% ","border":true}]}[/block]

In response, the Clover server returns an `apiAccessKey`, which is the PAKMS key.

```json Response: apiAccessKey
{
  "active": true,
  "apiAccessKey": "af4exxxxxxxxxxxxxxxxxxxxxxxxd145",
  "createdTime": 1722230745532,
  "developerAppUuid": "RKxxxxxxxxx9C",
  "merchantUuid": "6Xxxxxxxxxx91",
  "modifiedTime": 1722230745532
}
```

 In Step 2: Tokenize a card, use the `apiAccessKey` as the `apikey` header.

**Additional information:**

- To generate an OAuth `auth_token` for a test merchant, see  [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth).
- To learn more about `auth_token` and PAKMS key, see our blog post [Fiddling Through Digital Keys: Clover Auth Tokens and Ecommerce Keys](https://medium.com/clover-platform-blog/understanding-clover-auth-tokens-and-ecommerce-keys-4e048827afa2).

***

# Step 2: Tokenize a card

1. Send a `POST` request to the `/v1/tokens` endpoint. See [Create a card token](https://docs.clover.com/reference/create-card-token).
2. In the `apikey` header, enter the `apiAccessKey` generated in Step 1: Generate a PAKMS key.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f527e46-Screenshot_2024-07-29_at_11.43.21_AM.png",
        "",
        "Create a card token: Header apikey"
      ],
      "align": "center",
      "sizing": "80% ",
      "border": true,
      "caption": "Create a card token: Header apikey"
    }
  ]
}
[/block]


```curl Tokenize a test card number
curl --request POST \
  --url 'https://token-sandbox.dev.clover.com/v1/tokens' \
  --header 'accept: application/json' \
  --header 'apikey: {apikey}' \
  --header 'content-type: application/json' \
  --data '{"card":{"number":"6011361000006668","exp_month":"12",
"exp_year":"2030","cvv":"123","brand":"DISCOVER"}}'
```

In response, the Clover server returns a `source` token. All `source` tokens are alphanumeric and begin with `clv_`.

```json Response: Card token
{
  "id": "clv_1TSTxxxxxxxxxxxxxxxxxFQif",
  "object": "token",
  "card": {
    "exp_month": "12",
    "exp_year": "2030",
    "first6": "601136",
    "last4": "6668",
    "brand": "DISCOVER"
  }
}
```

**Additional information:** To encrypt and tokenize card data, see [Generate a card token](doc:ecommerce-generating-a-card-token#encrypting-card-data).

***

# Step 3: Pay for a charge or order

After you tokenize a card, use the `source` token to pay for a charge or an order. For information on required request parameters, see [Create a charge tutorial](https://docs.clover.com/docs/create-a-charge).

1. Send a `POST` request to the `/v1/charges` endpoint to pay for an $18.00 charge. 
2. In the  `authorization: Bearer` header, enter the `access_token` generated in Step 1: Generate a PAKMS key. 
3. In the `source` parameter, enter the token generated in Step 2: Tokenize a customer card. All `source` tokens are alphanumeric and begin with `clv_`.

```curl Pay with a tokenized card
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'content-type: application/json' \
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"amount":1800,"currency":"usd","source":"{token}"}'
```

In response, the Clover server returns a unique charge `id`, payment `status`, and additional information about the transaction.

**Additional information:** To know about the different data objects your apps interact with for different Ecommerce API flows, see [Ecommerce data model](doc:ecommerce-data-model).
