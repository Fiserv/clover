---
title: "Refresh access tokens"
slug: "refresh-access-tokens"
excerpt: ""
hidden: false
metadata: 
  title: "Refresh access tokens"
  description: "Learn how to refresh access tokens for your apps."
  image: []
  robots: "index"
createdAt: "Wed Jun 14 2023 17:32:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 09 2024 09:14:36 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Learn how to refresh access tokens for your apps.">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

To prevent your app from becoming unauthorized, your app uses the refresh token. The auth code flow generates new access and refresh tokens before the current tokens expire.

> 🚧 IMPORTANT
> 
> Limits apply to the number of refresh tokens that the auth code flow can create per merchant-app combination. If an app exceeds the limit, older tokens become invalid.

You can only use refresh tokens once, and they become invalid after use. A new refresh token is generated during the refresh process and returned in the response body. When you generate new access and refresh tokens, use the new refresh token in the request.

## Generate new access and refresh tokens

> 🚧 IMPORTANT
> 
> The following values for access and refresh tokens are dynamic and can change:
> 
> - Token expiration displays in the response body. Tokens created later can have different durations until they expire. 
> - Token lengths are not fixed.
> 
> Do not hard code access and refresh token expirations or lengths so that you can handle any future updates.

To generate new access and refresh tokens:

[block:parameters]
{
  "data": {
    "h-0": "Step",
    "h-1": "Who/what",
    "h-2": "What",
    "0-0": "1",
    "0-1": "Developer app",
    "0-2": "Send a POST request to the `/oauth/v2/refresh` endpoint. Include the client ID and refresh token from the auth code flow response.  \n  \n**Request**  \nPOST /oauth/v2/refresh  \n  \n**Request body**  \n  \n{  \n    <code>    </code>\"client_id\": \"{APP_ID}\",  \n    <code>    </code>\"refresh_token\": \"{REFRESH_TOKEN}\"  \n}  \n  \n**Sample response body**  \n  \n{  \n    <code>    </code>\"access_token\": \"{ACCESS_TOKEN}\",  \n    <code>    </code>\"access_token_expiration\": 1709498373,  \n    <code>    </code>\"refresh_token\": \"{REFRESH_TOKEN}\",  \n    <code>    </code>\"refresh_token_expiration\": 1741034373  \n}  \n  \n**Note:** The response body indicates when the access and refresh tokens expire. The expiration dates are represented as Unix timestamps."
  },
  "cols": 3,
  "rows": 1,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Bypass refresh token creation in the OAuth flow

Clover limits the number of active refresh tokens that an application can have for each merchant. In some scenarios, a refresh token is not needed: 

- Frontend apps that use OAuth to authenticate users to their own apps often don’t need a refresh token.
- Some apps only need the access token to verify that the user successfully authenticated with Clover and then use that token to get details from the API.

Generating a refresh token in such cases may cause the app to reach the limit unnecessarily. Use the `no_refresh_token` flag on the OAuth Authorize endpoint to bypass the refresh token creation.

To bypass generating a refresh token for your app:

[block:parameters]
{
  "data": {
    "h-0": "Step",
    "h-1": "Who/what",
    "h-2": "What",
    "0-0": "1",
    "0-1": "Developer app",
    "0-2": "Send a POST request to the `/oauth/v2/token`  \nendpoint. Set the `no_refresh_token` flag to true.  \n  \n**Request**  \nPOST /oauth/v2/token?no_refresh_token=true  \n  \n**Request body**  \n  \n{  \n    <code>    </code>\"code\": \"{AUTHORIZATION_CODE}\",  \n    <code>    </code>\"client_id\": \"{APP_ID}\",  \n    <code>    </code>\"client_secret\": \"{APP_SECRET}\"  \n}  \n  \n**Sample response body**  \n  \n{  \n   <code>    </code>\"access_token\": \"{ACCESS_TOKEN}\",  \n   <code>    </code>\"access_token_expiration\": 1709498373,  \n}  \n  \nA refresh token is not returned.  \n  \n**Note:** The response body indicates when the access and refresh tokens expire. The expiration dates are represented as Unix timestamps."
  },
  "cols": 3,
  "rows": 1,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


> 📘 NOTE
> 
> See [Sandbox and production environments URLs](https://docs.clover.com/docs/oauth-intro#sandbox-and-production-environment-urls) about which URLs to use in the requests.
