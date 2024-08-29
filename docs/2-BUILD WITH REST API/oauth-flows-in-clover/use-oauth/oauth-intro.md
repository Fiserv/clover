---
title: "OAuth at Clover"
slug: "oauth-intro"
excerpt: ""
hidden: false
metadata: 
  title: "Intro to OAuth at Clover"
  description: "Learn how Clover implements OAuth 2.0"
  image: []
  robots: "index"
createdAt: "Wed Jun 14 2023 16:06:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jul 04 2024 04:27:05 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--2024-Apr-23 Added correct blogpost link: https://medium.com/clover-platform-blog/expiring-oauth-tokens-securing-clover-merchant-data-16243b9c00cc#\n<!--2024-Feb-19 Add new Video Table to present the video in this topic (DS-5934/DS-5933) CD-->\n<!--2024.Feb.14 Move OAuth Request Paths to the Top of the Page (DS-5908) CD-->\n<!--2023.Dec.03 Add video link and \"Let's learn\" lists (DS-5130/5081) LH-->\n<!--2023.Mar.22 Region pill icon added to topic (DS-3009) AS-->"
}
[/block]


This topic explains how Clover implements OAuth principles in its application authentication paradigm. 

# Why use OAuth?

OAuth 2.0 is the industry-standard protocol for online authorization. 

While you build your Clover app, you may want to access data about Clover merchants, such as their order history or current inventory. With [Clover REST API](doc:making-rest-api-calls), your app can easily access data about merchants and their businesses.

