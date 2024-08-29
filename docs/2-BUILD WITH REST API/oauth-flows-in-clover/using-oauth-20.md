---
title: "Use OAuth 2.0—Europe and Latin America"
slug: "using-oauth-20"
excerpt: ""
hidden: false
metadata: 
  description: "OAuth 2.0 is the industry-standard protocol for online authorization. Get helpful information about the OAuth process and add an OAuth flow to your app."
  image: []
  robots: "index"
createdAt: "Wed Mar 23 2022 00:19:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n   <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


> 🚧 IMPORTANT
> 
> Starting in October 2023, Clover is rolling out expiring auth tokens starting in the United States and Canada.
> 
> - If you create apps in Latin America or Europe, use the instructions in this topic to acquire API tokens.
> - If you create apps in the United States and Canada, see [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth#) to create or migrate to expiring auth tokens.

# Watch the tutorial

Get helpful information about the OAuth process and add an OAuth flow to your app. 

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FzScD5jQC6_g%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DzScD5jQC6_g&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FzScD5jQC6_g%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=zScD5jQC6_g&feature=youtu.be",
  "title": "Using Clover OAuth",
  "favicon": "https://www.youtube.com/s/desktop/0ac1422e/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/zScD5jQC6_g/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=zScD5jQC6_g&feature=youtu.be"
}
[/block]


# Why use OAuth?

OAuth is the industry-standard protocol for online authorization. 

While building your Clover app, you may want to access data about Clover merchants, such as their order history or current inventory. With [Clover REST API](doc:making-rest-api-calls), your app can easily access data about merchants and their businesses.

Considering the sensitivity of merchant data, Clover has implemented the OAuth security framework. When a merchant selects and installs your app from the Clover App Market (in production environments), Clover uses OAuth to first secure the communication between your app and the merchant, and then give your app the necessary access to merchant data.

# OAuth in sandbox versus production environment

Our OAuth documentation is created for use with the sandbox environment. To create the OAuth flow for apps on the Clover App Market (in production environments), simply replace `https://sandbox.dev.clover.com/` with the correct regional base URL in your requests:

- Europe: `https://eu.clover.com/`
- Latin America: `https://la.clover.com/`

# Steps in the Clover OAuth flow

There are four keys steps in the Clover OAuth flow:

![](https://files.readme.io/e330b77-oauth_2x.png "oauth_2x.png")

To start, let us define a few concepts used in the OAuth flow:

- **Client ID**: This ID uniquely identifies your app on the Clover App Market. This ID confirms that your app is participating in the OAuth flow. Your client ID is the **App ID** value in your app's **Settings** page on the Developer Dashboard.
- **Client Secret**: This ID is a secret key that is assigned to your app by Clover. Together, the client ID and client secret authenticate the identity of your app with the Clover server. Your client secret is the **App Secret** value on your app's **Settings** page. **Do not share this key publicly**.
- **Merchant**: Clover merchants can be either one of two states: **unauthorized** or **authorized** 

[block:html]
{
  "html": "<div style=\"\n    margin-top: 0px;\n    margin-right: 30px;\n    margin-bottom: 2em;\">\n<table style=\"width:100%;font-size:14px;color: #4c555a;\n    border-top-color: rgb(238, 238, 238);\n    border-top-style: solid;\n    border-top-width: 3px;\n    border-right-color: rgb(238, 238, 238);\n    border-right-style: solid;\n    border-right-width: 3px;\n    border-bottom-color: rgb(238, 238, 238);\n    border-bottom-style: solid;\n    border-bottom-width: 3px;\n    border-left-color: rgb(238, 238, 238);\n    border-left-style: solid;\n    border-left-width: 3px;\n    border-top-left-radius: 5px;\n    border-top-right-radius: 5px;\n    border-bottom-right-radius: 5px;\n    border-bottom-left-radius: 5px;\n    overflow: auto;\">\n  <col width=\"40%\">\n<tr style=\"text-align:left; font-weight:bold; background-color:#f9f9f9; border-bottom-width:2px; border-bottom-style:solid;    border-bottom-color: rgb(238, 238, 238);\">\n  <td style=\"border-right-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\">Merchant</td>\n  <td>URL</td>\n</tr>\n<tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\">An <strong>unauthorized merchant</strong> wants access to your app, but has not logged in to their Clover merchant account. Your app redirects this merchant to log in to their merchant account.</p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">https://sandbox.dev.clover.com/oauth/authorize?client_id={APP_ID}</code></p></td>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\">An <strong>authorized merchant</strong> has logged in to their Clover merchant account. The Clover Server redirects this merchant to your app.</p></td>\n  <td><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">https://www.example.com/oauth_callback?merchant_id={MERCHANT_ID}&client_id={APP_ID}&code={AUTHORIZATION_CODE}</code></p></td>\n  </tr>\n</table>\n</div>"
}
[/block]


- **Authorization Code**: An authorized merchant is redirected to your app along with an authorization code. With this code, the Clover server confirms that your request for merchant data has been authorized by the merchant. 

```text Authorized merchant redirect URL format
https://sandbox.dev.clover.com/oauth/token?client_id={APP_ID}&client_secret={APP_SECRET}&code={AUTHORIZATION_CODE}
```

- **API Token**: Your app uses the authorization code, client ID, and client secret to negotiate with the Clover server for an API token. With the API token, your app can make REST API calls and access merchant data.

```json API token response from server
{
   "access_token":"{API_TOKEN}"
}
```

> 📘 NOTE
> 
> To learn more, see our blog post [Fiddling Through Digital Keys: Clover Auth Tokens and Ecommerce Keys](https://medium.com/clover-platform-blog/understanding-clover-auth-tokens-and-ecommerce-keys-4e048827afa2).

# Get an OAuth token

Complete the following steps in the OAuth flow to get an OAuth token.

## Prerequisites

Before you can obtain an OAuth token, complete the following tasks: 

- <a href="https://docs.clover.com/docs/setup-clover-sandbox-account">Set up a sandbox developer account</a>.
- <a href="https://docs.clover.com/docs/creating-a-sandbox-app">Create an app in the sandbox environment</a>.
- <a href="https://docs.clover.com/docs/installing-your-app-to-your-test-merchant#">Install your app to your test merchant.</a>

## Step 1: Request merchant authorization

When an unauthorized merchant selects and installs your app from the Clover App Market, redirect the merchant to log in to their Clover merchant account using the following URL format:

```text Unauthorized merchant redirect URL format
https://sandbox.dev.clover.com/oauth/authorize?client_id={APP_ID}&redirect_uri={CLIENT_REDIRECT_URL}
```

> 📘 NOTE
> 
> If an unauthorized merchant navigates directly to your app URL without installing the app from the Clover App Market:
> 
> - Redirect the merchant to log in to their Clover merchant account, and then
> - Inform the merchant to install your app from the Clover App Market

Clover provides several parameters to customize the merchant authorization redirect URL.

[block:html]
{
  "html": "<div style=\"\n    margin-top: 0px;\n    margin-right: 30px;\n    margin-bottom: 2em;\">\n<table style=\"width:100%;font-size:14px;color: #4c555a;\n    border-top-color: rgb(238, 238, 238);\n    border-top-style: solid;\n    border-top-width: 3px;\n    border-right-color: rgb(238, 238, 238);\n    border-right-style: solid;\n    border-right-width: 3px;\n    border-bottom-color: rgb(238, 238, 238);\n    border-bottom-style: solid;\n    border-bottom-width: 3px;\n    border-left-color: rgb(238, 238, 238);\n    border-left-style: solid;\n    border-left-width: 3px;\n    border-top-left-radius: 5px;\n    border-top-right-radius: 5px;\n    border-bottom-right-radius: 5px;\n    border-bottom-left-radius: 5px;\n    overflow: auto;\">\n  <col width=\"26%\">\n<tr style=\"text-align:left; font-weight:bold; background-color:#f9f9f9; border-bottom-width:2px; border-bottom-style:solid;    border-bottom-color: rgb(238, 238, 238);\">\n  <td style=\"border-right-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\">Parameter</td>\n  <td>Description</td>\n</tr>\n<tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">client_id</code></p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">This ID uniquely identifies your app on the Clover App Market. The <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">client_id</code> parameter value is the <strong>APP ID</strong> value on the <strong>App Settings</strong> page on the Developer Dashboard.</p></td>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">client_ids</code> (optional)</p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">If you are building an app for multiple Clover App Markets, your app receives a unique app ID for each App Market. For such apps, set the <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">client_ids</code> parameter with a comma-separated list of app IDs.</p></td>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">merchant_ids</code> (optional)</p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">This ID uniquely identifies a merchant account or business. App users can own multiple merchant accounts and businesses. If an app user has multiple merchant accounts, the user is asked to select the desired merchant account as part of the OAuth flow.</p>\n    <p style=\"line-height: 24px;\n    color: #747c84;\">If you know the merchant account that the user will select, you can simply set the <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">merchant_id</code> parameter with the merchant ID of that account. This enables the user to skip the account selection step.</p>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">redirect_uri</code> (optional)</p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">Once the merchant has logged in to their account, you can redirect them to a custom URL with the <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">redirect_uri</code> parameter.</p>\n    <p style=\"line-height: 24px;\n    color: #747c84;\">If you know the merchant account that the user will select, you can simply set the <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">merchant_id</code> parameter with the merchant ID of that account. This enables the user to skip the account selection step.</p>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">response_type</code> (optional)</p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">By default, the Clover server responds to merchant authorization requests by redirecting the merchant to your app along with an authorization code. For your app on the Clover App Market, receiving the authorization code is an important step in the OAuth 2.0 flow.</p>\n    <p style=\"line-height: 24px;\n    color: #747c84;\">You can also build and publish client-based JavaScript and mobile apps on the Clover App Market. For such apps, if you set the value of the <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">response_type</code> parameter as <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">token</code> in the redirect URL, the Clover server directly sends you an API token along with redirecting the merchant to your app.</p>\n    <p style=\"line-height: 24px;\n    color: #747c84;\">With this method, the API token from the Clover server is publicly accessible. We highly recommend that you use this method only for merchant-facing apps.</p>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">state</code> (optional)</p></td>\n  <td><p style=\"line-height: 24px;\n    color: #747c84;\">To ensure that merchants are logging in to a legitimate redirect URL from your app, you can set the state parameter with any string value.</p>\n    <p>In this case, if the Clover server response also includes the same state parameter value, this ensures that (1) a legitimate request has been made by your app, and (2) the Clover server has redirected the merchant to your app in response to the legitimate request.</p></td>\n  </tr>\n</table>\n</div>"
}
[/block]


## Step 2: Receive an authorization code

Once a merchant is authorized, the Clover server redirects merchants to your app using the **Site URL** value (under **App Settings > REST Configuration**) specified in the <a href="https://sandbox.dev.clover.com/dashboard" target="_blank">sandbox Merchant Dashboard</a>.

> 📘 NOTE
> 
> If you have set the `redirect_uri` parameter to a custom location as part of the merchant authorization redirect URL, the server then redirects the merchant to the specified location.

The Clover server redirects the merchant to your app along with a set of parameters in the following URL format, which includes an authorization code:

```text Merchant redirect URL format
https://www.example.com/oauth_callback?merchant_id={MERCHANT_ID}&client_id={APP_ID}&employee_id={EMPLOYEE_ID}&code={AUTHORIZATION_CODE}
```

With the authorization code, the Clover server confirms that your request for merchant data has been authorized by the merchant. You can use this code to further negotiate with the Clover server for an API token.

> 📘 NOTE
> 
> Every time a merchant is redirected to your app, you can confirm whether the merchant has logged in to their Clover merchant account by checking for an authorization code in the redirect URL.

The following table lists the parameters in the merchant redirect URL from the Clover server to your app.

[block:html]
{
  "html": "<div style=\"\n    margin-top: 0px;\n    margin-right: 30px;\n    margin-bottom: 2em;\">\n<table style=\"width:100%;font-size:14px;color: #4c555a;\n    border-top-color: rgb(238, 238, 238);\n    border-top-style: solid;\n    border-top-width: 3px;\n    border-right-color: rgb(238, 238, 238);\n    border-right-style: solid;\n    border-right-width: 3px;\n    border-bottom-color: rgb(238, 238, 238);\n    border-bottom-style: solid;\n    border-bottom-width: 3px;\n    border-left-color: rgb(238, 238, 238);\n    border-left-style: solid;\n    border-left-width: 3px;\n    border-top-left-radius: 5px;\n    border-top-right-radius: 5px;\n    border-bottom-right-radius: 5px;\n    border-bottom-left-radius: 5px;\n    overflow: auto;\">\n  <col width=\"26%\">\n<tr style=\"text-align:left; font-weight:bold; background-color:#f9f9f9; border-bottom-width:2px; border-bottom-style:solid;    border-bottom-color: rgb(238, 238, 238);\">\n  <td style=\"border-right-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\">Parameter</td>\n  <td>Description</td>\n</tr>\n<tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">merchant_id</code></p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">This ID uniquely identifies the Clover merchant account that has been authorized to use your app.</p></td>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">client_id</code></p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">This ID uniquely identifies your app on the Clover App Market. This parameter confirms that your app is participating in the OAuth flow and that the <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">code</code> parameter value is for the specified <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">client_id</code> parameter value.</p></td>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">code</code></p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">With this authorization code, the Clover server confirms that your request for merchant data has been authorized by the merchant. You can use this code to further negotiate with the Clover server for an API token.</p>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">employee_id</code> (optional)</p></td>\n  <td><p style=\"line-height: 24px; color: #747c84;\">This ID uniquely identifies the owner account associated with the merchant business.</p>\n    <p style=\"line-height: 24px; color: #747c84;\">Send a `GET` request to `v3/merchants/{mId}?expand=owner` to identify the merchant business UUID and owner account UUID.</p></td>\n  </tr>\n</table>\n</div>"
}
[/block]


## Step 3: Request an API token

At this stage of the OAuth flow, you exchange your authorization code for an API token. Send an API token request to the Clover server in the following URL format:

```text API token request URL format
https://sandbox.dev.clover.com/oauth/token?client_id={APP_ID}&client_secret={APP_SECRET}&code={AUTHORIZATION_CODE}
```

> 📘 NOTE
> 
> Since the API token request consists of sensitive information about your app, this request does not have [CORS support](https://docs.clover.com/clover-platform/docs/using-cors#section--cors-domain-). To successfully request an API token, send this request from your app server to the Clover server. When the Clover server responds to the request, retrieve the API token from your app server.

You must set all the parameters as listed in the following table.

[block:html]
{
  "html": "<div style=\"\n    margin-top: 0px;\n    margin-right: 30px;\n    margin-bottom: 2em;\">\n<table style=\"width:100%;font-size:14px;color: #4c555a;\n    border-top-color: rgb(238, 238, 238);\n    border-top-style: solid;\n    border-top-width: 3px;\n    border-right-color: rgb(238, 238, 238);\n    border-right-style: solid;\n    border-right-width: 3px;\n    border-bottom-color: rgb(238, 238, 238);\n    border-bottom-style: solid;\n    border-bottom-width: 3px;\n    border-left-color: rgb(238, 238, 238);\n    border-left-style: solid;\n    border-left-width: 3px;\n    border-top-left-radius: 5px;\n    border-top-right-radius: 5px;\n    border-bottom-right-radius: 5px;\n    border-bottom-left-radius: 5px;\n    overflow: auto;\">\n  <col width=\"26%\">\n<tr style=\"text-align:left; font-weight:bold; background-color:#f9f9f9; border-bottom-width:2px; border-bottom-style:solid;    border-bottom-color: rgb(238, 238, 238);\">\n  <td style=\"border-right-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\">Parameter</td>\n  <td>Description</td>\n</tr>\n<tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">client_id</code></p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">This ID uniquely identifies your app on Clover App Market.</p></td>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;border-bottom-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">client_secret</code></p></td>\n  <td style=\"border-bottom-style:hidden;\"><p style=\"line-height: 24px;\n    color: #747c84;\">This ID is a secret key that is assigned to your app by Clover. The client ID and client secret together authenticate the identity of your app with the Clover server when you are requesting for an API token.</p>\n    <p style=\"line-height: 24px;\n    color: #747c84;\">The <code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">client_secret</code> parameter value is the same as the <strong>APP SECRET</strong> value on the <strong>App Settings</strong> page on the Developer Dashboard. Do not share this key publicly.</p>\n  </tr>\n  <tr>\n  <td style=\"border-right-style:hidden;\n    padding-top: 5px;\n    padding-right: 15px;\n    padding-bottom: 5px;\n    padding-left: 15px;\"><p style=\"line-height: 24px;\n    color: #747c84;\"><code style=\"background: rgba(96,105,113,.1);\n    padding: 3px 5px;\n    border-radius: 3px;\n    font-size: .8em;\n    color: #555;\">code</code></p></td>\n  <td><p style=\"line-height: 24px;\n    color: #747c84;\">With this authorization code, the Clover server confirms that your request for merchant data has been authorized by the merchant. You can use this code to further negotiate with the Clover server for an API token.</p></td>\n  </tr>\n</table>\n</div>"
}
[/block]


## Step 4: Receive an API token

In the final step, the Clover Server responds to your API token request with a JSON object in the following format:

```json
{
   "access_token":"{API_TOKEN}"
}
```

> 📘 NOTE
> 
> The API token has a lifespan of one year.

# Use the Response Type Token method

All your apps on the Clover App Market follow the OAuth flow to retrieve an API token from the Clover server. You can also build and publish client-based JavaScript and mobile apps on the Clover App Market. For these client-based apps, Clover provides you with the Response Type Token method to retrieve an API token as soon as the merchant is authorized.

To use the Response Type Token method:

1. On the <a href="https://sandbox.dev.clover.com/developer-home/login" target="_blank">sandbox Developer Dashboard</a>, under **App Settings > REST Configuration** page, set the **DEFAULT OAUTH RESPONSE** value to **Token (Testing Only)**.
2. In the merchant authorization redirect URL (step 1 of the OAuth flow), set the value of the `response_type` parameter as `token`.

The Clover server directly sends you an API token and redirects the authorized merchant to your app using the following URL format:

```text App redirect URL format
http://example.com/javascript_app?&merchant_id={MERCHANT_ID}&client_id={APP_ID}&employee_id={EMPLOYEE_ID}#access_token={API_TOKEN}
```

> 🚧 WARNING
> 
> When you use the **Response Type Token** method, the API token from the Clover server is publicly accessible. We highly recommend that you use this method only for merchant-facing apps.
