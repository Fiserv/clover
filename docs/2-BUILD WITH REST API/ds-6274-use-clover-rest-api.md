---
title: "DS-6274-Use Clover REST API"
slug: "ds-6274-use-clover-rest-api"
excerpt: ""
hidden: true
createdAt: "Wed Aug 07 2024 07:08:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Aug 07 2024 09:28:49 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Learn about the important parameters required to make a sample Clover REST API call.”>"
}
[/block]


[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to the partner \ndoc. -->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# Overview

The Clover REST API lets you query relevant information about Clover merchants, such as inventory, orders, and payments. You can build a browser-based integration that uses our REST API along with the relevant OAuth flow. 

In the Clover REST API, each endpoint indicates a type of merchant information. The base URLs for building and testing your apps are different in the sandbox and production environments. Supported endpoints in the Clover [REST API Reference](https://docs.clover.com/reference) accept query parameters in the following format:

```http REST API query parameter syntax
[Endpoint URI]?field=value[,additionalValues...]&[additionalQueryStrings...]
```

## Environment base URLs

| Environment            | Description                                                                                                                                                              | Base URL                                                                                                                                |
| :--------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------- |
| Sandbox environment    | Use the sandbox REST API with the [Android emulator](doc:setting-up-an-android-emulator)  or with our [Developer Kits](doc:clover-dev-kits)  and sandbox test merchants. | '<https://apisandbox.dev.clover.com'>                                                                                                   |
| Production environment | Use a separate base URL in production for each of the Clover [supported markets](https://docs.clover.com/launch/multiple-markets/).                                      | - United States and Canada: `https://api.clover.com` - Europe: `https://api.eu.clover.com` - Latin America: `https://api.la.clover.com` |

## Key information

Here is some key information about the Clover REST API:

| Term        | Description                                                                                                                                                      |
| :---------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| HTTPS       | Clover API is only accessible through HTTPS.                                                                                                                     |
| JSON        | Request and response entities are in JSON.                                                                                                                       |
| OAuth       | All API requests in production are protected by an OAuth2-derived access token. See [OAuth flows in Clover](https://docs.clover.com/docs/oauth-flows-in-clover). |
| Permissions | Using Clover API endpoints requires access to necessary permissions. See Platform API permissions and E-Commerce API permissions for more information.           |

# Sample REST API requests

To retrieve information about your test merchant, send a `GET` request to `/v3/merchants/mId`:

```curl
curl --request GET \
  --url https://apisandbox.dev.clover.com/v3/merchants/{mId} \
  --header 'accept: application/json' \  
  --header 'authorization: Bearer {auth_token}'
```

To update the test merchant name, send a `POST` request to /v3/merchants/mId\`:

```curl
curl --request POST \
  --url https://apisandbox.dev.clover.com/v3/merchants/{mId} \
  --header 'accept: application/json' \  
  --header 'authorization: Bearer {auth_token}'
  --data '{"name":"{updated_merchant_name}"}'
```

In both requests:

- `mId` is the test merchant's universally unique identifier (UUID), also known as the merchantId.
- `auth_token` is the API token (or access token).

See [Use test merchant identifier and API token](doc:merchant-id-and-api-token-for-development) for more information.
