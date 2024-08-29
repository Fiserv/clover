---
title: "Configure the Clover Payments for WooCommerce plugin"
slug: "configuring-the-clover-payment-extension"
excerpt: ""
hidden: false
metadata: 
  description: "Follow the procedure to configure the Clover Payments for WooCommerce plugin on your WordPress Dashboard."
  image: []
  robots: "index"
createdAt: "Fri May 27 2022 18:53:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue May 14 2024 07:00:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Follow the procedure to configure the Clover Payments for WooCommerce plugin on your WordPress Dashboard.\">"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

To configure the Clover Payments for WooCommerce plugin.

1. Log in to your Wordpress Dashboard.
2. From the left navigation menu, click **WooCommerce** > **Plugin Settings** > **Payments**. The Clover Payments page appears.
3. From the Environment drop-down list, select the account you want to connect with WooCommerce:

- **Sandbox** for your Clover sandbox developer account.
- **Production** for your Clover production developer account. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5fcd5ed-Woo-SelectEnv.png",
        "Woo-SelectEnv.png",
        1600
      ],
      "align": "center",
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The following table describes the Clover Payments configuration fields:

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Enabled drop-down list",
    "0-1": "Indicates if the Clover Payments Extension displays as an option for customers at checkout.  \nValues:  \n  \n- Yes  \n- No",
    "1-0": "Title",
    "1-1": "Title of the Clover payment that displays to customers at checkout.  \nExample: Payment by card (Clover)",
    "2-0": "Environment drop-down list",
    "2-1": "Environment where the Clover Payments Extension is active.  \nValues:  \n  \n- Production  \n- Sandbox",
    "3-0": "Merchant ID",
    "3-1": "Universally unique identifier (UUID) of the merchant, also known as the <<glossary:merchantId>> created on the Clover sandbox or production environment, for every merchant business.  \nSee [Locate the merchant identifier (merchantId)](https://docs.clover.com/docs/locating-merchant-id-1).",
    "4-0": "Public Key",
    "4-1": "Token required for the Clover Payments Extension to connect to your Clover sandbox or production developer account. This token or public key allows you to use the Clover payments extension in the selected environment.  \nSee [Set up an API token](https://docs.clover.com/docs/setting-up-an-api-token).",
    "5-0": "Private Key",
    "5-1": "Token required for the Clover Payments Extension to connect to your Clover sandbox or production developer account. This token or private key allows you to use the Clover payments extension in the selected environment.  \nSee [Set up an API token](https://docs.clover.com/docs/setting-up-an-api-token).",
    "6-0": "Payment action drop-down list",
    "6-1": "Indicates how each payment transaction is handled based on the selected payment action.  \nValues:  \n  \n- **Authorize**—Ensures that the customer’s card is in good standing and has sufficient funds to cover the purchase. An authorization transaction places a hold on the customer’s funds for the transaction amount for settlement at a later date. You can use the WooCommerce built-in process to capture an authorization.  \n- **Authorize and Capture**—Ensures that authorization and capture occur simultaneously. Capture is the process of claiming authorized funds, that is, initiating the transfer of funds from the customer’s account to your merchant bank account.",
    "7-0": "Debug drop-down list",
    "7-1": "Enables the debug mode for log analysis.  \nValues:  \n  \n- Yes  \n- No  \n  **Note:** Log messages are logged in `wp-content/uploads/wc-logs/`  \n  Filename display example: `clover_payments-2022-04-27-c9b05b315173749bc3cb266ad98dd4e0.log`"
  },
  "cols": 2,
  "rows": 8,
  "align": [
    "left",
    "left"
  ]
}
[/block]


4. Click **Save Changes**. The active payment method option of Payment by card (Clover) displays on the Checkout page.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b818c4f-WooPlugin-Display.png",
        "WooPlugin-Display.png",
        1600
      ],
      "align": "center",
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]
