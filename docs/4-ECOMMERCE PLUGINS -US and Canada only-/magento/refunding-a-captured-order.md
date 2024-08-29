---
title: "Refund a captured order"
slug: "refunding-a-captured-order"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides the procedure to refund a captured order for Adobe Commerce."
  image: []
  robots: "index"
createdAt: "Wed May 25 2022 21:18:26 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


To view the refund status of a captured order:

1. Log in to the Adobe Commerce Dashboard.
2. From the left navigation menu, click **Sales **> **Operations** > **Order**. The Order page appears.
3. Click **Order View** > **Invoice**. The Invoices page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/407647e-Invoices2.png",
        "Invoices2.png",
        1849
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


4. For an invoice, click the **View** link in the Action column. The Order & Account Information section appears.
5. From the top menu, click **Credit Memo**. The merchant needs to issue a credit memo if a customer wants to cancel an order after it is invoiced, that is after the payment is captured.

![](https://files.readme.io/6ad62e3-Orders2.png "Orders2.png")

The New Memo for invoice number page appears.  
6. Verify refund information in the Refund Totals section.  
7. Click **Refund**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/83aaac1-NewMemo-Refund.png",
        "NewMemo-Refund.png",
        1074
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


8. In the Order & Information section, verify the Order Status displays as **Closed**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a54597e-ClosedOrder.png",
        "ClosedOrder.png",
        1860
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


To verify the transaction refund on the Clover Merchant Dashboard.

1. Log in to the Clover Merchant Dashboard.
2. From the left-navigation menu, click **Orders**.
3. In the Status column, verify that the order status displays as **Refunded**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0efd265-Refund.png",
        "Refund.png",
        1026
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


> 📘 Note
> 
> If you are unable to refund partially captured orders, contact the Clover Merchant support team to enable this feature.
