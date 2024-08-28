---
title: "API Reference overview"
slug: "api-reference-overview"
excerpt: ""
hidden: false
metadata: 
  description: "The Clover Platform REST API reference provides a comprehensive guide to each REST API endpoint in the sandbox environment. This API reference describes the use of each endpoint and provides sample REST API requests."
  image: []
  robots: "index"
createdAt: "Wed Oct 17 2018 23:46:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Aug 12 2024 04:15:00 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="The Clover Platform REST API Reference provides a comprehensive guide to each REST API endpoint in the sandbox environment. This API Reference describes the use of each endpoint and provides sample REST API requests.">

<!-- DS-6274 - updated by Aneesha on Aug 12, 2024 as part of updating REST API token topics. Reusable text has been added and sandbox URL corrected.-->

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Welcome to the Clover platform REST API Reference. This reference describes the function of each REST API endpoint in the sandbox environment.

# Before you begin

- See [Get started](https://docs.clover.com/docs/select-an-integration) to learn about the type of Clover integrations.
- See [Use Clover developer environments](https://docs.clover.com/docs/clover-environments) to learn about the different Clover environments, developer dashboards, and [setting up your developer account](https://docs.clover.com/docs/create-a-sandbox-account).
- See [Generate a merchant-specific test API token](https://docs.clover.com/docs/generate-a-test-api-token) for information on retrieving your first API token. The API token provides the necessary permissions to access test merchant data.
- Learn about API tokens and keys in our blog post [Fiddling Through Digital Keys: Clover Auth Tokens and Ecommerce Keys](https://medium.com/clover-platform-blog/understanding-clover-auth-tokens-and-ecommerce-keys-4e048827afa2).

# Sandbox base URLs

<!--DS-325 & DS-6547; correct domains: apisandbox.dev.clover.com; api.clover.com
**Note from Hunter: ** sandbox.dev.clover.com is for internal developers, whereas apisandbox.dev.clover.com is for third-party developers. I impacts how traffic to/from the servers is managed.-->

Use the [Android emulator](doc:setting-up-an-android-emulator) or [Developer Kits](https://cloverdevkit.com/) in the sandbox environment for building and testing your apps with test merchants. In the sandbox environment, Clover provides base URLs for different services:

[block:parameters]
{
  "data": {
    "h-0": "API",
    "h-1": "URL",
    "0-0": "Platform API",
    "0-1": "`https://apisandbox.dev.clover.com`",
    "1-0": "Tokenization service API",
    "1-1": "`https://token-sandbox.dev.clover.com`",
    "2-0": "Ecommerce service API",
    "2-1": "`https://scl-sandbox.dev.clover.com`  \n  \nSee the [Ecommerce API tutorials](doc:clover-development-basics-ecommerce)  for more information.  \n  \n📘 **NOTE: **The Ecommerce API and all related features are currently available in the US and Canada. We will provide updated information as Clover extends availability for more regions."
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]


# Production base URLs

In the production environment, Clover provides base URLs for different services in [supported markets](doc:multiple-markets).

| API and region                              | URL                         |
| :------------------------------------------ | :-------------------------- |
| Platform API (North America: US and Canada) | `https://api.clover.com`    |
| Platform API (Europe)                       | `https://api.eu.clover.com` |
| Platform API (Latin America)                | `https://api.la.clover.com` |
| Tokenization service API                    | `https://token.clover.com`  |
| Ecommerce service API                       | `https://scl.clover.com`    |

***

# Use the API Reference

## Prerequisites

To use the Clover platform API, you require the following:

- [Sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account)
- [Test merchant account](https://docs.clover.com/docs/use-test-merchants-dashboard)
- [Test API token](https://docs.clover.com/docs/generate-a-test-api-token) with permissions to make REST API requests and manage your test merchant's data.

## Make a sample REST API call

To make a sample REST API call using the Clover API reference:

1. From the Platform API left navigation, select **MERCHANTS > Get a single merchant**.
2. In the Authentication header > Bearer type field, enter your access token. The access token is the [test API token](https://docs.clover.com/docs/generate-a-test-api-token#generate-a-merchant-specific-test-api-token-in-sandbox) that you have generated in the sandbox Developer Dashboard.
3. In the Path Params section, enter your test <<glossary:merchantId>> in the `mId` field. Your test merchant ID is a 13-alphanumeric identifier that displays in the browser link (URL) of the Merchant Dashboard for your test merchant. See [Locate your test merchant ID](https://docs.clover.com/docs/merchant-id-and-api-token-for-development#locate-the-test-merchant-identifier-merchantid).
4. Click **Try It**. In the JSON output response, the `name` value is your test merchant’s name.

***

# Sample REST API requests

To test Clover REST APIs:

1. Set the Authorization header as Bearer token type, and enter the `auth_token`.
2. Include the merchantId in the request URL in place of `{mId}`.

To retrieve information about your test merchant, send a `GET` request to `/v3/merchants/mId`:

```curl Retrieve test merchant information
curl --request GET \
  --url 'https://apisandbox.dev.clover.com/v3/merchants/{mId}' \
  --header 'accept: application/json' \  
  --header 'authorization: Bearer {auth_token}'
```

In this request,

- `mId` is the test merchant's universally unique identifier (UUID), also known as the `merchantId`
- `auth_token` is the test API token or access token. See [Use test merchant IDs and API tokens](doc:merchant-id-and-api-token-for-development) for more information.

To update your test merchant's name, send a `POST` request to `/v3/merchants/mId`:

```curl Update test merchant name
curl --request POST \
  --url 'https://apisandbox.dev.clover.com/v3/merchants/{mId}' \
  --header 'accept: application/json' \  
  --header 'authorization: Bearer {auth_token}'
  --data '{"name":"{updated_merchant_name}"}'
```

# Set additional query parameters

To retrieve more information from your REST API requests, set query parameters for supported endpoints in the following format.

```curl
[Endpoint URI]?field=value[,additionalValues...]&[additionalQueryParameters...]
```

In the API documentation, the Query Params section lists the additional parameters available. For example, use the `expand` query parameter for additional information about a merchant.

```curl
curl --request GET \
  --url 'https://apisandbox.dev.clover.com/v3/merchants/{mId}?expand=openingHours' \
  --header 'accept: application/json' \  
  --header 'authorization: Bearer {auth_token}'
```

See [Use expandable fields](doc:expanding-fields) for more information.
