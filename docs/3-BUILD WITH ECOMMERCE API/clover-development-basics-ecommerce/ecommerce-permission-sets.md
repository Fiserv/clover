---
title: "Ecommerce permission sets"
slug: "ecommerce-permission-sets"
excerpt: ""
hidden: false
metadata: 
  description: "Ecommerce apps require a specific set of permissions depending on the functions they provide to merchants. This topic gives a few examples of Ecommerce apps and the permissions needed for each."
  image: 
    - "https://files.readme.io/069487f-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue Aug 11 2020 15:53:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:11:44 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Your app requires a specific set of permissions depending on its functions. This topic provides examples of Ecommerce apps to display differences in the required permissions.

## Example #1: iframe integration with no order or customer management

A simple app can build an online store for a merchant and process payments in this store. The app can not track customer or order data though this is available on the Merchant Dashboard.

Two permissions are required for this app:

- Online payments
- Read payments 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/571d65a-BasicEcommAppPerms.png",
        "BasicEcommAppPerms.png",
        868
      ],
      "align": "center",
      "sizing": "80% ",
      "border": true,
      "caption": "Edit Requested Permissions: Payments"
    }
  ]
}
[/block]


## Example #2: iframe integration with basic order management

A slightly more complex app can build an online store for a merchant and process payments in this store. This app can also display some basic order information to the merchant and provide order modification tools. The merchant is required to log on to the Dashboard to view or make changes to customer data.

Four permissions are required for this app:

- Online payments
- Read payments
- Read orders and write orders 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/152fd50-SemiComplexEcommAppPerms.png",
        "SemiComplexEcommAppPerms.png",
        872
      ],
      "align": "center",
      "sizing": "80% ",
      "border": true,
      "caption": "Edit Requested Permissions: Orders and Payments"
    }
  ]
}
[/block]


## Example #3: API integration with payment, order, and customer management features

A complex app can build a complete online store for customers with business management features for the merchant.

Eight permissions are required for this app:

- Online payments
- Read payments and write payments
- Read orders and write orders
- Read customers and write customers
- Read inventory 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1b5ddf9-ComplexEcommAppPerms.png",
        "ComplexEcommAppPerms.png",
        869
      ],
      "align": "center",
      "sizing": "80% ",
      "border": true,
      "caption": "Edit Requested Permissions: Customers, Inventory, Orders, and Payments"
    }
  ]
}
[/block]
