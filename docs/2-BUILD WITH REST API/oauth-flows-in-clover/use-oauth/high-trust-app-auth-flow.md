---
title: "High trust apps—Auth code flow"
slug: "high-trust-app-auth-flow"
excerpt: ""
hidden: false
metadata: 
  title: "Auth code flow for high trust apps"
  description: "Learn how to generate access and refresh tokens for high trust apps."
  image: []
  robots: "index"
createdAt: "Wed May 31 2023 17:01:29 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 09 2024 09:00:18 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Learn how to generate access and refresh tokens for high trust apps.">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

High trust apps securely store and use a client secret (app secret), as shown in the diagram. 

# Auth code flow for high trust apps

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/747657b-Auth_Code_Flow_High_Trust_Apps_.png",
        null,
        "Auth code flow for high trust apps"
      ],
      "align": "center",
      "caption": "Auth code flow for high trust apps"
    }
  ]
}
[/block]


# Generate access and refresh tokens

> 🚧 IMPORTANT
> 
> The following values for access and refresh tokens are dynamic and can change:
> 
> - Token expiration displays in the response body. Tokens created later can have different durations until they expire. 
> - Token lengths are not fixed.
> 
> Do not hard code access and refresh token expirations or lengths so that you can handle any future updates.

To generate an access and refresh token pair: 

[block:parameters]
{
  "data": {
    "h-0": "Step",
    "h-1": "Who/what",
    "h-2": "What",
    "0-0": "1",
    "0-1": "Merchant",
    "0-2": "Log in to the merchant Clover account and install the developer’s app from the [Clover App Market](https://www.clover.com/appmarket).  \n  \nBy installing the app, the merchant authorizes the app to access the merchant’s information that the app requires.",
    "1-0": "2",
    "1-1": "Clover UI",
    "1-2": "Redirect the merchant to the developer’s app with an authorization code.  \nExample:  \n<https://www.example.com/oauth_callback?merchant_id={MERCHANT_ID}&client_id={APP_ID}&code={AUTHORIZATION_CODE}>  \n  \n**NOTE:** If the merchant is not logged in to their Clover merchant account and they try to access to your app, Clover redirects the merchant to log in to their merchant account and back to your app.  \nExample:  \n<https://sandbox.dev.clover.com/oauth/v2/authorize?client_id={APP_ID}&redirect_uri={CLIENT_REDIRECT_URL}>",
    "2-0": "3",
    "2-1": "Developer app",
    "2-2": "Request an access- and refresh-token pair.  \n  \nSend a POST request to `/oauth/v2/token`. Include the client ID, client secret, and auth code in the request body.  \n  \n**Request**  \nPOST /oauth/v2/token  \n  \n**Query parameter—Optional**  \nIf you do not need a refresh token, set the query parameter  `no_refresh_token` to **true** in the request:  \n`/oauth/v2/token?no_refresh_token=true`  \n  \nSee [When refresh tokens are not needed](https://docs.clover.com/docs/refresh-access-tokens#when-refresh-tokens-are-not-needed) for more information.  \n  \n**Request body**  \n  \n{  \n       <code>   </code>\"client_id\": \"{APP_ID}\"  \n       <code>   </code>\"client_secret\": \"{APP_SECRET}\",  \n       <code>   </code>\"code\": \"{AUTHORIZATION_CODE}\"  \n}",
    "3-0": "4",
    "3-1": "Clover backend",
    "3-2": "Return an access and refresh token pair.  \n  \n**Sample response body**  \n  \n{  \n    <code>   </code>\"access_token\": \"{ACCESS_TOKEN}\",  \n    <code>   </code>\"access_token_expiration\": 1677875430,  \n    <code>   </code>\"refresh_token\": \"{REFRESH_TOKEN}\",  \n    <code>   </code>\"refresh_token_expiration\": 1709497830  \n}  \n  \nExpiration dates are represented as Unix timestamps."
  },
  "cols": 3,
  "rows": 4,
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
