---
title: "Process an authorization"
slug: "processing-an-authorization"
excerpt: ""
hidden: false
metadata: 
  title: "Process an authorization on the Wordpress Dashboard"
  description: "This page provides the procedure to authorize a payment on the Wordpress Dashboard."
  image: []
  robots: "index"
createdAt: "Fri Aug 26 2022 11:55:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


To process an authorization flow:

1. Log in to the Wordpress Dashboard.
2. From the left navigation menu, click **WooCommerce** > **Plugin Settings** > **Payments**. The Clover Payments page appears.
3. From the Payment Action drop-down list, select **Authorize**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3d08cff-Woo-Payments.png",
        "Woo-Payments.png",
        720
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


4. Click **Save Changes**.
5. On the merchant’s eCommerce website, select the product to purchase.
6. On the Checkout page, select **Pay by card (Clover Payments)** as the payment method, and enter card details.
7. Click **Place Order**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/53becca-WooPlugin-Display.png",
        "WooPlugin-Display.png",
        1600
      ],
      "sizing": "smart",
      "border": true
    }
  ]
}
[/block]


The following page displays that the transaction is successfully processed.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ef4d055-Woo-OrderRecieved.png",
        "Woo-OrderRecieved.png",
        720
      ],
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]
