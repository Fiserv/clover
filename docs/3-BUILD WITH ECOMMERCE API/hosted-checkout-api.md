---
title: "Hosted checkout API"
slug: "hosted-checkout-api"
excerpt: ""
hidden: false
metadata: 
  description: "Clover hosted checkout feature lets a merchant's customers pay for simple orders directly on their website."
  image: []
  robots: "index"
createdAt: "Fri Nov 20 2020 16:45:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:35:29 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover-hosted checkout feature lets a merchant's customers pay for simple orders directly on their website. For example, a business may be selling admission to an event, but it does not have a Clover terminal to take card payments at the event site. Customers can pay for their tickets online and leave the staff free to run the event. See [Take payments on your website with Clover](https://www.clover.com/help/take-payments-on-your-website-with-clover) for more information about the feature.

> 🚧 IMPORTANT
> 
> Hosted checkout does not use Clover’s inventory system. If you want to use your inventory, the Clover App Market has ecommerce apps that integrate with your existing data.

Other benefits of hosted checkout:

- Customizable to fit the merchant's brand and existing website
- Includes reCAPTCHA in the checkout flow to combat fraud on card-not-present transactions
- PCI compliant - customer card data is securely processed by Clover, not the merchant  
  See the following pages for more information:
- [Request a checkout](doc:making-a-checkout-request) 
- [Create a hosted checkout session](doc:creating-a-hosted-checkout-session) 
- [Redirect customers](doc:redirecting-customers) 
- [Test your hosted checkout integration (macOS/Linux)](doc:testing-your-hosted-checkout-integration-macoslinux) 
- [Test your hosted checkout integration (Windows)](doc:testing-your-hosted-checkout-integration-windows)
