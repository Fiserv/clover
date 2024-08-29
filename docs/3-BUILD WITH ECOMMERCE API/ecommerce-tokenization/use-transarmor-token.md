---
title: "(TA token Pilot) Use TransArmor tokens with Ecommerce"
slug: "use-transarmor-token"
excerpt: ""
hidden: true
metadata: 
  description: "Learn how to use TransArmor tokens in the Clover network for multi-pay and recurring payments."
  image: []
  robots: "index"
createdAt: "Fri Jul 12 2024 10:54:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Aug 14 2024 10:06:31 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=\"Learn how to use TransArmor tokens in the Clover network for multi-pay and recurring payments.\">\n\n<!--DS-6327-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--Add a top nav throughout the pilot doc content (v2.2: grayscale, no overlap)-->\n<div><!--div set-->\n <div class=\"top-container\">\n    <div class=\"topnav\">\n      <a href=\"https://docs.clover.com/docs/use-transarmor-token\">TransArmor token overview</a>\n      <a href=\"https://docs.clover.com/docs/ta-token-pilot-create-a-transarmor-token\">Create a TransArmor token</a>\n      <a href=\"https://docs.clover.com/docs/ta-pilot-use-existing-transarmor-tokens\">Use existing TransArmor tokens</a>\n      <a href=\"https://docs.clover.com/reference/ta-token-pilot-transarmor-token-api-index\">TransArmor token API Index</a>\n    </div><!--end topnav-->\n  </div><!--end top-container-->\n</div>\n\n<!--css-->\n<style>\n/* Add a background color to the top navigation */\n.topnav {\n  font-family: 'Graphik-Regular', sans-serif;\n  background-color: #5D5D5D;\n  overflow: hidden;\n}\n\n/* Style the links inside the navigation bar */\n.topnav a {\n  font-family: 'Graphik-Regular', sans-serif;\n  float: left;\n  color: #f2f2f2;\n  text-align: center;\n  padding: 10px 12px;\n  text-decoration: none;\n  font-size: 12px;\n}\n\n/* Change the color of links on hover */\n.topnav a:hover {\n  background-color: #D8D8D8;\n  color: black;\n}\n\n/* Add a color to the active/current link */\n.topnav a.active {\n  background-color: #5D5D5D;\n  color: white;\n}\n</style>"
}
[/block]


> 🚧 Welcome to the TransArmor tokens pilot!
> 
> TransArmor tokens provide an additional layer of security to protect cardholder data during transactions and reduce the regeneration of payment tokens. In Clover, you can create and use an existing TA token with [create a charge](https://docs.clover.com/reference/createcharge-1) and [pay for an order](https://docs.clover.com/reference/postordersidpay-1) endpoints.
> 
> - **Starting in early Q3 2024** -  Clover will gradually deploy the TA token support to across the merchant base; all merchants will not receive immediate access to the feature. As we do this, you can use our APIs to create new TA tokens and use existing TA tokens.
> - **After the launch is complete** -  You will be **required** to use the create a card token, create a charge and pay for an order endpoints to avail TA token features.

# TransArmor token functionality

TransArmor tokens provide an additional layer of security to protect cardholder data during transactions and reduce the regeneration of payment tokens. Key points of this feature are:

- Enhance security - TA tokens replace sensitive cardholder data with randomly generated tokens, making it nearly impossible to decrypt the data.
- Reduce PCI scope - By removing sensitive data from the merchant’s environment, TA tokens help reduce the scope of PCI compliance requirements.
- Ease of Implementation - TA tokens can be integrated with little to no new hardware requirements, making it easier for merchants to adopt this security measure.

## Use TransArmor tokens in Clover Ecommerce

As a Clover developer, you can:

- Create a new TA token
- Use existing valid TA tokens
- Create a charge
- Pay for an order
