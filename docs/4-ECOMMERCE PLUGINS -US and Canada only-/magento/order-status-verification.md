---
title: "Process a sales flow"
slug: "order-status-verification"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides the procedure to process a sales flow for Adobe Commerce."
  image: []
  robots: "index"
createdAt: "Mon Apr 04 2022 23:16:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


# Process a sales (authorization and capture) flow

To process a sales (authorization and capture) flow: 

1. Log in to the Adobe Commerce Dashboard.
2. From the left navigation menu, click **Stores** > **Settings** > **Configuration**. The Configuration page appears.
3. Click **Sales** > **Payment Methods**.
4. Click **Clover Payments Configure.**
5. Enter information in the fields and from the Payment Action drop-down list, select **Authorize and Capture**.
6. Click **Save**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/acd4e4c-Screen_Shot_2022-05-04_at_2.39.51_PM.png",
        "Screen Shot 2022-05-04 at 2.39.51 PM.png",
        1182
      ],
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


# View the status of a refund

To view the refund status of a captured order:

1. Log in to the Adobe Commerce Dashboard.
2. From the left navigation menu, click **Sales** > **Operations** > **Order**. The Order page displays.
3. Click **Order View** > **Invoice**. The Invoices page appears.
4. For an invoice, click the **View** link in the Action column.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1f3391c-Invoices2.png",
        "Invoices2.png",
        1849
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The Order and Account Information appears.  
5. From the top menu, click **Credit Memo**. The merchant needs to issue a credit memo if the customer wants to cancel an order after it is invoiced, that is after the payment is captured.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7c454b7-Orders2.png",
        "Orders2.png",
        1860
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The New Memo for _invoice number_ page appears.  
6. Verify refund information in the Refund Totals section.  
7. Click **Refund**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bb099ab-image1.png",
        "image1.png",
        1877
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


A success message appears.  
8. In the Order & Account Information section, verify that the Order Status displays as **Closed**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e904875-CreditMemo.png",
        "CreditMemo.png",
        1872
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


# Verify order on the Clover Dashboard

To verify that the order and transaction displays on the Clover Merchant Dashboard.

1. Log in to the Clover Merchant Dashboard.
2. From the left-navigation menu, click **Orders**.
3. In the Status column, verify that the order status displays as **Refunded**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7f73f1e-image3.png",
        "image3.png",
        1882
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
