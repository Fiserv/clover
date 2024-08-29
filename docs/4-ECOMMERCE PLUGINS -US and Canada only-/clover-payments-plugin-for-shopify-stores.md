---
title: "Ecommerce (US and Canada only) - Clover Payments plugin for Shopify Online Shop"
slug: "clover-payments-plugin-for-shopify-stores"
excerpt: ""
hidden: true
metadata: 
  description: "Learn how the Clover Payments plugin allows merchants with Shopify Online Shops in the North America—United States (US) and Canada—region to accept payments using Clover."
  image: []
  keywords: "Clover Payments for Shopify plugin, Shopify, Clover Payments"
  robots: "index"
createdAt: "Mon Feb 05 2024 05:16:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 16 2024 04:53:14 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\" description\" content=\"Learn how the Clover Payments plugin allows merchants with Shopify Online Shops in the North America—United States (US) and Canada—region to accept payments using Clover.\" > \n<!--DS-5828- New topic-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]{"html":"<!--Add a top nav for all related topics-->\n<div><!--div set-->\n <div class=\"top-container\">\n    <div class=\"topnav\">\n      <a href=\"https://docs.clover.com/docs/clover-payments-plugin-for-shopify-stores\">Clover Payments plugin for Shopify Online Shop</a>\n      <a href=\"https://docs.clover.com/docs/integrate-clover-payments-with-shopify\">Integrate Clover Payments with Shopify Online Shop</a>\n      <a href=\"https://docs.clover.com/docs/clover-payments-plugin-shopify-webhooks\">Compliance webhooks</a>\n   \n    </div><!--end topnav-->\n  </div><!--end top-container-->\n</div>\n\n<!--css-->\n<style>\n/* Add a background color to the top navigation */\n.topnav {\n  font-family: 'Graphik-Regular', sans-serif;\n  background-color: #5D5D5D;\n  overflow: hidden;\n}\n\n/* Style the links inside the navigation bar */\n.topnav a {\n  font-family: 'Graphik-Regular', sans-serif;\n  float: left;\n  color: #f2f2f2;\n  text-align: center;\n  padding: 10px 12px;\n  text-decoration: none;\n  font-size: 12px;\n}\n\n/* Change the color of links on hover */\n.topnav a:hover {\n  background-color: #D8D8D8;\n  color: black;\n}\n\n/* Add a color to the active/current link */\n.topnav a.active {\n  background-color: #5D5D5D;\n  color: white;\n}\n</style>"}[/block]

# Introduction

The Clover Payments plugin lets merchants with Shopify Online Shops in the North America—United States (US) and Canada—region to accept payments using Clover.

Existing Clover merchants can:

1. Integrate the Clover Payments plugin with their Shopify Online Shops to seamlessly accept payments.
2. Provide a secure and efficient transaction process through Clover during shopping cart checkout.

The plugin is free for merchants. Transactions are charged according to the merchant's Clover account agreement.

# How it works

The Clover Payments plugin is an app that provides customized payment processing services for merchants. Existing Clover merchants who do not support surcharging can:

1. Install the Clover Payments plugin from the Shopify Online Shop Dashboard.
2. Log in to the Clover Merchant Dashboard.
3. Connect the Clover merchant account with the Clover Payments plugin.
4. Activate the Clover Payment plugin as a payment method on the Shopify Online Shop.

# Supported payment methods

The supported payment methods for the Clover Payments plugin include digital wallets—Apple Pay, Google Pay, and credit and debit cards. In case of any issues setting up digital wallets, contact your Relationship manager or send an email to [developer-relations@devrel.clover.com](mailto:developer-relations@devrel.clover.com).

# PCI DSS compliance

The Clover Payments plugin offers merchants a seamless and secure card payment processing solution. It enhances security by directly handling card details within the Clover secure system. When the Clover Payments plugin collects card information, the card details are tokenized on the Clover server, and the payment is processed using this token. 

Card details for each processed payment are neither saved on Shopify nor the merchant's server. This removes the Payment Card Industry Data Security Standard ([PCI DSS](https://www.pcisecuritystandards.org/)) compliance scope of your merchant's e-commerce site.

