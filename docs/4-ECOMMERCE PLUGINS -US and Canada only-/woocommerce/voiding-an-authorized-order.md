---
title: "Void an authorized order"
slug: "voiding-an-authorized-order"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides the procedure to void an authorized WooCommerce order that is not captured. Partial voids are not allowed."
  image: []
  robots: "index"
createdAt: "Fri Sep 02 2022 08:12:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


You can only void an authorized order that is not captured. Partial voids are not allowed.

To completely void an authorized order:

1. Log in to the WordPress Dashboard.
2. From the left navigation menu, click **WooCommerce** > **Orders**.
3. From the Orders grid, click the link of an order number with the status as **On hold**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/204c3a7-Voiding-an-order1.png",
        "Voiding-an-order1.png",
        1472
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The Edit Order page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/35d433d-Voiding-an-order2.png",
        "Voiding-an-order2.png",
        1465
      ],
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


4. Click **Refund**.
5. In the Qty field, enter a value.
6. Select **Refund ${refund amount} via Clover Payments**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/322a326-Voiding-an-order3.png",
        "Voiding-an-order3.png",
        1462
      ],
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


A pop-up displays a confirmation message.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0ede1bd-Woo-RefundPopUp.png",
        "Woo-RefundPopUp.png",
        698
      ],
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


7. Click **OK**.
8. On the Edit Order page, verify that the:

- Bill amount displays as **Refunded**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3057e73-Voiding-an-order4.png",
        "Voiding-an-order4.png",
        1464
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


- Order notes displays the status—_Order status changed from On hold to Refunded._

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2f9013b-Voiding-an-order5.png",
        "Voiding-an-order5.png",
        1868
      ],
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


9. On the Orders page, check the order status displays as **Refunded**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e36d1b4-Woo-Refunded4.png",
        "Woo-Refunded4.png",
        1558
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


To verify that the order and transaction displays on the Clover Merchant Dashboard.

1. Log in to the Clover Merchant Dashboard.
2. From the left-navigation menu, click **Orders**.
3. In the Status column, confirm that the order status displays as **Refunded**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/73c4859-Woo-Refunded5.png",
        "Woo-Refunded5.png",
        720
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


> 📘 NOTE
> 
> If you are unable to void an authorized order, contact the Clover Merchant support team to enable this feature.
