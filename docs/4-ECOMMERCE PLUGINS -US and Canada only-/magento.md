---
title: "Ecommerce (US and Canada only) - Adobe Commerce (Magento 2) Clover Payments plugin"
slug: "magento"
excerpt: ""
hidden: false
metadata: 
  title: "Accept payments in your Adobe Commerce (Magento2) shopping cart page using Clover."
  description: "Want to know how to integrate Clover payment extension into Adobe Commerce's Magento 2? Start here and discover the plugin options available to Clover app developers."
  image: 
    - "https://files.readme.io/9bc0bea-Clover-go-app-icon-mockup.png"
    - "Clover-go-app-icon-mockup.png"
    - 192
    - 192
    - "#c5debd"
  robots: "index"
createdAt: "Fri Mar 25 2022 16:33:12 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


The Clover Payments extension for Adobe Commerce (formerly known as Magento 2) allows merchants, in the US and Canada regions, to securely:

- Collect payment card data on their Adobe Commerce-powered websites, and
- Process payments using their Clover merchant account.  
  The plugin is free for merchants and the transactions are charged according to the merchant’s Clover account agreement.

## How it works

This Clover Payments extension uses an `iframe` to collect card information. An associated JavaScript directly communicates with Clover servers to tokenize the card details. Clover `iframe`-based tokenizer is updated as current with any future API changes, so your app requires less maintenance.

## PCI compliance

Card details for each processed payment are not saved on either Adobe Commerce or the merchant's server. The Clover Payments extension does not contribute to the payment card industry (PCI) compliance scope of your Adobe Commerce shopping cart integration.

## Features

- Authorize only
- Capture
- Charge (Authorize and Capture)
- Refund
- Void
- PCI-compliance through `iframe`
- Multilingual support for Canadian French
- Sorting payment options on check out page

> 📘 Note
> 
> For more information on Adobe Commerce, formerly known as Magento 2, see [Adobe Commerce Developer Guide](https://devdocs.magento.com/).

## Contents

- [Prerequisites](doc:prerequisites) 
- [Install, upgrade and uninstall the Payment Extension](doc:installing-magento) 
- [Update multilingual support location](doc:multilingual-support)
- [Configure the Clover Payment Extension](doc:configuration) 
- [Locate the merchant ID](https://docs.clover.com/docs/locating-merchant-id)
- [Set up an API token](doc:configuration-1) 
- [Process authorized transactions](doc:authorization-flow) 
- [Capture authorized transactions](doc:capturing-authorized-transactions-invoice-generation) 
- [Process a sales flow](doc:order-status-verification) 
- [Refund a captured order](doc:refunding-a-captured-order) 
- [Void an authorization](doc:void-order-request) 
- [View surcharges](doc:surcharge) 
- [Customize iframe](doc:customizing-the-iframe) 
- [Appendix](doc:appendix)
