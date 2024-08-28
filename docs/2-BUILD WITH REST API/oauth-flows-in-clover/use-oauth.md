---
title: "Authenticate with OAuth—Canada and US"
slug: "use-oauth"
excerpt: ""
hidden: false
metadata: 
  description: "Learn about expiring auth tokens for Clover apps in the US and Canada."
  image: []
  robots: "index"
createdAt: "Wed May 31 2023 16:04:26 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 09 2024 09:13:23 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Learn about expiring auth tokens for Clover apps in the US and Canada.">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

> 🚧 IMPORTANT
> 
> Beginning in October 2023, Clover is rolling out expiring auth tokens starting in the United States and Canada.
> 
> - If you create apps in the United States and Canada, use the instructions in this topic to create or migrate to expiring access (authentication) tokens.
> - If you create apps in Latin America or Europe, see [Use OAuth 2.0—Europe and Latin America](https://docs.clover.com/docs/using-oauth-20) to acquire API tokens.

Use the following list of contents or the side navigation to view OAuth topics.

- [OAuth at Clover](https://docs.clover.com/docs/oauth-intro#)
- [Auth code flow for high trust apps](https://docs.clover.com/docs/high-trust-app-auth-flow#)
- [Auth code flow for low trust apps](https://docs.clover.com/docs/oauth-flow-for-low-trust-apps-pkce#)
- [Refresh access tokens](https://docs.clover.com/docs/refresh-access-tokens#)
- [Legacy token migration flow](https://docs.clover.com/docs/legacy-token-migration-flow#)
- [Initiate OAuth flow from the Clover App Market app selection](https://docs.clover.com/docs/merchant-dashboard-left-navigation-oauth-flow)

> 📘 NOTE
> 
> The topics in this documet set provide guidance on how Clover implements OAuth principles in its application authentication paradigm. It is not intended to be an OAuth tutorial.
