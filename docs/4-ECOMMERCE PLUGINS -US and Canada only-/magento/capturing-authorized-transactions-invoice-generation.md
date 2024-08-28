---
title: "Capture an authorized transaction"
slug: "capturing-authorized-transactions-invoice-generation"
excerpt: ""
hidden: false
metadata: 
  description: "On the Adobe Commerce Dashboard, you can capture successfully authorized transactions with invoice generation."
  image: []
  robots: "index"
createdAt: "Mon Apr 04 2022 23:13:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


To capture successfully authorized transactions with invoice generation:

1. Log in to the Adobe Commerce Dashboard.
2. From the left navigation menu, click **Sales** > **Operations** > **Order**. The Order page appears.
3. Click **Order View** > **Information**. The Order and Account Information section appears.
4. From the top menu, click **Invoice**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/392b131-Information.png",
        "Information.png",
        1854
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The New Invoice page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/628728c-image23.png",
        "image23.png",
        1101
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


5. Verify order details and the order total.
6. Click **Submit Invoice**. A success message displays that the invoice is created.
7. Click **Transactions** > **Payments.** 
8. In the Transaction Type column, verify the status displays as **Capture**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4dcf781-image25.png",
        "image25.png",
        1870
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


9. From the left navigation menu, click **Sales** > **Operations** > **Order**.
10. Click **Order View** > **Invoices**.
11. In the Status column, verify that the invoice status displays as **Paid**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7372539-Invoices.png",
        "Invoices.png",
        1864
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
        "https://files.readme.io/883b631-image27.png",
        "image27.png",
        1882
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]
