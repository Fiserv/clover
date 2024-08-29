---
title: "Integrate Clover Payments with Shopify Online Shop"
slug: "integrate-clover-payments-with-shopify"
excerpt: ""
hidden: true
metadata: 
  description: "Learn how to integrate the Clover Payments plugin with Shopify Online Shops in the North America—United States (US) and Canada—region to accept payments using Clover."
  image: []
  keywords: "Clover Payments for Shopify plugin, Shopify, Clover Payments"
  robots: "index"
createdAt: "Mon Feb 05 2024 07:53:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jul 17 2024 03:21:18 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--DS-5828- New topic-->\n<meta name=\" description\" content=\"Learn how to integrate the Clover Payments plugin with Shopify Online Shops in the North America—United States (US) and Canada—region to accept payments using Clover.\" > "
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]{"html":"<!--Add a top nav for all related topics-->\n<div><!--div set-->\n <div class=\"top-container\">\n    <div class=\"topnav\">\n      <a href=\"https://docs.clover.com/docs/clover-payments-plugin-for-shopify-stores\">Clover Payments plugin for Shopify Online Shop</a>\n      <a href=\"https://docs.clover.com/docs/integrate-clover-payments-with-shopify\">Integrate Clover Payments with Shopify Online Shop</a>\n      <a href=\"https://docs.clover.com/docs/clover-payments-plugin-shopify-webhooks\">Compliance webhooks</a>\n   \n    </div><!--end topnav-->\n  </div><!--end top-container-->\n</div>\n\n<!--css-->\n<style>\n/* Add a background color to the top navigation */\n.topnav {\n  font-family: 'Graphik-Regular', sans-serif;\n  background-color: #5D5D5D;\n  overflow: hidden;\n}\n\n/* Style the links inside the navigation bar */\n.topnav a {\n  font-family: 'Graphik-Regular', sans-serif;\n  float: left;\n  color: #f2f2f2;\n  text-align: center;\n  padding: 10px 12px;\n  text-decoration: none;\n  font-size: 12px;\n}\n\n/* Change the color of links on hover */\n.topnav a:hover {\n  background-color: #D8D8D8;\n  color: black;\n}\n\n/* Add a color to the active/current link */\n.topnav a.active {\n  background-color: #5D5D5D;\n  color: white;\n}\n</style>"}[/block]

# Before you begin

To integrate the Clover Payments plugin with a Clover merchant's Shopify Online Shop, note the following:

- **Clover merchants**—The free Clover Payments plugin is available for Clover merchants. On the Clover Merchant Dashboard, a merchant can have multiple merchantIds but can associate only one <<glossary:merchantId>> with one or more Shopify Online Shops. A merchant can only create a Shopify Online Shop for a specific country and its currency. The merchant's Clover account agreement determines the charges for transactions. Shopify does not support surcharging; hence, only Clover merchants who do not support surcharging can connect with a Shopify Online Shop.
- **Card networks**—Merchants with Shopify Online Shops must select the same card networks on Shopify to ensure a seamless payment transaction process. In case of any changes, Clover communicates the card network settings and updates to Shopify so they can apply the same settings.
- **Best practices**—Review the [best practices to install or uninstall](https://docs.clover.com/docs/clover-payments-plugin-for-shopify-stores#best-practices-to-install-or-uninstall) the Clover Payments plugin.

# Prerequisites

1. Clover merchant account with the Owner role and a Clover merchantId.  
   **Note: **Surcharge-enabled merchantId cannot be connected to a Shopify Online Shop.
2. Shopify Online Shop for the Clover merchant.

# 1\. Install the Clover Payments plugin

1. Log in to your [Shopify Online Store account](https://accounts.shopify.com/lookup?rid=c5483bbc-2be4-41fb-99ce-6d3189b439f9&verify=1707130110-NDU4MzUzZDg5NDk1MDFjYjg3ZWRjMGI1NDdkNWM4Y2RjNWJlMGMzZmU1N2RkOTcxYzhkOWRiOWQzMmEwNDllYw).
2. Click **Settings** > **Payments**. The Payments page appears. On this page, you can add different payment providers and methods.  
   **Note:** Click test payment provider to use the Bogus Gateway to test a payment provider.
3. In the Payment providers section, click Choose a provider.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/20c0d09-01-ChooseProvider.png",
        "",
        "Shopify Store: Payments > Choose a provider"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Shopify Online Shop: Payments > Choose a provider"
    }
  ]
}
[/block]