# Best practices to install or uninstall

When you plan to connect your merchant business with a [Shopify Online Shop](https://accounts.shopify.com/lookup?rid=c5483bbc-2be4-41fb-99ce-6d3189b439f9&verify=1707130110-NDU4MzUzZDg5NDk1MDFjYjg3ZWRjMGI1NDdkNWM4Y2RjNWJlMGMzZmU1N2RkOTcxYzhkOWRiOWQzMmEwNDllYw), be aware of the following:

### Rules to connect Shopify Online Shop with Clover merchants

1. Multiple Shopify Online Shops can connect to the same merchant identifier (<<glossary:merchantId>>). For example, a boutique with a unique merchantId can have Shopify Online Shops for business in five locations.
2. A Shopify Online Shop cannot connect to multiple Clover (account) merchantIds.
3. If a merchant not connected with a Shopify Online Shop is selected on the Clover Merchant Dashboard, the specific authorization (OAuth) flow is disrupted. In such a case, the merchant needs to uninstall the Clover Payments plugin from the Shopify Online Shop Dashboard and then reinstall it. See Install the Clover Payments plugin.

### Recommendation for uninstalling the Clover Payments plugin

- Merchants can uninstall the Clover Payments plugin from the Clover Merchant Dashboard left navigation menu > **More Tools** >** Clover App Market **page. However, this is not a recommended flow, as this deletes the plugin from all of the Shopify Online Shops connected to the Clover merchantId.
- Merchants should preferably uninstall the Clover Payments plugin for a shop from the Shopify Online Shop Dashboard. This is the recommended flow, as it only disconnects the plugin from the specific shop and does not impact other shops.

### Recommendation for your browser

- For best results, use Google Chrome or Microsoft Edge browsers; you may face some issues when using Apple Safari and Mozilla Firefox.
- For successful end-to-end OAuth workflow, enable pop-ups on your browser. See:
  - [Block or allow pop-ups in Chrome](https://support.google.com/chrome/answer/95472?hl=en&co=GENIE.Platform%3DDesktop)
  - [How to allow pop-ups for a specific URL in Microsoft Edge](https://support.microsoft.com/en-us/microsoft-edge/block-pop-ups-in-microsoft-edge-1d8ba4f8-f385-9a0b-e944-aa47339b6bb5)

# Features

The Clover Payments plugin for Shopify supports the following:

[block:parameters]
{
  "data": {
    "h-0": "Category",
    "h-1": "Description",
    "0-0": "Payment and sales",
    "0-1": "- **Charge (Authorize and Capture)**—Collect customer payment information and charge them for their purchase.  \n- **Capture**—Merchants can charge the amount placed on hold during authorization.  \n- **Split shipment or multiple capture**—Merchants can split any payment into several captures initiated from a single authorization within a specified time frame.  \n- **Refunds, including partial refunds**—Merchants can send a refund for a paid amount.  \n- **Voids**—Merchants can cancel a previously authorized amount.",
    "1-0": "Payment and card data security",
    "1-1": "- PCI DSS compliance  \n- Fraud value-added service (VAS) tools",
    "2-0": "Localized support",
    "2-1": "**Language:**  \n  \n- English (United States)  \n- French  \n  **Currency:**  \n- United States Dollar (USD)  \n- Canadian Dollar (CAD)"
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Features not supported on Shopify

- Convenience fee
- Split shipment
- Surcharge: Surcharge-enabled Clover merchantId cannot be connected to a Shopify Online Shop, as Shopify does not support surcharging.

## Features coming soon!

- EMV® 3-D Secure (3DS) authentication protocol
- Reporting—Payments coming through the Shopify Online Shop have a _Shopify_ tag to reconcile merchant records.

<!--

 

Hide until we publish webhooks topic also

# Related topics

- [Integrate Clover Payments with Shopify Online Shop](https://docs.clover.com/docs/integrate-clover-payments-with-shopify)
- [Compliance webhooks for Clover payments plugin](https://docs.clover.com/docs/clover-payments-plugin-shopify-webhooks)

\-->
