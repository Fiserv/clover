---
title: "Low trust apps—Auth code flow with PKCE"
slug: "oauth-flow-for-low-trust-apps-pkce"
excerpt: ""
hidden: false
metadata: 
  title: "Auth code flow with PKCE for low trust apps"
  description: "Learn how to use the auth code flow with PKCE for low trust apps."
  image: []
  robots: "index"
createdAt: "Mon Jun 05 2023 18:11:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 09 2024 09:02:03 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Learn how to use the auth code flow with PKCE for low trust apps.">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

If your app is a mobile, single-page, or native desktop application, it can not safely store the client's secret and is a low trust app. Therefore, the app must use the auth flow with a proof key for code exchange (PKCE), as shown in the diagram.

# Auth code flow with PKCE for low trust apps

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c560dc3-Auth_Code_Flow_with_PKCE_for_Low_Trust_Apps.png",
        null,
        "Auth code flow with PKCE for low trust apps"
      ],
      "align": "center",
      "caption": "Auth code flow with PKCE for low trust apps"
    }
  ]
}
[/block]


# Generate an access and refresh token pair using PKCE

> 🚧 IMPORTANT
> 
> The following values for access and refresh tokens are dynamic and can change:
> 
> - Token expiration displays in the response body. Tokens created later can have different durations until they expire. 
> - Token lengths are not fixed.
> 
> Do not hard code access and refresh token expirations or lengths so that you can handle any future updates.

To create an access and refresh token pair using PKCE:

[block:parameters]
{
  "data": {
    "h-0": "Step",
    "h-1": "Who/what",
    "h-2": "What",
    "0-0": "1",
    "0-1": "Developer app",
    "0-2": "Generate a `code_verifier` and `code_challenge` as shown in the [flow diagram](https://docs.clover.com/docs/oauth-flow-for-low-trust-apps-pkce#auth-code-flow-with-pkce-for-low-trust-apps). The `code_verifier` must be a random string value, and the `code_challenge` must be a SHA256 hash of the `code_verifier`. ",
    "1-0": "2",
    "1-1": "Developer app",
    "1-2": "Redirect the merchant to `/oauth/v2/authorize` with the `code_challenge`.",
    "2-0": "3",
    "2-1": "Merchant",
    "2-2": "Log in to the merchant Clover account and install the developer’s app from the [Clover App Market](https://www.clover.com/appmarket).  \n  \nBy installing the app, the merchant authorizes the app to access the merchant’s information that the app requires.",
    "3-0": "4",
    "3-1": "Clover backend",
    "3-2": "Redirect the merchant to the developer’s app with an authorization code.  \nExample:  \n<https://www.example.com/oauth_callback?merchant_id={MERCHANT_ID}&client_id={APP_ID}&code={AUTHORIZATION_CODE}>",
    "4-0": "5",
    "4-1": "Developer app",
    "4-2": "Request an access and refresh token pair.  \n  \nSend a POST request to `/oauth/v2/token`. Include the client ID, auth code, and code verifier in the request body.  \n  \n**Request**  \nPOST /oauth/v2/token  \n  \n**Request body**  \n{  \n    <code>    </code>\"client_id\": \"{APP_ID}\",  \n    <code>    </code>\"code\": \"{AUTHORIZATION_CODE}\",  \n    <code>    </code>\"code_verifier\": \"{CODE_VERIFIER}\"\\`  \n}",
    "5-0": "6",
    "5-1": "Clover backend",
    "5-2": "Return an access and refresh token pair.  \n  \n**Sample response body**  \n  \n{  \n    <code>    </code>\"access_token\": \"{ACCESS_TOKEN}\",  \n    <code>    </code>\"access_token_expiration\": 1677875430,  \n    <code>    </code>\"refresh_token\": \"{REFRESH_TOKEN}\",  \n    <code>    </code>\"refresh_token_expiration\": 1709497830  \n}  \n  \n**Note:** The response body indicates when the access and refresh tokens expire. The expiration dates are represented as Unix timestamps."
  },
  "cols": 3,
  "rows": 6,
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
