---
title: "Use Clover REST API"
slug: "making-rest-api-calls"
excerpt: ""
hidden: false
metadata: 
  description: "Learn about the important parameters required to make a sample Clover REST API call."
  image: []
  robots: "index"
createdAt: "Mon Jun 25 2018 21:23:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Aug 09 2024 08:52:38 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Learn about the important parameters required to make a sample Clover REST API call.”>"
}
[/block]


[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to the partner \ndoc. -->\n<!--DS-6274 Aug 7, 2024 - Aneesha - Updated format and text to make this an overview topic. Removed the sample code and added it to Use API tokens topic as it makes more sense there.--> \n"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# Overview

The Clover REST API lets you query relevant information about Clover merchants, such as inventory, orders, and payments. You can build a browser-based integration that uses our REST API along with the relevant OAuth flow. 

In the Clover REST API, each endpoint indicates a type of merchant information. The base URLs for building and testing your apps are different in the sandbox and production environments. Supported endpoints in the Clover [REST API Reference](https://docs.clover.com/reference) accept query parameters in the following format:

```http REST API query parameter syntax
[Endpoint URI]?field=value[,additionalValues...]&[additionalQueryStrings...]
```

# Environment base URLs

[block:parameters]
{
  "data": {
    "h-0": "Environment",
    "h-1": "Base URL",
    "h-2": "Description",
    "h-3": "Token type",
    "0-0": "[Sandbox environment](https://docs.clover.com/docs/get-started-with-sandbox-environment)",
    "0-1": "`https://apisandbox.dev.clover.com`",
    "0-2": "Use the sandbox REST API with the [Android emulator](doc:setting-up-an-android-emulator)  or with our [Developer Kits](doc:clover-dev-kits) and sandbox test merchants.",
    "0-3": "To test your app in the sandbox environment, you can [generate and use merchant-specific test API tokens](https://docs.clover.com/docs/generate-a-test-api-token) instead of access and refresh tokens.",
    "1-0": "[Production environment](https://docs.clover.com/docs/clover-app-approval-process)",
    "1-1": "- United States and Canada: `https://api.clover.com`  \n- Europe: `https://api.eu.clover.com`  \n- Latin America: `https://api.la.clover.com`",
    "1-2": "Use a separate base URL in production for each of the Clover [supported markets](https://docs.clover.com/launch/multiple-markets/).",
    "1-3": "Use access and refresh tokens following the region-specific [OAuth flow](https://docs.clover.com/docs/oauth-flows-in-clover) to secure merchant data.  \n**Note: **Do not use the test merchant API tokens in the production environment."
  },
  "cols": 4,
  "rows": 2,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


# Key information

Here is some key information about the Clover REST API and using the API Reference to make requests:

| Term            | Description                                                                                                                                                                                                                                                                                                                                                          |
| :-------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| API tokens      | API tokens are used to authenticate requests to Clover REST APIs. Generating an API token is a fundamental part of the OAuth flow to enable secure, controlled, and auditable access to APIs. For more information, see [API tokens for test and published apps](https://docs.clover.com/docs/generate-a-test-api-token#api-tokens-for-test-and-published-apps).     |
| HTTPS           | Clover REST API is only accessible through HTTPS.                                                                                                                                                                                                                                                                                                                    |
| JSON            | Request and response entities are in JSON.                                                                                                                                                                                                                                                                                                                           |
| OAuth           | Clover uses the [OAuth 2.0](https://docs.clover.com/docs/oauth-flows-in-clover) security framework for third-party developers to authenticate their apps with merchant accounts and lets them use Clover public REST APIs on behalf of the merchant. Clover developers use expiring access and refresh tokens in the production environment to secure merchant data. |
| Permissions     | Using Clover API endpoints requires access to necessary permissions. See [Platform API permissions](doc:permissions)  and [E-Commerce API permissions](doc:ecommerce-app-permissions)  for more information.                                                                                                                                                         |
| Required inputs | The merchant identifier `merchantId` and the test API token are required for you to test interactions with Clover REST API and for Android development. For more information, see [Use API tokens in sandbox](https://docs.clover.com/docs/using-api-tokens).                                                                                                        |

# Related topics

- [Generate a merchant-specific test API token](https://docs.clover.com/docs/generate-a-test-api-token)
- [Use test merchant identifier and API token](https://docs.clover.com/docs/merchant-id-and-api-token-for-development)
- [Make a sample REST API call](https://docs.clover.com/docs/make-a-rest-api-call)
- [Redirect merchants to your app](https://docs.clover.com/docs/merchant-interaction)
