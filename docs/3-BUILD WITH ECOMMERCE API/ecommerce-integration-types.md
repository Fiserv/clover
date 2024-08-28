---
title: "Ecommerce integration types"
slug: "ecommerce-integration-types"
excerpt: ""
hidden: false
metadata: 
  description: "Learn about Clover Ecommerce integrations: Clover-hosted checkout for a seamless, branded experience; iframe and API integration for secure, low PCI burden setups; and API-only integration for full control and customization, though it requires higher PCI compliance."
  image: 
    - "https://files.readme.io/70759b4-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Mon Jan 13 2020 00:24:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Aug 12 2024 05:36:55 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Learn about Clover Ecommerce integrations: Clover-hosted checkout for a seamless, branded experience; iframe and API integration for secure, low PCI burden setups; and API-only integration for full control and customization, though it requires higher PCI compliance.">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Clover offers different types of ecommerce integrations to cater to various business needs. Your apps can integrate with Clover Ecommerce services in different ways, depending on the needs of the app and merchants who use it. 

# Clover Ecommerce integration types

The Ecommerce integration types from Clover are:

[block:parameters]
{
  "data": {
    "h-0": "Integration type",
    "h-1": "Description",
    "h-2": "Key features",
    "0-0": "Clover-hosted checkout (HCO)",
    "0-1": "Provides a secure and reliable payment flow with minimal developer effort. You can embed the checkout page into an ecommerce site to offer a customized and brand-cohesive shopping experience.",
    "0-2": "- Provides a seamless, PCI-compliant transaction process.</br> - Includes reCAPTCHA to prevent fraud in card-not-present transactions.</br> - Offers a branded checkout experience for merchants who want to maintain a consistent brand experience throughout the checkout process.",
    "1-0": "Clover  iframe (inline frame) and API Integration",
    "1-1": "Provides a payment form with customizable card and page elements. You can add the [Clover-hosted iframe](https://docs.clover.com/docs/clover-iframe-integrations)  as a single-page component with all required fields or integrate each page element individually based on your app's design.",
    "1-2": "- Provides the simplest form of integration that uses a Clover-hosted <<glossary:iframe tokenizer>>.</br> - Allows secure card data entry in the payment form and returns a tokenized card for use with the Clover payment system with a reduced PCI compliance burden.</br> - Lets you quickly set up an online store with a payment form for card-not-present payments and is ideal for most ecommerce merchants.</br> - Allows customization of specific elements of the payment page on the secure Clover infrastructure.",
    "2-0": "Clover API-only integration",
    "2-1": "Involves connecting a merchant's ecommerce platform or app to Clover services using Ecommerce API-only integration.",
    "2-2": "- Uses additional services beyond the iframe tokenizer for apps requiring full control over the payment flow.</br> - Carries a higher PCI compliance burden for developers and merchants. It's important for API-only integration in production to have [PCI DSS certification](https://docs.clover.com/docs/pci-security-guidance-for-app-developers#what-is-pci-dss).</br> - Requires encryption and tokenization of card data using PAKMS and token APIs, along with the Ecommerce API for charges and customer data.</br> - Allows you to programmatically access Clover services such as processing payments, managing inventory, and retrieving transaction data.</br> - Requires more development effort but provides flexibility and scalability with customization options and advanced features."
  },
  "cols": 3,
  "rows": 3,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


***

# Payment flows and Ecommerce integration use cases

## iframe and API integration

### PCI burden on developers & merchants:\*\* LOW

The iframe tokenizer lets customers provide card data securely to the Clover servers. A `source`, which is an encrypted card token, is provided to your app after the card is encrypted and tokenized for use with the Clover payment system. This gives your app the benefit of reduced PCI compliance burden, as well as speeding up the integration and coding process by using a pre-built component. Clover keeps the tokenizer up to date with any future API changes, so your app requires less maintenance.

### Use case

Most ecommerce merchants require an app built with this type of integration. It provides the greatest business benefit and the lowest security risk for card-not-present payments through a third-party Clover app. For instance, a Clover merchant running a small retail store wants to set up an online store to expand their customer base. You can quickly build the payment aspect of the online store with an `iframe` and API integration.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ad18711-iframeApi.png",
        "iframeApi.png",
        2025
      ],
      "align": "center",
      "sizing": "100",
      "caption": "iframe and API request flow"
    }
  ]
}
[/block]