Considering the sensitivity of merchant data, Clover uses the industry-standard OAuth 2.0 security framework for third-party developers to authenticate their apps with merchant accounts and let them use Clover’s public REST APIs on behalf of the merchant. When a merchant selects and installs your app from the Merchant Dashboard left navigation menu or the [Clover App Market](https://www.clover.com/appmarket) (in production environments), the OAuth flow begins.

# Prerequisites to get an OAuth token

Before you can obtain an OAuth token, complete the following tasks:

- [Create a sandbox developer account](https://docs.clover.com/docs/setup-clover-sandbox-account).
- [Create an app](https://docs.clover.com/docs/creating-a-sandbox-app)—Note the app ID (client ID) and app secret (client secret) for use later.
- [Create your test merchant](https://docs.clover.com/docs/working-with-test-merchants).

# Sandbox and production environment URLs

Clover sandbox and production environments use different URLs. The following table lists which URL to use for OAuth requests in each environment. 

| Request path            | Sandbox URL               | Production URL                          |
| :---------------------- | :------------------------ | :-------------------------------------- |
| /oauth/v2/authorize     | sandbox.dev.clover.com    | [www.clover.com](http://www.clover.com) |
| /oauth/v2/token         | apisandbox.dev.clover.com | api.clover.com                          |
| /oauth/v2/refresh       | apisandbox.dev.clover.com | api.clover.com                          |
| /oauth/token/migrate_v2 | apisandbox.dev.clover.com | api.clover.com                          |

> 📘 NOTE
> 
> The Clover v2 OAuth flow, is only available in North America.

# Low trust and high trust apps

Clover distinguishes between apps that more securely store and use their client secrets, and apps that do not.

- **Low trust apps**—Have no secure way to store and use a client secret (app secret)— such as mobile, single-page, and native desktop applications. Previously, low trust apps used the response type token (implicit) auth code flow. Clover now requires that low trust apps use the auth code flow with PKCE. If your Clover app uses the implicit flow and is considered to be a low trust app, [migrate your app to use the auth code flow with PKCE](https://docs.clover.com/docs/legacy-token-migration-flow#).
- **High trust apps**—Securely store and use a client secret (app secret). High trust apps can use the standard auth code flow to generate auth tokens.  
  See [Auth code flow for high trust apps](https://docs.clover.com/docs/high-trust-app-auth-flow#) for more information.

# Watch video: Clover OAuth expiring tokens

[block:html]
{
  "html": "<div class=\"vt\">\n   <table class=\"vt\">\n     <colgroup>\n      <col id=\"first\">\n      <col id=\"second\">\n      </colgroup>\n          <thead>\n            <tr class=\"table-head\">\n              <th class=\"table-head\">Watch</th>\n              <th class=\"table-head\">Learn</th>\n            </tr>\n          </thead>\n          <tbody>\n <!--1st body Row-->\n            <tr class=\"table-content\">\n <!--1st cell-->\n              <td class=\"table-content\">\n                <p class=\"table-content\" style=\"text-align:center;\"></p>\n      <div style=\"clear: both;padding: 2px;text-align:center;\">\n        <iframe id=\"myiframe100p\" \n        src=\"https://www.youtube.com/embed/UgVWhqdfY2c\" \n        title=\"Clover OAuth 2.0: Expiring Tokens\" \n        frameborder=\"0\" \n        allow=\"accelerometer; autoplay; clipboard-write; encrypted-media; \n               gyroscope; picture-in-picture; web-share\" \n        allowfullscreen>\n      </iframe>\n       </div>\n         </td>\n <!--2nd cell-->\n          <td class=\"table-content\">\n<p class=\"table-content\">In this video, learn:</p>\n    <ul class=\"table-content\">\n      <li>What expiring tokens are.</li>\n      <li>How to generate access and refresh tokens.</li>\n      <li>How to migrate an existing app to use expiring tokens.</li>\n      <li>How to start the OAuth flow from the Merchant Dashboard left navigation app link.</li>\n    </ul>\n <p class=\"table-content\">View or download:\n<a href=\"https://clover.box.com/s/27w4v0aq4j47qg8k8tg1cfba4ivuauri\" target=\"_blank\">\n  Clover expiring tokens slides</a></p>\n         </td>\n          </tr>\n <!--end 1st body Row-->\n</table> </div>\n\n<!--=========================================================-->\n<!--related styles are in Reusable HTML content block - Video-Embed-Table-Code - at the bottom of the page-->\n\n"
}
[/block]


# OAuth terminology

A few definitions help to understand the OAuth flow:

- **Access token** (`access_token`)—Used to access Clover APIs. Access tokens expire after a period of time.

> 🚧 IMPORTANT
> 
> The following values for access and refresh tokens are dynamic and can change:
> 
> - Token expiration displays in the response body. Tokens created later can have different durations until they expire. 
> - Token lengths are not fixed.
> 
> Do not hard code access and refresh token expirations or lengths so that you can handle any future updates.

- **Alternate Launch Path**—Sends the merchant directly to your app at the path specified in the field and initiates the v2 OAuth flow. See [Initiate OAuth flow from Merchant Dashboard left nav app link](https://docs.clover.com/docs/merchant-dashboard-left-navigation-oauth-flow) for more information.

- **Authorization code** (`code`)—An authorized merchant is redirected to your app along with an authorization code. With this code, the Clover server confirms that your request to access merchant data is authorized by the merchant.

- **Client ID** (`client_id`)—Uniquely identifies your app on the Clover App Market. This ID confirms that your app is participating in the OAuth flow. Your client ID is the App ID value in your app's Settings page on the <<glossary:Developer Dashboard>>.

- **Client secret** (`client_secret`)—Secret key that is assigned to your app by Clover. Together, the client ID and client secret authenticate the identity of your app with the Clover server. Your client secret is the app secret value on your app's Settings page.
  > 🚧 IMPORTANT
  > 
  > Do not share the client secret key publicly.

- **Merchant ID** (`merchant_id`)—Uniquely identifies a merchant account or business. App users can own multiple merchant accounts and businesses. If an app user has multiple merchant accounts, the user can select the desired merchant account as part of the OAuth flow.  
  You can allow the user to skip the account selection step if you set the `merchant_id` parameter with the merchant ID of that account.

  A merchant who wants access to your app, but has not logged in to their Clover merchant account is an unauthorized merchant. Your app redirects the merchant to log in to their merchant account with the URL <https://sandbox.dev.clover.com/oauth/authorize?client_id={APP_ID}>.

  When a merchant logs in to their Clover merchant account, they become an authorized merchant. The Clover server redirects this merchant to your app with the URL <https://www.example.com/oauth_callback?merchant_id={MERCHANT_ID}&client_id={APP_ID}&code={AUTHORIZATION_CODE}>.

- **Proof key for code exchange (PKCE)**—Created to better secure mobile apps, but it is valuable across all OAuth clients. PKCE removes the need to pass the client secret by using the following parameters:
  - **Code verifier** (`code_verifier`)—Unique random string that the application creates for every authorization request.
  - **Code challenge** (`code_challenge`)—Application hashes the code verifier resulting in the code challenge. Clover currently supports SHA256 (secure hash algorithm 256 bit) to one-way hash the code verifier. Other algorithms may be added in the future.

- **Redirect URI** (`redirect_uri`)—After the merchant has logged in to their account, you can redirect them to a custom URL with the `redirect_uri` parameter. If you know the merchant account that the user will select, you can simply set the merchant_id parameter with the merchant ID of that account. This enables the user to skip the account selection step.

- **Refresh token** (`refresh_token`)—A token that is used to generate more access tokens. It is a one-time-use token used to generate another access token when it expires. Refresh tokens expire, but they are valid for a longer period of time than the access token.  
  Refresh tokens tend to accumulate in the database and can cause performance issues or other technical maintenance issues. Clover sets a limit on the number of refresh tokens a single application can have active for each merchant.

> 🚧 IMPORTANT
> 
> The following values for access and refresh tokens are dynamic and can change:
> 
> - Token expiration displays in the response body. Tokens created later can have different durations until they expire. 
> - Token lengths are not fixed.
> 
> Do not hard code access and refresh token expirations or lengths so that you can handle any future updates.

- **State** (`state`)—To ensure that merchants are logging in to a legitimate redirect URL from your app, you can set the state parameter with any string value.  
  Suppose the Clover server response also includes the same state parameter value. In that case, this ensures that your app makes a legitimate request and the Clover server has redirected the merchant to your app in response to the legitimate request.

> 📘 NOTE
> 
> To learn more about auth tokens, see our blog post [Expiring OAuth Tokens: Securing Clover Merchant Data](https://medium.com/clover-platform-blog/expiring-oauth-tokens-securing-clover-merchant-data-16243b9c00cc).

# Auth code flows

Clover apps use the following auth token acquisition flows:

- **Implicit flow**—Also called **response type token**, this is the least secure auth flow. Implicit flow is a simplified auth flow that can not securely store a client secret. The access token is returned immediately without an extra authorization code exchange step. Implicit flow was previously recommended for native and JavaScript apps that can not securely store a client secret.
  > 🚧 IMPORTANT
  > 
  > Clover plans to deprecate the response type token (implicit) flow. If your app uses response type tokens, migrate your app to use the auth code flow with PKCE. See [Legacy token migration flow](https://docs.clover.com/docs/legacy-token-migration-flow#) for more information.

- **[Authorization code flow](https://docs.clover.com/docs/high-trust-app-auth-flow#)**—Used by [high trust clients](https://docs.clover.com/docs/high-trust-app-auth-flow#) to exchange an authorization code for an access token. After the redirect URL returns the merchant to the application, the app receives the authorization code from the URL and uses it to request an access token.

- **[Authorization code flow with proof key for code exchange (PKCE)](https://docs.clover.com/docs/oauth-flow-for-low-trust-apps-pkce#)**—Required for all applications that can not securely store a client secret, but especially for standalone mobile, desktop, and single-page applications.

## Compare: Legacy response type token (implicit) flow with PKCE flow

Comparing the implicit flow and auth code flow with PKCE illustrates the added security steps in the auth code flow with PKCE.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/349142b-Legacy_Implicit_Flow_vs_New_Auth_Code_Flow_with_PKCE.png",
        null,
        "Implicit flow compared to auth code flow with PKCE"
      ],
      "align": "center",
      "caption": "Implicit flow compared to auth code flow with PKCE"
    }
  ]
}
[/block]


# Additional References

To learn more about the OAuth protocol, visit [OAuth.net](https://oauth.net).

To learn more about Clover auth tokens, see our blog post [Fiddling Through Digital Keys: Clover Auth Tokens and Ecommerce Keys](https://medium.com/clover-platform-blog/understanding-clover-auth-tokens-and-ecommerce-keys-4e048827afa2)

[block:html]{"html":"<style>\n*,\n*::before,\n*::after {\n  box-sizing: border-box; \n  }\n\n/*== Video Table (vt) sample styles ==*/\n  \n /*video table (vt) size based on percentage of container*/\n  div.vt {width:100%; overflow:auto;}\n  table.vt, td.vt {border:1px solid #000;}\n  #first {width:30%;}\n  #second {width:60%;}\n\n  tr.table-head th.table-head /*background-color table header row*/\n{\n\tbackground-color: #280;\n  margin-block-start: 1em;\n  color: #fff;\n  margin-top: 0px;\n\tfont-size: 1.4em;\n\tfont-weight: 500;\n  overflow-wrap: normal;\n  word-break: normal;\n  }\n\n  td.table-head\n{\n  margin-block-start: 1em;\n  color: #fff;\n\tpadding: 10px;\n\tmargin-top: 0px;\n\tfont-size: 1.4em;\n\tfont-weight: 500;\n  overflow-wrap: normal;\n  word-break: normal;\n}\n  tr.table-content {\n  vertical-align: top;\n  }\n  td.table-content\n{\n  vertical-align: top !important;\n  margin-block-start: 1em;\n}\np.table-title\n{\n\tcolor: #fff;\n\tpadding: 10px;\n\tmargin-top: 0px;\n\tfont-size: 1.4em;\n\tfont-weight: 500;\n  overflow-wrap: normal;\n  word-break: normal;\n}\n  \np.table-content\n{\n\tpadding-left: 4%;\n\tpadding-right: 4%;\n  overflow-wrap: normal;\n  vertical-align: top;\n  margin-block-start: 1em;\n}\nul.table-content\n{\n  margin-block-start: 1em;\n}\n/*== iframe sample sizes ==*/  \n  \n  /*iframe size based on percentage of container*/\n  #myiframe100p {\n      width: 100%;\n      height: 100%;\n   }\n    #myiframe90p {\n      width: 90%;\n      height: 100%;\n      m\n   }\n  #myiframe75p {\n      width: 75%;\n      height: 75%;\n   }\n  #myiframe60p {\n      width: 60%;\n      height: 60%;\n   }\n  #myiframe50p {\n      width: 50%;\n      height: 50%;\n   }\n \n</style>"}[/block]
