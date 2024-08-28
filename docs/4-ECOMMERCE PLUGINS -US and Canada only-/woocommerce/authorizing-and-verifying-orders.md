---
title: "Authorize and verify orders"
slug: "authorizing-and-verifying-orders"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides the procedures to authorize an order on the Wordpress Dashboard, and then verify the order and transaction on the Clover Dashboard."
  image: []
  robots: "index"
createdAt: "Fri Sep 02 2022 07:44:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


To authorize an order on the Orders page:

1. Log in to the WordPress Dashboard.
2. From the left navigation menu, click **WooCommerce** > **Orders**.
3. To authorize an order, select the checkbox for an order with **On hold** status.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0fe7a21-Woo-OnHold.png",
        "Woo-OnHold.png",
        1557
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
3. In the Orders grid, verify the Status column for the placed order displays a status of **Open**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3d01bc7-Woo-OpenOrder.png",
        "Woo-OpenOrder.png",
        1803
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


4. From the left navigation menu, click **Transactions** > **Payments**.
5. In the Created column, verify the status of **Auth** for the order transaction.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e079a69-Woo-Auth.png",
        "Woo-Auth.png",
        1805
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]
