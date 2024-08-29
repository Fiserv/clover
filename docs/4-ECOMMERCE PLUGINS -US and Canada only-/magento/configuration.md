---
title: "Configure the Clover Payment extension"
slug: "configuration"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to configure the Clover Payment extension for Adobe Commerce."
  image: []
  robots: "index"
createdAt: "Fri Mar 25 2022 23:34:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue May 14 2024 07:02:52 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Learn how to configure the Clover Payment extension for Adobe Commerce.\">"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

To configure the Clover Payments extension for Adobe Commerce.

1. Log in to Adobe Commerce dashboard.
2. Click **Stores**  >  **Settings** > **Configuration**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1bca436-Store_Configuration.png",
        "Store_Configuration.png",
        490
      ],
      "align": "center",
      "sizing": "70",
      "border": true
    }
  ]
}
[/block]


The Configuration page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8243aa4-Config1.png",
        "Config1.png",
        1855
      ],
      "align": "center",
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


3. From the left navigation menu, click **Payment Methods**.
4. From the Environment drop-down list, select the account you want to connect with Adobe Commerce:

- **Sandbox** for your Clover sandbox developer account.
- **Production** for your Clover production developer account.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/99a7e35-Config2.png",
        "Config2.png",
        1852
      ],
      "align": "center",
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The following table describes the Configuration Details fields.

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
    "3-0": "Debug drop-down list",
    "3-1": "Enables the debug mode for log analysis.  \nValues:  \n  \n- Yes  \n- No  \n  **Note: **Log messages are logged in `var/log/payment.log.`",
    "4-0": "Merchant ID",
    "4-1": "Universally unique identifier (UUID) of the merchant, also known as the <<glossary:merchantId>> created on the Clover sandbox or production environment for every merchant business.  \nSee [Locate the merchant identifier (merchantId)](https://docs.clover.com/docs/locating-merchant-id).",
    "5-0": "Public Key",
    "5-1": "Token required for the Clover Payments Extension to connect to your Clover sandbox or production developer account. This token or public key allows you to use the Clover payments extension in the selected environment. See [Set up an API token](https://docs.clover.com/docs/configuration-1)",
    "6-0": "Private Key",
    "6-1": "Token required for the Clover Payments Extension to connect to your Clover sandbox or production developer account. This token or private key allows you to use the Clover payments extension in the selected environment. See [Set up an API token](https://docs.clover.com/docs/configuration-1)",
    "7-0": "Payment action",
    "7-1": "Indicates how each payment transaction is handled based on the selected payment action.  \nValues:  \n  \n- **Authorize**—Ensures that the customer’s card is in good standing and has sufficient funds to cover the purchase. An authorization transaction places a hold on the customer’s funds for the transaction amount for settlement at a later date. You can use the Adobe Commerce built-in process to capture an authorization.  \n- **Authorize and Capture**—Ensures that authorization and capture occur simultaneously. Capture is the process of claiming authorized funds, that is, initiating the transfer of funds from the customer’s account to your merchant bank account.",
    "8-0": "Sort Order",
    "8-1": "Sets the display order of the enabled payment methods on the checkout page."
  },
  "cols": 2,
  "rows": 9,
  "align": [
    "left",
    "left"
  ]
}
[/block]


4. Click **Save Changes**. The active payment method option of Payment by card (Clover) displays on the Checkout page.

> 📘 NOTE
> 
> The Adobe Commerce Clover Payments Extension for the current release (1.0.2) is only available in the US and Canada (both English and French).
