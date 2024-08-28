---
title: "Migrate from Developer Pay to Ecommerce"
slug: "migrating-from-developer-pay-to-ecommerce"
excerpt: ""
hidden: false
metadata: 
  description: "If your app uses the Clover Developer Pay API for card-not-present payments, you can easily migrate your code to the Clover Ecommerce API."
  image: 
    - "https://files.readme.io/dcf9567-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Jan 24 2020 19:41:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 09 2024 09:39:37 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="If your app uses the Clover Developer Pay API for card-not-present payments, you can easily migrate your code to the Clover Ecommerce API. Learn why the Clover Ecommerce API is a preferred choice.">

[block:html]
{
  "html": "<div>\n<section class=\"header\">\n   <p style=\"background-color: #f3f8f3;\nborder-left: 3px solid #280; padding: 1em;\">\n  <b>IMPORTANT NOTICE to Clover Developers</b><br><b>Developer Pay (DevPay) was deprecated on October 27, 2021, and is no longer supported by Clover.</b> <br><br>Contact <a href=\"mailto:developer-relations@devrel.clover.com?subject=Moving to Ecommerce API\">Developer Relations support</a> with questions or concerns.</p>\n</div>"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# Ecommerce migration guide

The Ecommerce API provides developers and merchants with features and updates that make transitioning from Developer Pay a recommended action:

- **Reduced PCI scope: **With the new Clover-hosted `iframe` tokenizer, sensitive card data will not pass through your app’s code, and this reduces your PCI compliance burden
- **Additional payment functions: **Refunds were not available with Developer Pay, but you can refund a charge with Ecommerce

The following sections will help you understand the new API and guide you through the steps to transition your app from using Developer Pay to Ecommerce.

## Comparison: Developer Pay and Ecommerce

Before beginning a transition project, read about the available [Integration types](doc:ecommerce-integration-types) to ensure you know which you will use for your updated application.

If you want to integrate with the Ecommerce API, you need to understand the similarities and differences with the old API.

> 🚧 IMPORTANT
> 
> An API-only integration may expose your app to greater PCI compliance risk than using the Clover-hosted `<iframe>`.

### Authentication

Developer Pay and Ecommerce have the same authentication requirements. Your application must send a valid OAuth 2.0 API access token with each request. For more information, see [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth).

### Permissions

The Ecommerce API `/v1/charges` endpoints require the `PAYMENTS_R`, `PAYMENTS_W`, and `ENABLE_ONLINE_PAYMENTS` permissions, so no changes are needed to use the payment functions of the API. If your app will use other Ecommerce endpoints, see [Ecommerce app permissions](doc:ecommerce-app-permissions) for information about additional permissions your app may need.

### New payment features

The Ecommerce API offers payment operations not offered with Developer Pay. Those features are outside the scope of this migration guide, but you are encouraged to enhance your app with as many of these as needed for your use case.

- Pre-authorizing a card for an amount
- Refunding a charge

### Card tokenization

Developer Pay required apps to create an encrypted card token on the client side, an operation that exposes apps and their merchant users to a greater PCI compliance burden. Merchants also had to be specifically set up to accept payments with tokenized cards.

The Ecommerce API provides a more merchant- and developer-friendly option in a Clover-hosted card details form. Any US merchant can accept payments using the new tokens without additional configuration. This form is embeddable `<iframe>` element that securely collects the sensitive card data and returns a Clover token (`cToken`) in response.

| DevPay endpoint                  | Ecommerce replacement       |
| -------------------------------- | --------------------------- |
| `GET /v2/merchant/{mId}/pay/key` | Hosted `<iframe>` tokenizer |

### Payments

The Ecommerce API provides two different endpoints that can replace the existing Developer Pay endpoints, depending on your use case.

| DevPay endpoint               | Ecommerce replacement                                             |
| ----------------------------- | ----------------------------------------------------------------- |
| `POST /v2/merchant/{mId}/pay` | To pay for a charge:<br />`POST /v1/charges`                      |
|                               | To pay for a created order:<br />`POST /v1/orders/{order_id}/pay` |

## Convert DevPay requests to Ecommerce requests

The JSON request bodies for the Ecommerce `/v1/orders/{orderId}/pay` endpoint are simpler than those required for DevPay. The following sections provide the minimum changes required, but the endpoint accepts additional request values you may find useful. See the API reference documentation for more information about these optional fields.

### Charge a card to pay for an order

Charging a customer card is done in a similar manner with the new API. The major difference is that card data and metadata are not sent in the request. Instead, you set the `source` value as the `cToken` representing the customer's card. Also, the `orderId` is now specified in the URL instead of the request body. 

It is recommended that you continue creating orders with the `/v3/merchants/{mId}/orders` endpoint. While you can migrate to use `/v1/orders`, this endpoint is meant for streamlined app creation and does not include all of the same features. Note that the base URL for these endpoints is different.

> 📘 NOTE
> 
> You can also charge a card without having an associated order. See the [Tutorials](doc:ecommerce-api-tutorials) for more information.

```diff
{
- "zip": "94041",
- "expMonth": 1,
- "cvv": "111",
- "last4": "1111",
- "expYear": 2021,
- "first6": "411111",
- "cardEncrypted": "X8UeKej+AEG1h0wD9Xw==",
- "orderId": "HCFFREA222N02", //now part of the request URL
- "taxAmount": 9,
- "amount": 109, //part of the original order data
- "currency: "usd" //part of the original order data
+ "source": "cToken",
}
```

Taxes are handled differently with the Ecommerce API. DevPay defined a separate field for this part of the transaction total called `taxAmount`. Ecommerce requests should set the full amount to be charged, including any tax, as the value of the `amount` field.

The fields in the `/charges` response differ from the responses from DevPay's `v2/{mId}/pay` endpoint. The following table shows these differences to remap your code to the new fields and values.

| DevPay response field              | Ecommerce response field                                               | Notes                                                                                                           |
| ---------------------------------- | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `authCode`                         | Not available                                                          |                                                                                                                 |
| `avsResult`                        | Not available                                                          |                                                                                                                 |
| `cvvResult`                        | `source.cvc_check`                                                     | If a CVC was provided, this value will be one of the following: `pass`, `failed`, `unavailable`, or `unchecked` |
| `failureMessage`                   | `failure_message`                                                      |                                                                                                                 |
| `paymentId`                        | `id`                                                                   |                                                                                                                 |
| `"result": (APPROVED or DECLINED)` | `"paid": (true/false)` - The new value is a boolean instead of an enum |                                                                                                                 |
| `token`                            | N/A                                                                    | Tokens are returned from the hosted tokenizer                                                                   |

### Charge a vaulted card

With DevPay, a vaulted card token could only be obtained after charging a card for an initial transaction. The hosted tokenizer replaces the dual-purpose `/pay` endpoint with a dedicated tool for retrieving card tokens. Because a tokenized card is required for all Ecommerce requests, code for retrieving and storing a token from the `/pay` endpoint should be migrated to use the tokenizer.
