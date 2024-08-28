---
title: "Ecommerce data model"
slug: "ecommerce-data-model"
excerpt: ""
hidden: false
metadata: 
  description: "Clover designed its ecommerce data model around the concepts central to any business: orders, customers, and charges. Read about the details here."
  image: 
    - "https://files.readme.io/b5e4314-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Mon Jan 06 2020 07:07:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 06:59:44 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover Ecommerce API provides access points for retrieving and working with data in several categories. This topic describes these categories and provides insight into their relationships. Developers using the API should understand the basics of these concepts before investing development time in a Clover app. 

# Data model

There are four basic elements to the data model, each with an associated endpoint: charges, customers, refunds, and orders. These elements and their relationships are described in the following sections. See the [Ecommerce Service API](ref:charges) for information.

## Charges

A charge is the central action taken with the API. When your application needs to process a payment, you will use a `/charges` endpoint to perform the transaction. The payment is charged to a `source`, a credit card or debit card that has been tokenized with the hosted tokenizer. See [Integration types](doc:ecommerce-integration-types) for more information.

The charge is related to other data in the following ways:

- A charge is associated with single customer
- A charge is associated with a single order
- A charge can be partially or fully refunded

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8d0f9d6-charge.png",
        "charge.png",
        2700
      ],
      "align": "center",
      "sizing": "smart"
    }
  ]
}
[/block]


## Customers

Customers will use your application to make payments for products or services provided by a merchant. Customer accounts are uniquely identified by the `id` field, and other relevant customer data includes their `name`, `address`, `email`, and billing and shipping information.

![](https://files.readme.io/ccc868a-customer.png "customer.png")

Cards on file are encrypted tokens stored as `source`s for the customer’s account. These tokens are retrieved using the hosted tokenizer to keep applications out of PCI scope.

A customer is related to other data in the following ways:

- A customer can have zero or more orders
- A customer can have zero or more charges applied to their account

## Refunds

Refunds store information about the partial or full repayment of a `charge`. The money to be refunded is set with the `amount` field. Refunds can also set a reason: `duplicate`, `fraudulent`, or `requested_by_customer`.

A refund is related to other data in the following ways:

- A refund is associated with a single charge
- A refund is associated with a single order
- A customer may have zero or many refunds for an order

![](https://files.readme.io/fe668b3-refund.png "refund.png")

## Orders

Orders store information about the items being purchased, the amount the merchant is charging the customer for those items, and the time the order is created. The customer is likely making the purchase through a website, so the order also contains shipping information. This shipping information may be different from the customer’s billing address or own shipping address. If any of the items are returned, that information is also stored with the order.

An order is related to other data as follows:

- A customer can have zero or more orders
- An order can have a single charge
- An order is made by a single customer

![](https://files.readme.io/f6c3f0b-order.png "order.png")

# Ecommerce API webinar

The Ecommerce API engineering team has recorded a webinar to showcase working with the product.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FSE-tzLNeyT4%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DSE-tzLNeyT4&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FSE-tzLNeyT4%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=SE-tzLNeyT4&feature=youtu.be",
  "title": "Clover Developer Webinar | Clover E-Commerce API",
  "favicon": "https://www.youtube.com/s/desktop/5bf10bf8/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/SE-tzLNeyT4/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=SE-tzLNeyT4&feature=youtu.be"
}
[/block]


In the following sections, you can learn more about using the Clover Ecommerce API:

- [Integration types](doc:ecommerce-integration-types)
- [Ecommerce app permissions](doc:ecommerce-app-permissions)
- [Ecommerce API tutorials](doc:ecommerce-api-tutorials)
- [Migrating from Developer Pay to Ecommerce](doc:migrating-from-developer-pay-to-ecommerce)