The Third-party payment providers page appears.

4. Enter **Clover** in the Filter third-party payment field and click the search icon. Clover Payments displays in the search results.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b64a86c-04-Select-TPP.png",
        "",
        "Shopify Store: Third-party payment providers"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Shopify Online Shop: Third-party payment providers"
    }
  ]
}
[/block]


5. Click **Clover Payments** and then click **Install**. The Install app page appears.
6. Review or add information as needed.
7. Click **Install**. The Clover Payments plugin page appears.
8. Click **Manage Account**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b388cbd-05-Manage-Account.png",
        "",
        "Clover Payments: Manage Account"
      ],
      "align": "center",
      "border": true,
      "caption": "Clover Payments: Manage Account"
    }
  ]
}
[/block]


The Clover Merchant Log In page appears.

9. Log in to your Merchant Dashboard and complete the steps to Connect the Clover Payments plugin with a merchant.

# 2\. Connect the Clover Payments for Shopify plugin with a merchant

On the Clover Merchant Dashboard, select the merchant to integrate the Clover Payments plugin with the Shopify Online Shop.

1. Log in to the Clover Merchant Dashboard. The Select a Merchant page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9facbc4-Select-merchant.png",
        "",
        "Clover Merchant Dashboard: Select a Merchant page"
      ],
      "align": "center",
      "sizing": "70% ",
      "border": true,
      "caption": "Clover Merchant Dashboard: Select a Merchant page"
    }
  ]
}
[/block]


2. From the Merchant column, click a merchant. The Clover App Market displays the Clover Payments plugin in the Merchant Dashboard.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e68e747-05-ConnectPlugin.png",
        "",
        "Merchant Dashboard > More Tools > Clover Payments for Shopify plugin > Connect button"
      ],
      "align": "center",
      "sizing": "112% ",
      "border": true,
      "caption": "Merchant Dashboard > More Tools > Clover Payments for Shopify plugin > Connect button"
    }
  ]
}
[/block]


3. Click **Connect**. The Pricing & Subscription pop-up appears. The Free subscription option is selected by default.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0a85f50-06-Subscribe.png",
        "",
        "Pricing & Subscription Information pop-up"
      ],
      "align": "center",
      "sizing": "60% ",
      "border": true,
      "caption": "Pricing & Subscription Information pop-up"
    }
  ]
}
[/block]


4. Click **Connect**. The Select a Merchant page reappears.  
   Reselect the merchant's name. The Review card brands accepted by \<_store name_> page appears.  
   **Note: **The page displays all the card network brands associated with merchant ID during their onboarding. Merchants with Shopify Online Shops must select the same card networks on Shopify to ensure a seamless payment transaction process.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/eff2cca-image.png",
        null,
        "Clover Merchant Dashboard: Review credit card networks"
      ],
      "align": "center",
      "sizing": "70% ",
      "border": true,
      "caption": "Clover Merchant Dashboard: Review credit card networks"
    }
  ]
}
[/block]


5. Review the information and click **Confirm**. The Shopify Online Shop Dashboard appears.  
   **Note:** To integrate the Clover Payments plugin with another business's Shopify Online Shop, click **Choose your business**. Search for and select another merchant on the Select a Merchant page.

<!--

 

Hide until we publish the webhooks topic

# Related topics

- [Ecommerce (US and Canada only) - Clover Payments plugin](https://docs.clover.com/docs/clover-payments-plugin-for-shopify-stores)
- [Compliance webhooks for Clover payments plugin](https://docs.clover.com/docs/clover-payments-plugin-shopify-webhooks)

\-->
