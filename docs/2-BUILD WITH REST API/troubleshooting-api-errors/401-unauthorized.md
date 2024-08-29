---
title: "401 Unauthorized"
slug: "401-unauthorized"
excerpt: ""
hidden: false
metadata: 
  description: "A 401 error indicates the request from your app was rejected because the request header did not include an API token or the token provided does not have the correct permissions."
  image: 
    - "https://files.readme.io/86ea6c5-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Apr 05 2019 21:36:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 10 2024 22:19:39 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

401 Unauthorized indicates the request lacks valid authentication credentials for the target resource. Some examples when this error displays include incorrect link (URL), incorrect login attempts, outdated browser cache and cookies, server configuration errors, and IP restrictions.

Guidelines to troubleshoot 401 errors are:

# 1\. Use the right Clover environment

Clover sandbox and production are separate environments. You can access and use different environments based on specific regions:

- **North America—United States and Canada: **Create a single developer account and access both the sandbox and production environments on the [Global Developer Dashboard](https://www.clover.com/global-developer-home). See [Get started with the global developer platform](https://docs.clover.com/docs/global-developer-platform-get-started).
- **Europe and Latin America: **Create separate developer accounts on the [sandbox environment](https://docs.clover.com/docs/get-started-with-sandbox-environment) and the region-based [production environments](https://docs.clover.com/docs/get-started-with-sandbox-environment).

Make sure you are executing your request in the correct [Clover environment](https://docs.clover.com/docs/clover-environments).

# 2\. Use the correct URL (link) for the environment

[block:parameters]
{
  "data": {
    "h-0": "Environment",
    "h-1": "URL",
    "0-0": "Global developer environment",
    "0-1": "<https://www.clover.com/global-developer-home>",
    "1-0": "Sandbox base",
    "1-1": "<https://sandbox.dev.clover.com/developer-home/>",
    "2-0": "Production base",
    "2-1": "Europe: <https://www.eu.clover.com>  \nLatin America: <https://www.la.clover.com>"
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]


# 3\. Make sure your request has no errors

1. Check for typing errors in requests, as these often cause a 401 error.
2. Make sure that the access [token](https://docs.clover.com/docs/using-api-tokens#) is passed correctly. The merchant ID required for our REST API is a 13-alphanumeric identifier that displays the merchant name in the Merchant column. Example: TC4DGCJW1K4EW. See [Locate the test merchant ID](https://docs.clover.com/docs/merchant-id-and-api-token-for-development#locate-the-test-merchant-id).
3. Check if you are using the v1 app code URL for the `/v2/token` endpoint. Be sure to use the updated v2 auth code URL: `https\://{clover_server}.clover.com/oauth/v2/authorize?client_id={app_id}&redirect_uri=http\://{app_site_URL}`

# 4\. Check your app's permissions

Clover merchant data is protected by a permissions scheme that requires each merchant to approve access. The API does not distinguish between an unauthorized error (401 - expired/invalid token) and a permissions error (403 - token has insufficient permissions) and returns a 401 Unauthorized in either case. 

Check the following:

- Does your application request the [correct permissions](https://docs.clover.com/docs/permissions#) for the API you call?  
  Example: If you try to create a new order but your app does not request the ORDERS_W permission, an error will appear.
- Did you edit the required permissions for your app after merchants installed it?  
  Example: You have modified the permissions after merchants installed your app. In this case, your merchants must uninstall and reinstall the application and generate a new access token using the [OAuth flow](https://docs.clover.com/docs/401-unauthorized#6-use-the-correct-oauth-flow). This is necessary to protect our merchants as they accept permissions and terms of your app when they install it.

## Uninstall an app

1. Log in to the Developer Dashboard.
2. From the header, select _Your Name_ > **Businesses **> _Merchant Name_.
3. From the left navigation menu, click **More Tools**. The Clover App Market page appears.
4. From the top-right menu, click **My Apps**.
5. Find your app in the list; if needed, click **Next** to find it.
6. For the app, in the Actions column, click the ⋮ icon and click **Uninstall app**.

## Reinstall an app

1. Log in to the Developer Dashboard.
2. From the left navigation menu > **Dashboard** > **Your Apps**, select your app.
3. Click **Market Listing**. The App Name - Market Listing page appears.
4. Click **Preview in App Market**. The app page appears.
5. Click **Connect**, and complete the steps in the reinstall workflow.

# 5\. Check your app's default OAuth response

Verify if the app's Default OAuth Response is set to **Code** or **Token**. This setting is available in the Developer Dashboard under REST Configuration in your [web app settings](https://docs.clover.com/docs/app-settings#add-web-app-settings). 

# 6\. Use the correct OAuth flow

When a merchant selects and installs your app from the Merchant Dashboard left navigation menu or the [Clover App Market](https://www.clover.com/appmarket) (in production environments), the OAuth flow begins. Clover uses OAuth to secure the communication between your app and the merchant and then gives your app the necessary access to merchant data.

Use the correct OAuth flow based on the regions in which you create apps.

- If you create apps in the **North America—United States and Canada**, see [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth) to create or migrate to expiring access (authentication) tokens.
- If you create apps in **Europe or Latin America**, see [Use OAuth 2.0—Europe and Latin America](https://docs.clover.com/docs/using-oauth-20) to acquire API tokens. Note the following for the OAuth 2.0 flow based on your app's Default OAuth Response:
  - If set to **Code**, complete all steps of the OAuth 2.0 flow. When your test merchant is authorized through OAuth 2.0, you receive an authorization code. This code is required for you to request an API token for your app permissions. The code in [Step 2: Receive an authorization code](https://docs.clover.com/docs/using-oauth-20#step-2-receive-an-authorization-code) is **not **an access token. If you try to pass this code as an access token, you receive a 401 - Unauthorized error. 
  - If set to **Token,** you receive the access token directly in [Step 2: Receive an authorization code](https://docs.clover.com/docs/using-oauth-20#step-2-receive-an-authorization-code). You can use a token only when testing in the sandbox environment. See [Generate an API token](https://docs.clover.com/docs/generate-a-test-api-token).

# 7\. Authenticate API requests using the Authorization Bearer header

API requests must be authenticated using the Authorization Bearer header. Trying to authenticate the request in any other manner returns a 401 - Unauthorized response. For example, authentication requests using the access_token query parameter result in a 401 - Unauthorized response.

# 8\. Use merchant tokens correctly

Merchant tokens do not support Cross-Origin Resource Sharing (CORS). If you use a merchant token and call directly from a web browser, your request will fail. You must either proxy Clover API requests through your server or use an OAuth token.
