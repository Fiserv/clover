---
title: "Capture an authorization"
slug: "capturing-an-authorization"
excerpt: ""
hidden: false
metadata: 
  description: "On the Wordpress Dashboard, you can capture successfully authorized transactions."
  image: []
  robots: "index"
createdAt: "Fri Sep 02 2022 07:48:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


To capture successfully authorized transactions:

1. Log in to the WordPress Dashboard.
2. From the left navigation menu, click **WooCommerce** > **Orders**.
3. From the Orders grid, click the link of the order number to capture an authorization. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f420a05-Woo-OnHold.png",
        "Woo-OnHold.png",
        1557
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
        "https://files.readme.io/01556e2-Woo-EditOrder-Capture.png",
        "Woo-EditOrder-Capture.png",
        1483
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


4. Verify the order details, and click **Capture Charge**. A success message displays the Capture ID.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3fbab9e-Woo-CapturePopUp.png",
        "Woo-CapturePopUp.png",
        1345
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


5. On the message pop-up, click **OK**. The Edit Order page appears.
6. In the Order notes, verify the status—_Order status changed from On hold to Processing._ 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d5188a5-Woo-OnHoldProcessing.png",
        "Woo-OnHoldProcessing.png",
        1873
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


7. Click **OK** and return to the Orders page.
8. In the Orders grid, verify that the status of the order displays as **Processing**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/61eddfd-Woo-OnHold-Processing.png",
        "Woo-OnHold-Processing.png",
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
2. From the left-navigation menu, click **Orders**.
3. In the Status column, verify that the order status displays as **Paid**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/604e2e6-Woo-Paid.png",
        "Woo-Paid.png",
        1827
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]
