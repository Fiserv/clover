---
title: "View surcharges"
slug: "viewing-surcharges"
excerpt: ""
hidden: false
metadata: 
  description: "Surcharge is an additional fee that a merchant can charge buyers for accepting certain credit card transactions in some countries or regions. If the merchant is configured for surcharges at a specific Clover account, a message displays for the customers on the eCommerce site, Checkout iframe page, informing of the surcharge."
  image: []
  robots: "index"
createdAt: "Sat May 14 2022 17:15:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 10 2024 22:21:00 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Surcharge is an additional fee that a merchant can charge buyers for accepting certain credit card transactions in some countries or regions. A merchant can configure surcharges in two ways:

- Use a plugin to calculate the surcharge amount.
- Use their Clover account to surcharge a credit card transaction. 

If the merchant is configured for surcharges on a specific Clover account, the customers can view an image on the e-commerce website, checkout `iframe` page, informing about the surcharge.

In the following image, the Note: in the Payment by card (Clover) section indicates that a surcharge may be applicable on credit card transactions.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d53120-Surcharge.png",
        "Surcharge.png",
        2180
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "E-commerce checkout page: Payment by card (Clover) with a note about the surcharge"
    }
  ]
}
[/block]
