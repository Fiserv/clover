---
title: "DS-5379-Arpit-API Reference overview"
slug: "api-reference-overview-copy"
excerpt: ""
hidden: true
createdAt: "Thu Dec 14 2023 08:07:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Dec 14 2023 08:08:05 GMT+0000 (Coordinated Universal Time)"
---
Welcome to the Clover platform REST API reference. This reference describes the function of each REST API endpoint in the sandbox environment.

# Prerequisites

See [Get started](https://docs.clover.com/docs/select-an-integration) for more information about setting up your developer account and retrieving your first API token. The API token provides the necessary permissions to access test merchant data. To learn more, see our blog post [Fiddling Through Digital Keys: Clover Auth Tokens and Ecommerce Keys](https://medium.com/clover-platform-blog/understanding-clover-auth-tokens-and-ecommerce-keys-4e048827afa2)

To use the Clover platform API, you require the following:

- <a href="https://sandbox.dev.clover.com/developer-home/create-account" target="_blank">Sandbox developer account</a>
- [Test merchant account](https://docs.clover.com/docs/use-test-merchants-dashboard)
- API token with permissions to make REST API requests and manage your test merchant's data

# Use the API reference

To make a sample REST API call:

1. Select **MERCHANTS > Get a single merchant**.
2. In the Path Params section, enter your test merchant ID in the mId field. Your test merchant ID is a 13-character sequence of numbers. See [Locate your test merchant ID](doc:merchant-id-and-api-token-for-development#section-finding-your-test-merchant-id) for more information.
3. In the Authentication section, enter your access token in the Bearer field. This value is the [test API token](doc:create-an-api-token#section-generating-an-api-token) you generated in the sandbox Developer Dashboard.
4. Click **Try It**. In the JSON output response, the `name` value is your test merchant’s name.

# Sample REST API requests

To retrieve information about your test merchant, send a `GET` request to `/v3/merchants/mId`:

Retrieve test merchant information

```curl
curl --request GET \
  --url 'https://sandbox.dev.clover.com/v3/merchants/{mId}' \
  --header 'accept: application/json' \  
  --header 'authorization: Bearer {auth_token}'
```

To update your test merchant's name, send a `POST` request to `/v3/merchants/mId`:

Update test merchant name

```curl
curl --request POST \
  --url 'https://sandbox.dev.clover.com/v3/merchants/{mId}' \
  --header 'accept: application/json' \  
  --header 'authorization: Bearer {auth_token}'
  --data '{"name":"{updated_merchant_name}"}'
```

> 📘 TIP
> 
> In the sample request, `mId` is the test merchant UUID (Universally unique identifier) and `auth_token` is the API token (or access token).

# Set additional query parameters

To retrieve more information from your REST API requests, set query parameters for supported endpoints in the following format:

```text REST API query parameter syntax
[Endpoint URI]?field=value[,additionalValues...]&[additionalQueryParameters...]
```

In the API documentation, the QUERY PARAMS section displays additional parameters for an endpoint. For example, use the `expand` query parameter for additional information about a merchant.

```curl
curl --request GET \
  --url 'https://sandbox.dev.clover.com/v3/merchants/{mId}?expand=openingHours' \
  --header 'accept: application/json' \  
  --header 'authorization: Bearer {auth_token}'
```

See [Expanding Fields](https://docs.clover.com/docs/expanding-fields) for more information.

# Sandbox base URLs

Use the [Android emulator](https://docs.clover.com/docs/setting-up-an-android-emulator) or [Developer Kits](https://cloverdevkit.com/) in the sandbox environment for building and testing your apps with test merchants. In the sandbox environment, Clover provides base URLs for different services.

- Platform API: `https://sandbox.dev.clover.com`
- Tokenization service API: `https://token-sandbox.dev.clover.com`
- Ecommerce service API: `https://scl-sandbox.dev.clover.com` 

See the [Ecommerce API tutorials](doc:clover-development-basics-ecommerce) for more information.

> 📘 NOTE
> 
> Ecommerce API and all related features are currently available in the US and Canada. We will provide updated information as Clover extends its availability to more regions.

# Production base URLs

In the production environment, Clover provides base URLs for different services in [supported markets](https://docs.clover.com/docs/multiple-markets).

[block:parameters]
{
  "data": {
    "h-0": "Environment",
    "h-1": "Base URL",
    "0-0": "Sandbox",
    "0-1": "`https://sandbox.dev.clover.com`",
    "1-0": "Production",
    "1-1": "United States & Canada: `https://api.clover.com`  \nEurope: `https://api.eu.clover.com`  \nLatin America: `https://api.la.clover.com`  \nTokenization service API: `https://token.clover.com`  \nEcommerce service API: `https://scl.clover.com`"
  },
  "cols": 2,
  "rows": 2,
  "align": [
    "left",
    "left"
  ]
}
[/block]
