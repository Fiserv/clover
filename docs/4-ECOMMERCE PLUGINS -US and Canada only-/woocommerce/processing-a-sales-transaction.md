---
title: "Process a sale transaction"
slug: "processing-a-sales-transaction"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides the procedure to process a sale transaction on the WooCommerce Dashboard."
  image: []
  robots: "index"
createdAt: "Fri Sep 02 2022 07:49:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


To process a sale transaction with authorization and capture flow:

1. Log in to WordPress Dashboard.
2. From the left navigation menu, click **WooCommerce** > **Settings**.
3. Click the **Payments tab**.
4. Click **Payment Method** > **Clover Payments**. The Clover Payments page appears.
5. From the Payment Action drop-down list, select **Authorize and Capture**.
6. Click **Save changes**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1c445e5-Woo-Payments-Sales.png",
        "Woo-Payments-Sales.png",
        716
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


7. On the merchant’s eCommerce website, select the product to purchase.
8. On the Checkout page, select **Pay by card (Clover Payments)** as the Payment method, and enter card details.
9. Click **Place Order**. A success message appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c322bb6-Woo-OrderRecieved1.png",
        "Woo-OrderRecieved1.png",
        704
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]
