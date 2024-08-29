---
title: "Set app link (URL) and CORS domain"
slug: "using-cors"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to set app link (URL) and CORS domain for your web apps."
  image: []
  robots: "index"
createdAt: "Mon Jun 25 2018 21:23:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 12 2024 11:36:58 GMT+0000 (Coordinated Universal Time)"
---
<meta name= "description" content= "Learn how to set app link (URL) and CORS domain for your web apps.>

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to\nthe partner docs. -->\n<!--DS-6275: Updated links and moved the topic under OAuth flow.-->"
}
[/block]


The Clover integration for web applications uses the OAuth 2.0 protocol to secure API tokens for merchants. When setting up a web app, you must enter the app link or site URL, which merchants are redirected to after they install and launch an app from the Merchant Dashboard. You can also set a custom post-authorization landing page by including a `redirect_uri parameter` in the OAuth authorization request. Optionally, you can enter an Alternate Launch Path and CORS Domain values in the web app settings. See how to [add web app settings](https://docs.clover.com/docs/app-settings#add-web-app-settings).

All these configurations are set in the sandbox Developer Dashboard for testing and in the production Developer Dashboard to launch an approved app and publish it in the <a href="https://www.clover.com/appmarket" target="_blank">Clover App Market</a>. See [Use Clover developer environments](https://docs.clover.com/docs/clover-environments) for information on the Developer Dashboards.

## Site URL (link)

The Site URL is the link where a merchant is redirected after they install your app and launch it from the Merchant Dashboard. Your authenticated merchants are sent to the Site URL after you redirect them to `/oauth/authorize`. Merchants can authenticate themselves by logging in or selecting their merchant account.

You can override the post-authorization landing page by providing a `redirect_uri` in your request to.`/oauth/authorize`.

> 📘 NOTE
> 
> A `redirect_uri` passed to `/oauth/authorize` must be a subpath of the set **Site URL**.
> 
> For example, if you enter the site URL `https://www.example.com/myapp`, the `redirect_uri` of `https://www.example.com/myapp/setup` in your OAuth request is **valid**, but `https://example.com/setup` is **invalid**.

## Cross-Origin Resource Sharing (CORS) (optional)

Clover implements [Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS), which lets you:

1. Build pure HTML/JavaScript-based client applications without an app server to intermediate between your browser and the Clover server.
2. Make requests from your client-side app to the Clover REST API using the `XmlHttpRequests` or AJAX requests.
3. Connect a semi-integrated app to a Clover Flex, Mini, or Mobile using [Cloud Pay Display](doc:pay-display-apps).

> 🚧 IMPORTANT
> 
> Clover REST API does not support JSON with Padding (JSONP).

On the sandbox Developer Dashboard, enter your application domain, such as `https://www.example.com` or `http://localhost:8000` for testing. You can use the OAuth access tokens from your application domain for cross-domain requests.

**Troubleshoot CORS**

If you experience difficulties in implementing CORS:

- Verify that you have entered the **Site URL** and **CORS Domain** for your app in the sandbox Developer Dashboard.
- Verify that you are using an OAuth token retrieved by following the correct [OAuth flow](https://docs.clover.com/docs/oauth-flows-in-clover). If you want an OAuth token instead of a code, set the `response_type=token` in the OAuth request.
- Make sure that you are not using test API tokens (**Setup > API Tokens**) on the test Merchant Dashboard.

## Alternate Launch Path (optional)

The Alternate Launch Path is an optional setting that lets you configure an alternate link. If you have defined the alternate launch path link, your merchant is redirected to this link in your app after they install and launch the app from the Merchant Dashboard. This URL:

- Uses the expiring authentication tokens to authenticate with APIs.
- Sends the merchant directly to your app and initiates the OAuth flow. See [Initiate OAuth flow from Merchant Dashboard left navigation app link](https://docs.clover.com/docs/merchant-dashboard-left-navigation-oauth-flow).
