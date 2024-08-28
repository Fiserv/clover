---
title: "Clover iframe integrations"
slug: "clover-iframe-integrations"
excerpt: ""
hidden: false
metadata: 
  description: "The Clover-hosted iframe allows you to quickly integrate card-not-present payment acceptance into your app."
  image: []
  robots: "index"
createdAt: "Thu Feb 13 2020 10:34:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:38:13 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover-hosted `iframe` lets you integrate secure payment features on your website. With an `iframe` you can send sensitive card details directly to Clover servers. This minimizes your Payment Card Industry (PCI) compliance burden and makes it simple to begin taking payments on your website.

In this section, we discuss the following topics:

- [Use the Clover-hosted iframe](doc:using-the-clover-hosted-iframe) 
- [Clover iframe features](doc:clover-iframe-features)
- [Customize iframe elements with CSS](doc:customizing-iframe-elements-with-css)
