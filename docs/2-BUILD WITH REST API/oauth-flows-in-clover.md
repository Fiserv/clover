---
title: "OAuth flows in Clover"
slug: "oauth-flows-in-clover"
excerpt: ""
hidden: false
metadata: 
  description: "When you build your Clover app, you may want to access data about Clover merchants, such as their order history or current inventory. For this, you need to authenticate with OAuth 2.0, the industry-standard protocol for online authorization. Learn more about the OAuth flow in Clover."
  image: []
  robots: "index"
createdAt: "Wed Apr 24 2024 09:26:12 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jun 14 2024 05:24:39 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="When you build your Clover app, you may want to access data about Clover merchants, such as their order history or current inventory. For this, you need to authenticate with OAuth 2.0, the industry-standard protocol for online authorization. Learn more about the OAuth flow in Clover." >

[block:html]
{
  "html": "<!--new topic created as introductory topic that can be linked to all references to OAuth flows-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# Why use OAuth?

OAuth 2.0 is the industry-standard protocol for online authorization. 

While you build your Clover app, you may want to access data about Clover merchants, such as their order history or current inventory. With [Clover REST API](doc:making-rest-api-calls), your app can easily access data about merchants and their businesses.

Considering the sensitivity of merchant data, Clover uses the industry-standard OAuth 2.0 security framework for third-party developers to authenticate their apps with merchant accounts and let them use Clover’s public REST APIs on behalf of the merchant. When a merchant selects and installs your app from the Merchant Dashboard left navigation menu or the [Clover App Market](https://www.clover.com/appmarket) (in production environments), the OAuth flow begins.

# OAuth flows based on regions

Beginning in October 2023, Clover is rolling out expiring auth tokens starting in the United States and Canada.

- If you create apps in **North America**—the United States, and Canada, see [Authenticate with OAuth—Canada and US ](https://docs.clover.com/docs/use-oauth)to create or migrate to expiring access (authentication) tokens.
- If you create apps in **Europe or Latin America**—Argentina, see [Use OAuth 2.0—Europe and Latin America](https://docs.clover.com/docs/using-oauth-20) to acquire API tokens.
