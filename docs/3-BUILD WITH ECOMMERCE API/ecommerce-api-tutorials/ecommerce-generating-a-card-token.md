---
title: "Generate a card token"
slug: "ecommerce-generating-a-card-token"
excerpt: ""
hidden: false
metadata: 
  description: "Card tokens can be generated using the Clover-hosted iframe or a REST call. This page explains the process for both options."
  image: 
    - "https://files.readme.io/5637ed9-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Mon Aug 03 2020 20:06:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:58:22 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The first step in the Ecommerce API flow is encrypting a customer card as a `source` token. Apps using an `iframe` and `API integration` receive and send `source` tokens that represent encrypted customer card data. See [Use the Clover-hosted iframe](https://docs.clover.com/docs/using-the-clover-hosted-iframe#adding-interaction-to-the-payment-form) and [iframe and API Integration](https://docs.clover.com/docs/ecommerce-integration-types#section-iframe-and-api). Clover uses this token to process secure payments. Complete an Ecommerce API flow by using the `source` token, along with an OAuth token.

# API-only integrations

For [API-only integrations](doc:ecommerce-integration-types#section-api-only), use a PAKMS key obtained from the PAKMS key endpoint (`GET /pakms/apikey`) to authorize the tokenization of a card. To learn more, see our blog post [Fiddling Through Digital Keys: Clover Auth Tokens and Ecommerce Keys](https://medium.com/clover-platform-blog/understanding-clover-auth-tokens-and-ecommerce-keys-4e048827afa2).

> ❗️ WARNING
> 
> Using the `iframe` and API integration to securely accept credit card information reduces the PCI compliance burden on app developers and on Clover merchants. To use the API-only integration in production, you must have (or use a service that has) a <a href="https://www.imperva.com/learn/data-security/pci-dss-certification/" target="_blank">PCI DSS certification</a>.

> 🚧 IMPORTANT
> 
> Clover reserves the right to disable keys suspected of misuse that violates our terms. If needed, you can request the deactivation of a key by sending an email to: <a href="mailto:developer-relations@devrel.clover.com" target="_blank">developer-relations@devrel.clover.com</a>

## Generate a PAKMS key

To charge a customer's card using only the API, your app will complete the following flow. The fields mentioned for the various requests are the minimum required for each endpoint. See [API Reference overview](ref:api-reference-overview) for complete information.

PAKMS keys are unique for each merchant and do not expire. Because of this, the PAKMS endpoint should be called only once for each merchant when they first configure an app. The app should store the returned key for use in each of that merchant's subsequent charge requests. See the [PAKMS API reference](ref:keys) for more information.

To generate a PAKMS key:

1. [Get an `OAuth2` token](https://docs.clover.com/docs/obtaining-an-oauth-token), also known as, `access token`.
2. Send a `GET` request to the [Retrieve an API key](ref:keys) endpoint.
3. Set the Authorization header as the `auth_token.` 

```curl
curl --request GET \
     --url 'https://scl-sandbox.dev.clover.com/pakms/apikey' \
     --header 'accept: application/json' \
     --header 'authorization: Bearer <TOKEN>'
```

The server returns an `apiAccessKey`.

## Encrypt card data

1. Retrieve the public encryption keys from [CDN](https://checkout.clover.com/assets/keys.json).  These keys generally do not change and should be cached by your application. The endpoint returns:

- `TA_PUBLIC_KEY_DEV` for use in the sandbox environment, and
- `TA_PUBLIC_KEY_PROD` for use in the production environment

```json JSON response
{
  "TA_PUBLIC_KEY_DEV": "...",
  "TA_PUBLIC_KEY_PROD": "..."
}
```

2. Do the following to encrypt the card information. See the following code: [Java example](https://clover.app.box.com/s/rz18bni3bpmdrc8wc92xm4w8h9grrtty). 
   - Parse the Base64 public key string (returned by the CDN). Obtain the `modulus` and `exponent`.
   - Generate an RSA public key using the `modulus` and `exponent` values.
   - Prepend the `prefix` value to the card number.     
   - Using the public key, encrypt the combined prefix and card number.
   - Base64 encode the resulting encrypted data into a string. This string is the `encrypted_pan` value in the `/v1/tokens` request.

## Tokenize encrypted card data

1. Create a token request containing a `card` object with its required fields, including:

| Field               | Description                                                                                    | Type    |
| :------------------ | :--------------------------------------------------------------------------------------------- | :------ |
| `encrypted_pan`     | Enter the encryption service ID used to store the payment card's Primary Account Number (PAN). | String  |
| `transarmor_key_id` | Enter the ID of the TransArmor key used to perform the encryption.                             | String  |
| `exp_month`         | Enter the month that the card will expire.                                                     | Numeric |
| `exp_year`          | Enter the year that the card will expire.                                                      | Numeric |
| `cvv`               | Enter the Card verification value (CVV) number.                                                | Numeric |
| `brand`             | Enter the brand ID (that is, Mastercard, Visa, and so on.)                                     | Numeric |
| `first6`            | Enter the first six digits of the card.                                                        | Numeric |
| `last4`             | Enter the last four digits of the card.                                                        | Numeric |

2. Set the `apiAccessKey` (PAKMS key) as the value of the `apikey` header and send a `POST` request to the `/v1/tokens` endpoint. See [Create a card token](ref:tokens) for more information.

```curl
curl --request POST \
  --url 'https://token-sandbox.dev.clover.com/v1/tokens' \
  --header 'accept: application/json' \
  --header 'apikey: {apiAccessKey}' \
  --header 'content-type: application/json' \
  --data '{"card":{"encrypted_pan":"{encrypted_card_number}", "transarmor_key_id":"{transarmor_key_id}","first6":"601136","last4":"6668","exp_month":"12","exp_year":"2021","cvv":"123","brand":"DISCOVER"}}'
```

The server returns a `source` token.  
Format: All `source` tokens are alphanumeric and begin with `clv_`.  
With a <code>source</code> token, you can create a charge, create and pay for orders, accept tips, and save customer cards for future transactions.

Clover provides several [sandbox test cards](doc:test-card-numbers) that you can use when developing your app.
