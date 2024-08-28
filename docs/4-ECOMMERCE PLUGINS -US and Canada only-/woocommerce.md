---
title: "Ecommerce (US and Canada only) - WordPress Clover Payments plugin"
slug: "woocommerce"
excerpt: ""
hidden: false
createdAt: "Thu May 12 2022 18:31:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


# Introduction

The Clover Payments plugin for WordPress allows merchants, in the US and Canada regions, to use a WordPress-based app, such as WooCommerce, to securely:

- Collect card information from buyers your merchant’s eCommerce site, and 
- Process payments using their Clover merchant account.

The plugin is free for merchants. Transactions are charged according to the merchant’s Clover account agreement.

## How it works

Clover Payments plugin uses an `iframe` to collect card information. An associated JavaScript directly communicates with a Clover server to tokenizes the card details. Clover `iframe`-based tokenizer is updated with any future API changes, so your app requires less maintenance.

## PCI compliance

Card details for each processed payment are not saved on either Wordpress or the merchant's server. The Clover Payments plugin does not contribute to the payment card industry (PCI) compliance scope of your merchant’s eCommerce site.

## Features

- Authorize, only 
- Capture 
- Charge (Authorize and capture)
- Multilingual support for Canadian French
- PCI-compliance through `iframe` (See [Clover iframe features](doc:clover-iframe-features))
- Refund 
- Void 

> 📘 Note
> 
> For more information on WooCommerce by WordPress, see the [WooCommerce Developer Guide](https://woocommerce.com/documentation/).

## Contents

- [Install the Clover Payments for WooCommerce plugin](https://docs.clover.com/docs/installing-upgrading-and-uninstalling-payment-extension)
- [Configure the Clover Payments for WooCommerce plugin](https://docs.clover.com/docs/configuring-the-clover-payment-extension) 
- [Update multi-lingual support](https://docs.clover.com/docs/multilingual-support-1) 
- [Locate the merchant ID](https://docs.clover.com/docs/locating-merchant-id-1)
- [Set up an API token](https://docs.clover.com/docs/setting-up-an-api-token)
- [Process an authorization](https://docs.clover.com/docs/processing-an-authorization)
- [Authorize and verify orders](https://docs.clover.com/docs/authorizing-and-verifying-orders)
- [Capture an authorization](https://docs.clover.com/docs/capturing-an-authorization)
- [Process a sale transaction](https://docs.clover.com/docs/processing-a-sales-transaction)
- [Verify order processing and transaction](https://docs.clover.com/docs/verifying-order-processing-and-transaction)
- [Refund an order](https://docs.clover.com/docs/refunding-an-order)
- [Void an authorized order](https://docs.clover.com/docs/voiding-an-authorized-order)
- [View surcharges](https://docs.clover.com/docs/viewing-surcharges) 
- [Customize iFrame](https://docs.clover.com/docs/customizing-iframe) 
- [Appendix](https://docs.clover.com/docs/appendix-1)
