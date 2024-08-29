---
title: "Use test API tokens in sandbox"
slug: "using-api-tokens"
excerpt: ""
hidden: false
metadata: 
  description: "Your app must pass a valid API token with each request. The way this token is passed can vary depending on the Clover environment and the way your app is designed to make API calls."
  image: 
    - "https://files.readme.io/ced2fcb-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Sep 07 2018 02:57:27 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Aug 12 2024 05:01:55 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Your app must pass a valid API token with each request. The way this token is passed can vary depending on the Clover environment and the way your app is designed to make API calls.”>"
}
[/block]


<!-- DS-6274 Aug 7, 2024 - Aneesha - Updated format and text. The general flow of topics is: 1. Clover REST API Basics 2. Clover REST API overview 3. Use API tokens in sandbox 4. Use test merchant identifier 5. Make a sample REST API call. A new Index topic has been added to organize the tutorials. -->

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Clover uses the [OAuth 2.0](https://docs.clover.com/docs/oauth-flows-in-clover) security framework for third-party developers to authenticate their apps with merchant accounts and lets them use Clover public REST APIs on behalf of the merchant. 

# Use API tokens for testing in sandbox

When you test your app in the [sandbox environment](https://docs.clover.com/docs/get-started-with-sandbox-environment#), you can [generate and use API tokens](https://docs.clover.com/docs/generate-a-test-api-token) instead of access and refresh tokens that you need in the production environment.  You can use the API token to test Clover REST APIs from the command line. 

# Prerequisites

When you make server-side requests to Clover REST APIs, you need the following:

- `Authorization` header with a type of <<glossary:Bearer token>> token, where you need to enter your  `{API_Token}`.
- Merchant identifier or <<glossary:merchantId>> that displays in the browser link (URL) of the Merchant Dashboard for your test merchant.

With this information, you can send the following request from your app server to the Clover server. 

```text Sandbox URL with merchantId
https://apisandbox.dev.clover.com/v3/merchants/{mId}
```

See [Use test merchant identifier and API token](doc:merchant-id-and-api-token-for-development) for more information.

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

***

> 📘 NOTE
> 
> You need to use expiring access and refresh tokens in the [production environment](https://docs.clover.com/docs/clover-app-approval-process) to secure merchant data. When your app is ready for testing in the production environment, use the following.
> 
> - For Web apps: Use the relevant [OAuth flow based on regions](https://docs.clover.com/docs/oauth-flows-in-clover#oauth-flows-based-on-regions) to generate an `auth_token`.
> - For Android apps: Use the Android SDK to generate an [API token and query web services](https://docs.clover.com/docs/query-web-services).
