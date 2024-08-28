---
title: "Legacy token migration flow"
slug: "legacy-token-migration-flow"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to migrate legacy API tokens to new access and refresh token pairs, including the option to use Proof Key for Code Exchange (PKCE)."
  image: []
  robots: "index"
createdAt: "Mon Jun 05 2023 02:15:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 09 2024 09:16:23 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Learn how to migrate legacy API tokens to new access and refresh token pairs, including the option to use Proof Key for Code Exchange (PKCE).">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Developers who have an app with a non-expiring token need to exchange their app’s legacy API token for an expiring access and refresh token pair. The token migration flow includes the option to use Proof key for code exchange (PKCE).   

# Token migration flow with PKCE option

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8b3484b-Legacy_Token_Migration_Flow.png",
        null,
        "Token migration flow"
      ],
      "align": "center",
      "sizing": "70% ",
      "caption": "Token migration flow"
    }
  ]
}
[/block]


# Migrate legacy tokens

> 🚧 IMPORTANT
> 
> The following values for access and refresh tokens are dynamic and can change:
> 
> - Token expiration displays in the response body. Tokens created later can have different durations until they expire. 
> - Token lengths are not fixed.
> 
> Do not hard code access and refresh token expirations or lengths so that you can handle any future updates.

To exchange a legacy token for a new access and refresh token pair:

[block:parameters]
{
  "data": {
    "h-0": "Step",
    "h-1": "Who/what",
    "h-2": "What",
    "0-0": "1",
    "0-1": "Developer app",
    "0-2": "If using PKCE, generate a `code_verifier` and `code_challenge` using the method of your choice.",
    "1-0": "2",
    "1-1": "Developer app",
    "1-2": "Request an authorization code.  \n  \nSend a POST request to `/oauth/token/migrate_v2`. Include the merchant ID, app ID, legacy API token, and if using PKCE, code challenge in the request body.  \n  \n**Request**  \nPOST /oauth/token/migrate_v2  \n  \n**Request body**  \n{  \n  <code>    </code>\"merchant_uuid\": \"{MERCHANT_ID}\",  \n  <code>    </code>\"app_uuid\": \"{APP_ID}\",  \n  <code>    </code>\"auth_token\": \"{LEGACY_API_TOKEN}\"  \n  <code>    </code>\"code_challenge\": \"{CODE_CHALLENGE}\"  \n}",
    "2-0": "3",
    "2-1": "Clover backend",
    "2-2": "Return authorization code.  \n  \n**Sample response body**  \n{  \n  <code>    </code>\"authorization_code\": \"{AUTHORIZATION_CODE}\",  \n  <code>    </code>\"expiration\": 1678489882  \n}",
    "3-0": "4",
    "3-1": "Developer app",
    "3-2": "Request an access token pair.  \n  \nSend a POST request to `/oauth/v2/token`. Include the client ID, client secret (if a high trust app), auth code, and if using PKCE, code verifier in the request body.  \n  \n**Request**  \nPOST /oauth/v2/token  \n  \n**Request body**  \n{  \n    <code>    </code>\"client_id\": \"{APP_ID}\"  \n    <code>    </code>\"client_secret\": \"{APP_SECRET}\",    -> If a high trust app  \n    <code>    </code>\"code\": \"{AUTHORIZATION_CODE}\",  \n    <code>    </code>\"code_verifier\": \"{CODE_VERIFIER}\"   -> If using PKCE  \n}  ",
    "4-0": "5",
    "4-1": "Clover backend",
    "4-2": "Return new access and refresh tokens.  \n  \n**Sample response body**  \n{  \n    <code>    </code>\"access_token\": \"{ACCESS_TOKEN}\",  \n    <code>    </code>\"access_token_expiration\": 1677875430,  \n    <code>    </code>\"refresh_token\": \"{REFRESH_TOKEN}\",  \n    <code>    </code>\"refresh_token_expiration\": 1709497830  \n}  \n**Note:** The response body indicates when the access and refresh tokens expire. The expiration dates are represented as Unix timestamps."
  },
  "cols": 3,
  "rows": 5,
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
