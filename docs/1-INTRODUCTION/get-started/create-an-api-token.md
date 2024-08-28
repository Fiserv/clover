---
title: "Generate a test API token"
slug: "create-an-api-token"
excerpt: ""
hidden: true
metadata: 
  description: "Clover's API requires apps to authenticate with OAuth 2.0. Learn how to generate tokens with this tutorial."
  image: 
    - "https://files.readme.io/23a41a4-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue Aug 21 2018 18:53:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
type: "link"
link_url: "https://docs.clover.com/docs/generate-a-test-api-token"
---
Clover uses OAuth 2.0 to create a secure connection between your Web apps and Clover merchant information.

> 📘 NOTE
> 
> For your Android app, you can simply [generate an API token and query web services](doc:query-web-services) using Clover Android SDK.

The Clover OAuth 2.0 framework requires you to retrieve an API token before you can query merchant information, such as inventory, orders, and payments. Clover’s implementation of [Using OAuth 2.0](doc:configuring-oauth-20) consists of the following parts:

| ID                         | Description                                                                                                                                                                                                                                 |
| :------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Client ID (App ID)         | The Client ID or App ID uniquely identifies an app on Clover App Market.                                                                                                                                                                    |
| Client Secret (App Secret) | The Client Secret or App Secret is a secret key that is assigned to your app by Clover.                                                                                                                                                     |
| Merchant ID (MID)          | The merchant ID uniquely identifies Clover merchants (including test merchants) on the Clover platform. MIDs are 13 characters in length. On the Merchant Dashboard, you can find the MID for your test merchant in the browser window URL. |
| Authorization Code         | When a merchant has signed in to Clover with their merchant account, you receive an authorization code. With this code, you can request for an API token.                                                                                   |
| API Token                  | With the API token, your app can make REST API calls and access merchant data.                                                                                                                                                              |

You can view the **App ID** and **App Secret** on the [App Settings](doc:app-settings) page.

# Generating an API token

To generate a test API token for use in the sandbox environment:

1. On the <a href="https://sandbox.dev.clover.com/developer-home/login" target="_blank">sandbox Developer Dashboard</a>, select a test merchant from the header menu. You are redirected to the test merchant dashboard.
2. Click **Account & Setup > API Tokens** from the side-nav. This is where you generate test API tokens.
3. On the API Tokens page, click **Create New Token**.
4. In the **Create new token** modal, enter a name and set permissions based on the test merchant information you want to query and manage. Note that these are app permissions and they map to platform API endpoints.
5. Select **Create Token**. You can create as many test API tokens as required.  
   With your test API token, you can make a REST API call and access Clover merchant data.

> ❗️ WARNING
> 
> Tokens generated with the **Setup** app should only be used when testing the API in sandbox. Using these merchant tokens in production is forbidden.
