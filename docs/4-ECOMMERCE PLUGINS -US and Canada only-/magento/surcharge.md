---
title: "View surcharges"
slug: "surcharge"
excerpt: ""
hidden: false
metadata: 
  description: "Surcharge is an additional fee that a merchant can charge buyers for accepting certain credit card transactions in some countries or regions. If the merchant is configured for surcharges at a specific Clover account, a message displays for the customers on the eCommerce site, Checkout iframe page, informing of the surcharge."
  image: []
  robots: "index"
createdAt: "Mon Apr 04 2022 23:23:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 10 2024 22:20:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Surcharge is an additional fee that a merchant can charge buyers for accepting certain credit card transactions in some countries or regions. A merchant can configure surcharges in two ways:

- Use a plugin to calculate the surcharge amount.
- Use their Clover account to surcharge a credit card transaction. 

If the merchant is configured for surcharges on a specific Clover account, the customers can view an image on the e-commerce website, checkout `iframe` page, informing about the surcharge.

In the following image, the Note: in the Payment with card (Clover) section indicates that a surcharge may be applicable on credit card transactions.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/687bd54-Surcharges.png",
        "Surcharges.png",
        1154
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "E-commerce checkout page: Payment by card (Clover) with a note about the surcharge"
    }
  ]
}
[/block]
