---
title: "Verify order processing and transaction"
slug: "verifying-order-processing-and-transaction"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides the procedure to verify a WooCommerce order and transaction."
  image: []
  robots: "index"
createdAt: "Fri Sep 02 2022 07:57:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


To verify that the order and transaction display on the Orders page:

1. Log in to the WordPress Dashboard.
2. From the left navigation menu, click **WooCommerce** > **Orders**.
3. From the Orders grid, click the link of an order number with the status as **Processing**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/baef9a6-Woo-Processing1.png",
        "Woo-Processing1.png",
        1558
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The Edit Order page appears.  
4. In the Order notes, verify the status—_Order status changed from Pending payment to Processing_.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5ac70ad-Woo-Processing2.png",
        "Woo-Processing2.png",
        1886
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


To verify that the order and transaction displays on the Clover Merchant Dashboard.

1. Log in to the Clover Merchant Dashboard.
2. From the left navigation menu, click **Orders**.
3. In the Status column, confirm that the order status displays as **Paid**.
4. Verify that the transaction displays in the Transactions section.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3ce2442-Woo-Paid.png",
        "Woo-Paid.png",
        1827
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]
