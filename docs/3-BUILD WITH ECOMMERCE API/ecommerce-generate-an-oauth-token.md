---
title: "Get an OAuth token"
slug: "ecommerce-generate-an-oauth-token"
excerpt: ""
hidden: true
createdAt: "Tue Aug 13 2024 13:02:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Aug 14 2024 10:51:13 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="....>

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

<meta name=" description" content="Learn about the OAuth API token. You need the token to secure the communication between your app and the merchant, and then to give your app the required permissions to access the merchant's data." >

# Overview

To secure communication between your app and the merchant, you need an OAuth API token. The OAuth token is required to:

- Complete the Ecommerce API authorization flow that grants your app the necessary permissions to access the merchant’s data. 
- Generate a PAKMS key or `apiAccessKey`, from the Public Access Key Management Service (PAKMS). The PAKMS key identifies the merchant who is tokenizing the customers' cards. You can use the same static PAKMS key to tokenize multiple cards for that merchant.

There are two ways to generate an OAuth API token:

- In the legacy v1 OAuth flow for apps created before August 2024, and not migrated to using expiring tokens, this API token is known as an `auth_token`. See[ Generate API token with the legacy OAuth flow](https://docs.clover.com/docs/ecommerce-generate-an-oauth-token#generate-api-token-with-the-legacy-oauth-flow).
- In the v2 OAuth flow for all new apps created after August 2024, this OAuth API token is an expiring token, which is an `access_token` and `refresh token` combination. See [Generate OAuth expiring (access and refresh) token](https://docs.clover.com/docs/ecommerce-generate-an-oauth-token#generate-oauth-expiring-access-and-refresh-token).

# Terminology

The following terms are used in the OAuth flow to generate an OAuth token:

**Legacy v1 OAuth flow**

[block:parameters]
{
  "data": {
    "h-0": "Term",
    "h-1": "Description",
    "0-0": "Client ID or App ID",
    "0-1": "App ID or Client ID that uniquely identifies an app on Clover App Market. This ID is also used to confirm that your app is participating in the OAuth 2.0 flow.",
    "1-0": "Client Secret or App Secret",
    "1-1": "App Secret or Client Secret is a secret key that Clover assigns to your app. Do not share the Client Secret key publicly.  \n  \n**Note: **Both the App ID and App Secret are automatically assigned when you create an app. You can view the App ID and App Secret on the [_App name_ - App Settings page](https://docs.clover.com/docs/app-settings#access-settings-for-your-app).  Both these values are required for you to authenticate your app with the Clover server and make authorized and authenticated requests to Clover merchant data.",
    "2-0": "Merchant ID",
    "2-1": "Merchant identifier or `merchantId` that uniquely identifies Clover merchants, including test merchants, on the Clover platform. See [Locate the test merchant identifier (merchantId)](https://docs.clover.com/docs/merchant-id-and-api-token-for-development#section-locate-your-test-merchant-id).",
    "3-0": "Authorization Code",
    "3-1": "An authorized merchant who has signed into Clover is redirected to your app along with an authorization code. The authorization code is a temporary code that the Clover server provides after the merchant is authenticated. This code is exchanged for an access token during the [OAuth flow](https://docs.clover.com/docs/oauth-flows-in-clover#oauth-flows-based-on-regions).",
    "4-0": "API Token",
    "4-1": "Your app uses the Authorization Code, Client ID, and Client Secret to negotiate with the Clover server for an API token. With the API token, your app can make REST API calls and access merchant data. See [Use Clover REST API](https://docs.clover.com/docs/making-rest-api-calls)."
  },
  "cols": 2,
  "rows": 5,
  "align": [
    "left",
    "left"
  ]
}
[/block]


**Expiring (access and refresh tokens) v2 OAuth flow**

[block:parameters]
{
  "data": {
    "h-0": "Term",
    "h-1": "Description",
    "0-0": "Access token  \n`access_token`",
    "0-1": "Tokens to access Clover APIs. Access tokens expire after a period of time.",
    "1-0": "Refresh token  \n`refresh_token`",
    "1-1": "Token used to generate more access tokens. It is a one-time-use token used to generate another access token when it expires. Refresh tokens expire, but they are valid for a longer period of time than the access token.  \nRefresh tokens tend to accumulate in the database and can cause performance issues or other technical maintenance issues. Clover sets a limit on the number of refresh tokens a single application can have active for each merchant.",
    "2-0": "Alternate Launch Path",
    "2-1": "Lets you configure an alternate launch path link or URL for your app in the Edit REST Configuration page for web apps. See [Add web app settings](https://docs.clover.com/docs/app-settings#add-web-app-settings) . Your merchant is redirected to this link after they install and launch the app from the Merchant Dashboard. This alternate path URL:  \n  \n- Uses the expiring authentication tokens to authenticate with APIs.  \n- Sends the merchant directly to your app and initiates the OAuth flow. See Initiate OAuth flow from Merchant Dashboard left navigation app link."
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]


# Prerequisites

Before you can get an OAuth API token, you need to complete the following tasks: 

1. [Create a global developer account](https://docs.clover.com/docs/gdp-create-global-developer-account).
2. [Manage test merchant accounts and information](https://docs.clover.com/docs/gdp-manage-test-merchants-accounts).
3. [Create your app](https://docs.clover.com/docs/gdp-create-new-app) in the sandbox environment.
4. Configure [settings](https://docs.clover.com/docs/app-settings) and [permissions](https://docs.clover.com/docs/app-settings#edit-requested-permissions) that your app requires to access Clover merchant data. For more information, see [Ecommerce app permissions](https://docs.clover.com/docs/ecommerce-app-permissions).

In production, your application server needs to handle the merchant user, who is redirected from Clover to your server, once they connect to your app. To build the OAuth flow for apps on the [Clover App Market](https://www.clover.com/appmarket), in production environments, replace `https://sandbox.dev.clover.com/` with the base URL in your requests for United States (US) and Canada: `https://www.clover.com/`

# Generate API token with the legacy OAuth flow

1. Log in to the [Global Developer Dashboard](https://www.clover.com/fusionauth/oauth2/authorize?client_id=8c4b9ac9-c55b-4ee1-b978-30ea9edbf552&response_type=code&redirect_uri=https%3A%2F%2Fwww.clover.com%2Fglobaldeveloperexperience%2Fcallbacks%2Fredirect-login&scope=openid%20offline_access).
2. Navigate to the Merchant Dashboard for your test merchant.
3. From the left navigation menu, select your test application. Clover redirects to your application.
4. If you have not yet coded your application server to handle the redirect and obtain an access token, note the `client_id` and the `code` in the URL. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f5a7788-rest_pay_client_id_and_code.png",
        "rest_pay_client_id_and_code.png",
        2120
      ],
      "align": "center",
      "sizing": "smart",
      "border": true
    }
  ]
}
[/block]


5. Send an API token GET request in the following URL format to the Clover /oauth/token server, passing the `client_id`, your `client_secret`, and `code`:

```text API token request URL format
https://sandbox.dev.clover.com/oauth/token?client_id={appId}&client_secret={APP_SECRET}&code={AUTHORIZATION_CODE}
```

The response displays your API access token.

```json API token response from server
{
   "access_token":"{API_TOKEN}"
}
```

# Generate OAuth expiring (access and refresh) token

The merchant clicks Connect on your app in the Clover App Market.  
The Clover App Market redirects the merchant to the location specified in the Alternate Launch Path field.  
The app calls /oauth/v2/authorize to initiate OAuth.

A merchant uses an app for the first time  
The merchant chooses an app from the appmarket  
The merchant will be redirected to /oauth/v2/authorize  
The merchant is prompted to log in (if not logged in already)  
The merchant is prompted to choose a merchant (if there is more than one under the account)  
The merchant is prompted to approve the app for access to merchant data  
The merchant is redirected to /a/v2/{appID}  
The merchant is redirected to the app callback URL with authorization token as query param  
The developer app makes a call to /oauth/v2/token to obtain an access and refresh token pair  
The developer app uses the access token to authenticate against a public API endpoint successfully

# Related topics

Authenticate with OAuth—Canada and US

Blog: [Fiddling Through Digital Keys: Clover Auth Tokens and Ecommerce Keys](https://medium.com/clover-platform-blog/understanding-clover-auth-tokens-and-ecommerce-keys-4e048827afa2)