### Request flow ( iframe and API)

The fields in this example request are the minimum required for each endpoint. See the [Ecommerce API](https://docs.clover.com/reference/createcharge) for complete information. 

To charge a customer's card using the  iframe and API, your app completes the following flow:

1. Direct the user to the iframe based on your app's user flow.
2. Let the user enter and submit their card information. The Clover server returns the tokenized card as a `source`.
3. [Create a charge](https://docs.clover.com/reference/createcharge) request with the tokenized card information as `source` and enter a specific `amount` in cents.
4. Send the charge request `POST /v1/charges`to create a charge endpoint. The card is charged for the specified `amount`.

***

## API-only integration

Use Clover Ecommerce APIs for custom integrations tailored to your specific requirements. Integrate with additional services for apps requiring complete control over the payment flow.

### PCI burden on developers & merchants:\*\* HIGH

For an API-only integration, you must use the PAKMS and token APIs in addition to the Ecommerce API, which provides access to charges and customer data. These APIs provide operations for your app to retrieve an encryption key and use that key to encrypt and tokenize card data.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/31558c9-apiOnly.png",
        "apiOnly.png",
        2473
      ],
      "align": "center",
      "sizing": "100",
      "caption": "API only request flow"
    }
  ]
}
[/block]


### Request flow (API only)

The fields in this example request are the minimum required for each endpoint. See the [Ecommerce API](https://docs.clover.com/reference/createcharge) for complete information. You need a Public Access Key Management Service (PAKMS) key that is unique for each merchant to complete the OAuth flow that lets you use the Clover Ecommerce API. The PAKMS key does not expire. You need to send a request to the PAKMS endpoint only once for each merchant when they first install and configure your app. Your app should store the returned PAKMS key for use in each of that merchant's subsequent charge requests. See the [Ecommerce - PAKMS Service API reference](ref:keys) for more information.

The entire flow to tokenize a card and create a charge is available in the [Ecommerce API: Accept payments flow](https://docs.clover.com/docs/ecommerce-api-payments-flow). Here is a high-level overview of what our app needs to complete the flow to charge a customer's card using only the Ecommerce API:

1. Send an API `access token` request containing the `merchantId` and Clover App ID, also known as the `client_id`.
2. Send an `apiAccessKey` request to the PAKMS key endpoint `GET /pakms/apikey` using the `access_token`.  
3. For the `authorization: Bearer` token, enter the OAuth-generated `auth_token`. See [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth).

```curl cURL
curl --request GET \
  --url 'https://apisandbox.dev.clover.com/pakms/apikey' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {auth_token}'
```

The server returns an `apiAccessKey`.

3. [Create a card token](https://docs.clover.com/reference/create-card-token) request with a `card` object and its required fields: `number`, `exp_month`, `exp_year`, `cvv`, and `brand`.
4. In the `apikey` header, enter  the `apiAccessKey` and send the request to the token endpoint: `POST /v1/tokens`.

```curl
curl --request POST \
  --url 'https://token-sandbox.dev.clover.com/v1/tokens' \
  --header 'accept: application/json' \
  --header 'apikey: {apiAccesssKey}' \
  --header 'content-type: application/json' \
  --data '{ "card": { "number": "6011361000006668","exp_month": "12","exp_year": "2031","cvv": "123","brand": "DISCOVER"}}'
```

The Clover server returns the tokenized card as a `source`. All `source` tokens are alphanumeric and begin with `clv_`.

5. [Create a charge](https://docs.clover.com/reference/createcharge) `POST /v1/charges` request with the Clover token as the `source` and a specific `amount` in cents. The card is charged for the specified `amount`.

# Related topics

- [Generate a card token](doc:ecommerce-generating-a-card-token#encrypting-card-data) for more information about encrypting card data and then tokenizing the encrypted data. 
- [Create a card token](ref:tokens) endpoint in the Ecommerce API to create a single-use token to make a payment.
