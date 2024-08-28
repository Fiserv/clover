---
title: "Process an authorization transaction"
slug: "authorization-flow"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides the procedures to authorize a payment, verify an order on the Adobe Commerce Dashboard, and then verify an order on the Clover Dashboard."
  image: []
  robots: "index"
createdAt: "Wed Apr 06 2022 00:46:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


# Authorize a payment

1. Log in to the Adobe Commerce Dashboard.
2. From the left-navigation menu, click **Stores **> **Setting** > **Configuration**. The Configuration page appears.
3. Click **Sales** > **Payment Methods**.
4. Click **Clover Payments Configure**.
5. Enter information in the fields and from the Payment Action drop-down list, select **Authorize**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/193b9be-Payment-action.jpg",
        "Payment-action.jpg",
        1304
      ],
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


6. Click **Save **.
7. On the merchant’s eCommerce website, select the product to purchase.
8. Enter the Shipping details, and proceed with checkout.
9. On the Review & Payments page, in the Payment Method section, select the **Pay by card (Clover Payments) **option.
10. Enter card information.
11. Click **Place Order**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d388447-Review-Pay.jpeg",
        "Review-Pay.jpeg",
        1224
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The following page displays when the transaction is successfully processed

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1ea462d-Thank-you.jpg",
        "Thank-you.jpg",
        1046
      ],
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


# Verify an order on the Adobe Commerce Dashboard

1. Log in to the Adobe Commerce dashboard.
2. From the left navigation menu, click **Sales** >  **Operations** > **Orders**. The Orders page appears.
3. Verify the order details.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c6619d7-Orders.png",
        "Orders.png",
        2207
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


4. For an order, click the **View** link in the Actions column for an order. The Transactions page appears.
5. Verify the transaction details, including the transaction type.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1e6bfb5-Transactions.jpeg",
        "Transactions.jpeg",
        1098
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


# Verify order on the Clover Dashboard

To verify that the order and transaction display on the Clover Merchant Dashboard.

1. Log in to the Clover Merchant Dashboard.
2. From the left navigation menu, click **Transactions** > **Payments**.
3. In the Created column, verify the status of ** Auth ** for the order transaction.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f59dc44-Payments.png",
        "Payments.png",
        1869
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]
