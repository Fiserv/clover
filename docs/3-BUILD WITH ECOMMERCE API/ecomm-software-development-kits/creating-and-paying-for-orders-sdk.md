---
title: "Create and pay for orders (SDK)"
slug: "creating-and-paying-for-orders-sdk"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides step for creating and paying for an order using a Clover Ecommerce SDK."
  image: []
  robots: "index"
createdAt: "Thu Jan 30 2020 10:31:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 08:57:37 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Most applications need to allow merchants to manage order data that payments are associated with. The Ecommerce SDKs provide resources for performing order-related actions.

# 1. Create an order

To create an order, call the `[create an order](https://docs.clover.com/reference/postorders)` endpoint and pass in the minimum required order information:

- `currency`
- `email`
- `items`

```python Python
from clover import Order

order = Order.create(
    currency='usd',
    email='sample.email@example.com',
    items=[
        {
            'amount': 1358,
            'currency': 'usd',
            'description': 'Lemon cupcake with blackberry frosting',
            'quantity': 2,
            'tax_rates'=[
                {
                    'name': 'Sale',
                    'tax_rate_uuid': '{tax_uuid}'
                }
            ]
        }
    ]
)
```
```javascript Node
require('dotenv').config();
const Clover = require("clover-ecomm-sdk");

let ACCESS_TOKEN = process.env.ACCESS_TOKEN;
let ENVIRONMENT = process.env.ENVIRONMENT;

const cloverInst = new Clover(ACCESS_TOKEN, {
  environment: ENVIRONMENT
});

let order = cloverInst.orders.create({
    currency: 'usd',
    email:'sample.email@example.com',
    items:{
        'amount': 1358,
        'currency': 'usd',
        'description': 'Lemon cupcake with blackberry frosting',
        'quantity': 2,
      	'tax_rates':{'name':'Sale','tax_rate_uuid':'{tax_uuid}'}
    }
});
```

In this example, the item-level tax is set using the `tax_rates` object. You can set the tax value for each item in three ways.

[block:parameters]
{
  "data": {
    "h-0": "Tax object",
    "h-1": "Description",
    "0-0": "Tax as UUID (recommended)",
    "0-1": "To set the tax based on merchant tax information, use `tax_rate_uuid`. This is the recommended approach.  \n  \nTaxes are set under **Setup > Taxes & Fees** on the Merchant Dashboard. You can retrieve this merchant tax information with `/v3/merchants/{mId}/tax_rates`.",
    "1-0": "Tax as percentage",
    "1-1": "To set a tax percentage, set the `rate` as an integer. For example, use `1000000` for a 10% tax.",
    "2-0": "Tax as amount",
    "2-1": "To set a flat fee, use `tax_amount`."
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]


This returns an order object in JSON. The `id` value is the unique identifier of the order needed for other requests.

```json Sample create order response
{
    "id": "6WDD8Y1AQ7WCT",
    "object": "order",
    "amount": 2716,
    "tax_amount": 272,
    "amount_returned": 0,
    "currency": "usd",
    "created": 1580416974000,
    "email": "sample.email@example.com",
    "items": [
        {   
            "type": "sku",
            "quantity": 2,
            "amount": 1358,
            "currency": "usd",
            "description": "Lemon cake with blackberry frosting"
          	"tax_rates": [
                {
                   "name" : "Sale",
      						 "tax_rate_uuid" : "77FAGR71YYD5M"
                }
            ]
        }
    ],
        {   
            "type" : "tax",
            "amount" : 272,
            "description" : "Sales Tax"
        }
    ],
    "status": "created"
}
```

# 2. Pay for an order with a source

To pay for an order using a tokenized card, call the [`pay for the order`](https://docs.clover.com/reference/postordersidpay) endpoint and pass in the order's ID and a payment `source`.

```python Python
import clover

pay = clover.Order.pay(orderId, source='clv_1TSTSpbfbN6Jh5CqCm3bMQne')
```
```javascript Node
require('dotenv').config();
const Clover = require("clover-ecomm-sdk");

let ACCESS_TOKEN = process.env.ACCESS_TOKEN;
let ENVIRONMENT = process.env.ENVIRONMENT;

const cloverInst = new Clover(ACCESS_TOKEN, {
  environment: ENVIRONMENT
});

let pay = cloverInst.orders.pay(
  orderId,
  {source:'clv_1TSTSpbfbN6Jh5CqCm3bMQne'},
  function(err, order) {
    //handle errors and successful payment
  }
)
```

> 📘 NOTE
> 
> In case you are adding a customer while creating an order, you can set the source value to the customer UUID while paying for the created order.

The card is charged for the full order amount, and an order object is returned showing the `status` as `paid`. See the [REST API Reference](doc:rest-api-reference) for complete information about the returned values.

```json Sample pay for order response
{
   "id": "6WDD8Y1AQ7WCT", 
   "object": "order", 
   "amount": 2716,
   "tax_amount": 272,
   "amount_paid": 2716,
   "tax_amount_paid": 272,
   "currency": "usd", 
   "charge": "5E1ZZ9JJMA5Z6",
   "created": 1582301374000,
   "email": "sample.email@example.com",
   "ref_num": "015600501490",
   "auth_code": "OK2183",
   "items": [
       {
           "quantity": 2,
           "amount": 1358,
           "description": "Lemon cake with blackberry frosting"
           "tax_rates": [
               {
                   "name": "Sale",
                   "rate": 1000000
               }
           ]
       }
   ],
   ...
   card details
   ...
   "status": "paid",
   "status_transitions": {
       "paid": 1582301378011
   }
}
```

# 3. Add a tip to your order

You can use the `tip_amount` (in cents) value to add a tip before paying for an order.

```python
import clover

pay = clover.Order.pay(orderId, tip_amount=300,
                       source='clv_1TSTSpbfbN6Jh5CqCm3bMQne')
```
```javascript Node
require('dotenv').config();
const Clover = require("clover-ecomm-sdk");

let ACCESS_TOKEN = process.env.ACCESS_TOKEN;
let ENVIRONMENT = process.env.ENVIRONMENT;

const cloverInst = new Clover(ACCESS_TOKEN, {
  environment: ENVIRONMENT
});

let pay = cloverInst.orders.pay(
  orderId,
  {tip_amount: 300, source:'clv_1TSTSpbfbN6Jh5CqCm3bMQne'},
  function(err, order) {
    //handle errors and successful payment
  }
)
```

## Calculations with tips

Always submit the charge amount and tip separately. In the above Python example, for a subtotal of $27.16 and a tip of $3:

|               | Subtotal      | Tip              |
| :------------ | :------------ | :--------------- |
| **Correct**   | `amount=2716` | `tip_amount=300` |
| **Incorrect** | `amount=3016` | `tip_amount=300` |
