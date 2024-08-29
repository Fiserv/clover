---
title: "Refund payments"
slug: "ecommerce-refunding-payments"
excerpt: ""
hidden: false
metadata: 
  description: "This tutorial explains the process for processing a payment refund with the Clover Ecommerce API. Steps are included for refunding order items and for refunding payments not associated with an order."
  image: 
    - "https://files.readme.io/c2a4323-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue Jan 21 2020 01:42:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


You can refund payments in different scenarios with the Ecommerce API.

# Refund payments without order items to be returned

To refund a payment without any order items to be returned, send a <code>POST</code> request to the <code>/v1/orders/{orderId}/returns</code> endpoint.

> 📘 NOTE
> 
> To use the <code>/v1/orders/{orderId}/returns</code> endpoint, the order <code>status</code> value must be either <code>paid</code> or <code>fulfilled</code>.

In the following example, set the <code>orderId</code> for the order. Set the `authorization: Bearer` as your OAuth-generated `access_token`.

```curl
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/orders/{orderId}/returns' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'content-type: application/json'
```

In response, the refund <code>status</code> value is <code>returned</code> if the refund was successful.

# Refund payments for returned order items

To refund a payment for order items that have been returned, send a <code>POST</code> request to the <code>/v1/orders/{orderId}/returns</code> endpoint along with a list of the items returned.

In the following example, set `items` array values for each item returned. The `parent` (inventory or order line item ID), `amount`, and `type` values are required. To retrieve line item IDs associated with the order, send a `GET` request to `/v3/merchants/{mId}/orders/{orderId}/line_items`.

Set the `authorization` header as your OAuth-generated `access_token`. See the API reference for more information about other values you can set.

```curl
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/orders/{orderId}/returns' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'content-type: application/json' \
  --data '{"items":[{"parent":"{itemId}","amount":1800,
  "description":"Test item #1","quantity":1,"type":"sku"},
  {"parent":"{itemId}","amount":3000,
  "description":"Test item #2","quantity":1,"type":"sku"}]}'
```

In response, the refund <code>status</code> value is <code>returned</code> if the refund was successful.

# Refund charges

To refund a payment without any associated orders, create a refund by sending a <code>POST</code> request to the <code>/v1/refunds</code> endpoint.

> 📘 NOTE
> 
> `/v1/refunds` can be used only to refund charges created with `/v1/charges`. The `/v1/refunds` endpoint does not support partial refunds for charges that include taxes or tips or charges that have more than one line item.
> 
> You can partially refund payments created with `/v1/orders/{orderId}/pay` with the `/v1/orders/{orderId}/returns` endpoint.

In the following example, set the <code>charge</code> ID value of the payment to be refunded. Set the `authorization' header as your OAuth-generated `access_token\`. 

```curl
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/refunds' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'content-type: application/json' \
  --data '{"charge":"{charge_id}"}'
```

In response, the refund <code>status</code> value states whether the refund was successful (<code>succeeded</code> or <code>failed</code>). If the merchant is set up for credit surcharging, the `additional_charges` object provides details of the surcharge for the original payment.
