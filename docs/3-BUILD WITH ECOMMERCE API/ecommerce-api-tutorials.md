---
title: "Ecommerce API tutorials"
slug: "ecommerce-api-tutorials"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides links to basic tutorials for the Clover Ecommerce API."
  image: []
  robots: "index"
createdAt: "Thu Jan 16 2020 19:09:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 06:08:31 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--2024.Apr.9: Added RegionIcon-US-CAN reusable content to replace long form html -cd-->\n<!--2023.Feb.27 (DS-3008): Region pill icon added to topic  -->\n"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Ecommerce API tutorials are written for the sandbox environment. Once your app is complete, switch it to use the production base URLs listed in the [API Reference Overview](ref:api-reference-overview).

An OAuth token is required for authenticating and authorizing your account. For any Ecommerce API flow, you need an OAuth token. Generate an OAuth token for a specified <<glossary:merchantId>> and [Clover app ID](https://docs.clover.com/docs/app-settings#view-app-id-and-app-secret). For information on the authentication flow, see [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth).
