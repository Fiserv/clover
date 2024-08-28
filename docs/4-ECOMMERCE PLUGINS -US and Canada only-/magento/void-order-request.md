---
title: "Void an authorization"
slug: "void-order-request"
excerpt: ""
hidden: false
metadata: 
  description: "You can only make a void request against an authorized transaction not yet captured. This page provides the procedure to void an authorization in Adobe Commerce."
  image: []
  robots: "index"
createdAt: "Mon Apr 04 2022 23:20:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


You can only make a void request against an authorized transaction not yet captured. 

To submit a void request:

1. Log in to the Adobe Commerce Dashboard.
2. From the left navigation menu, click **Sales** > **Operations** > **Order**. The Order page appears.
3. Click **Order View** > **Invoice**. The Invoices page appears.
4. For an invoice, click the **View **link in the Action column.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f9078af-Invoices2.png",
        "Invoices2.png",
        1849
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The Order and Account Information section appears.  
4. From the top menu, click **Void** to place a request.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/27a91b0-Information1.png",
        "Information1.png",
        1879
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


To verify the order on the Clover Merchant Dashboard.

1. Log in to the Clover Merchant Dashboard.
2. From the left-navigation menu, click **Orders**.
3. In the Status column, verify that the order status displays as **Voided/Refunded**.
