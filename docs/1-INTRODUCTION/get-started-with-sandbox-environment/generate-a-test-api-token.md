---
title: "Generate a merchant-specific test API token"
slug: "generate-a-test-api-token"
excerpt: ""
hidden: false
metadata: 
  description: "Clover uses OAuth 2.0 to secure connections between web apps and merchant information, requiring API tokens for access. Learn about generating API tokens for sandbox and production environments."
  image: []
  robots: "index"
createdAt: "Fri May 13 2022 21:46:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 30 2024 08:52:19 GMT+0000 (Coordinated Universal Time)"
---
<meta name= "description" content= "Clover uses OAuth 2.0 to secure connections between web apps and merchant information, requiring API tokens for access. Learn about generating API tokens for sandbox and production environments.">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# API tokens overview

Clover uses the industry-standard OAuth 2.0 protocol for authentication. Generating an API token is a fundamental part of the OAuth flow to enable secure, controlled, and auditable access to APIs.  
Use API tokens to:

- Authenticate requests to [Clover REST APIs](https://docs.clover.com/docs/clover-development-basics-web-app).
- Secure the communication between an app integration and your merchant account.
- Allow an app to access and create merchant data, such as payments, orders, and inventory. 
- Integrate online payments with your e-commerce website. To generate an Ecommerce API token, see [Clover Help](https://www.clover.com/en-US/help/ecomm-api-token).

# API tokens for test and published apps

In the Clover production environment, expiring access and refresh tokens are used to secure merchant data. In the sandbox environment, you can access the test Merchant Dashboard and create a merchant-specific API token to test your app.

> 🚧 IMPORTANT
> 
> Use the test API tokens generated in your test Merchant Dashboard only for testing the API in the sandbox environment. Do not use the test merchant API tokens in the production environment. For the production environment, use access and refresh tokens following the [region-specific OAuth flow](https://docs.clover.com/docs/oauth-flows-in-clover).

A brief overview of tokens and OAuth flow in the sandbox and production environment is as follows:

[block:parameters]
{
  "data": {
    "h-0": "S.no.",
    "h-1": "Tokens based on environment",
    "h-2": "Description",
    "0-0": "1.",
    "0-1": "API tokens to test apps in sandbox",
    "0-2": "To test your app in the sandbox environment, generate **API test tokens** on the test Merchant Dashboard.",
    "1-0": "2.",
    "1-1": "API tokens to test apps in production",
    "1-2": "To test your app in the production environment, use one of the following:  \n  \n- For Web apps: Use the relevant [OAuth flow based on regions](https://docs.clover.com/docs/oauth-flows-in-clover#oauth-flows-based-on-regions)  to generate an **auth_token**.  \n- For Android apps: Use the Android SDK to [generate an API token and query web services](doc:query-web-services).",
    "2-0": "3.",
    "2-1": "API tokens for published apps",
    "2-2": "The OAuth flow typically begins when a merchant selects and installs your app from the Clover App Market. The app then goes through the OAuth process to obtain an **access token**, which is used to make authenticated API calls.  \n  \nTo create the OAuth flow for published apps, replace <https://sandbox.dev.clover.com/> with the correct regional base URL in your requests, such as:  \n  \n- North America: <https://clover.com/>  \n- Europe: <https://eu.clover.com/>  \n- Latin America: <https://la.clover.com/>  \n  <!--Source: https://docs.clover.com/docs/using-oauth-20#oauth-in-sandbox-versus-production-environment -->",
    "3-0": "4.",
    "3-1": "API tokens for ecommerce apps and integrations",
    "3-2": "To simulate different ecommerce integration type settings and scenarios, including the steps to authenticate and authorize:  \n  \n- Create public and private merchant-specific API tokens for configuring Clover payment integrations to take online payments on an ecommerce site.  \n- Generate OAuth token to complete the Ecommerce API authorization flow. See [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth).  \n- Tokenize customer cards and use the Clover Ecommerce API for payment flows. See [Ecommerce API: Accept payment flows](https://docs.clover.com/docs/ecommerce-api-payments-flow)."
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


# Generate a merchant-specific test API token in sandbox

With your test API token, you can make a REST API call and access Clover merchant data. You can create as many merchant-specific test API tokens as required.

## Prerequisites

- [Create a sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account).
- [Create test merchant account](https://docs.clover.com/docs/use-test-merchants-dashboard).

## Steps

1. Log in to the <<glossary:Developer Dashboard>>.
2. From the Developer Account drop-down list, select a merchant name under Businesses. The test Merchant Dashboard appears.
3. From the left navigation menu, click **Account & Setup.** The Account & Setup page appears.
4. In the Business Operations section, click **API Tokens**.

[block:image]{"images":[{"image":["https://files.readme.io/b9c0eb8-AccntSetup-CreateToken.png","Accnt-Setup.png",2650],"align":"center","sizing":"100% ","border":true,"caption":"Test Merchant Dashboard: Account & Setup page"}]}[/block]

The API Tokens page appears.

[block:image]{"images":[{"image":["https://files.readme.io/b133269-CreateNewToken.png","Create-New-Tken.png",3456],"align":"center","sizing":"100% ","border":true,"caption":"Test Merchant Dashboard: API Tokens"}]}[/block]

5. Click **Create New Token**. The Create new token pop-up displays app permissions that map to platform API endpoints. See [API Reference](https://docs.clover.com/reference/api-reference-overview) > Platform API section.

[block:image]{"images":[{"image":["https://files.readme.io/cfdf764-Create-New-Token-Popup.png","Create-New-Token-Popup.png",1296],"align":"center","sizing":"50","border":true,"caption":"Create new token pop-up"}]}[/block]

6. Enter a token name.
7. Select checkboxes to set permissions based on the test merchant information you want to manage. API tokens are scoped to grant specific permissions to make sure that apps only have access to the resources they need. 
8. Click **Create Token**. The new token displays in the Tokens section. Use this token as the Bearer token to make calls to the Clover Platform API endpoints.
9. Expand the Permissions section to view or edit the permissions associated with the API token.

***

# Test apps in sandbox

When making a REST API call, you must include an Authorization header set with a Bearer token, and the test merchant-specific API token as the credential. 

1. [Create an app](https://docs.clover.com/docs/creating-an-app) and note the App ID and App Secret.
2. [Connect your app](https://docs.clover.com/docs/installing-your-app-to-your-test-merchant) with your test merchant to receive the authorization code in the URL of your installed test app.
3. Note the following information to negotiate with the Clover server for an API token that you can use to make REST API calls:

[block:parameters]
{
  "data": {
    "h-0": "ID",
    "h-1": "Description",
    "0-0": "App ID (Client ID)",
    "0-1": "App ID or Client ID that uniquely identifies an app on Clover App Market.",
    "1-0": "App Secret (Client Secret)",
    "1-1": "App Secret or Client Secret is a secret key that Clover assigns to your app.  \n  \n**Note: **Both the App ID and App Secret are automatically assigned when you create an app. You can view the App ID and App Secret on the [_App name_ - App Settings page](https://docs.clover.com/docs/app-settings#access-settings-for-your-app). These values are required for you to make authorized and authenticated requests to Clover merchant data.",
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
