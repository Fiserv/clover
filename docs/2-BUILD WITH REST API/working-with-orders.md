---
title: "Manage orders data"
slug: "working-with-orders"
excerpt: ""
hidden: false
metadata: 
  description: "Orders are central to the Clover merchant data model. Web app builders should understand the structure of the order object and how to interact with this data."
  image: 
    - "https://files.readme.io/5f3f1e4-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Mon Jun 25 2018 21:23:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 30 2024 07:30:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!-- \n***Content shared with OLO Partner docs***\n   This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to the partner docs.\n1/30/2023 [christine]:\n\t.\tAdded *Recipes*\n\t.\t[Acelia] updated the sample code snippets\n \t.\tFormatted recipe boxes in the main CSS to make them more noticable. \n2/1/2023 [christine]:\n\t.\tAdded changes that Aneesha made per DS-2544 to this page as well.\n\t.\tUsing this page to replace the current \"Orders data\" page\n\t.\tCoopting the old slug, *working-with-orders*\n> This page needs to be reviewed by an SME for the content relavancy.\n> This page also needs to be updated for the Gift card token.\n--> \n\n"
}
[/block]


[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Use the [Atomic Orders API](https://docs.clover.com/reference/ordercreateatomicorder) to create a complete order with a single API call, including line items, modifiers, discounts, and service charges. This endpoint can also compute order totals and taxes while building the order without creating an actual order. This endpoint builds an ordering solution for both in-store and online orders.

If you need to create an order with custom or ad-hoc line items, use the `/v3/orders` endpoint.

# Prerequisite

Before using the API to create or summarize the orders, the inventory must be available in the Clover environment. You can use our [inventory API](https://docs.clover.com/reference/inventorycreateitem) to create items, modifiers, and discounts and set up tax rates and rules.

# Atomic order requests

An `atomic_order` request includes the following fields:

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "`orderCart`",
    "0-1": "Order cart that contains items, discounts, modifications, and order-related information.",
    "1-0": "`lineItems`",
    "1-1": "Line items associated with the order.  \nYou can use a `modifier` to indicate the size of the coffee (small or large).",
    "2-0": "`discount`",
    "2-1": "Amount or percentage discount applied to the order subtotal. To retrieve discounts applied to individual items, use the [get all line items for an order](https://docs.clover.com/reference/ordergetorderlineitems) endpoint and enter discounts in the `expand` parameter.",
    "3-0": "`orderType`",
    "3-1": "Classification of the order, such as online, delivery, pick-up, or dine-in. Each order type is specific to the merchant.  \n  \nCreate an order type before you create the order. To create an order type, send a POST request to `/v3/merchants/{mId}/order_type`.",
    "4-0": "`serviceCharge`",
    "4-1": "Optional. A service charge or gratuity tip is applied to the order."
  },
  "cols": 2,
  "rows": 5,
  "align": [
    "left",
    "left"
  ]
}
[/block]


# Before you begin

**Prerequisites**

Before creating an order, you must have the following identifiers:

- `orderTypeId`
- `itemId`
- `modId`, if any
- `discountId`, if any
- `taxId`, if any

**Requirements for modifiers**

Modifiers are optional, but if you use them, note the following requirements:

- If you do not pass a `modId`, other modifier fields are ignored.
- If you pass both `name` and `amount` values, these override default modifiers set in the merchant's inventory.

**Steps**

Multiple endpoints are required to create an order: 

1. `v3/merchants/{mId}/atomic_order/checkouts` endpoint opens a cart to build the order (prerequisite information is captured here).
2. `/v3/merchants/{mId}/atomic_order/orders` endpoint creates the order record.
3. `v1/orders/{orderId}/pay` of the Ecommerce API automatically charge the total order amount and to include a tip.

# Build an order summary

Use the `/atomic_order/checkouts` endpoint to build an order and calculate totals, taxes, discounts, service charges, and display summary information. This endpoint does not create an order but displays the current state of the order to the customer.  This endpoint does not display orders on their dashboards and devices.

To use the `/checkouts` endpoint, build an `orderCart` object including a discount and send it as the body of a `POST` request to the `/v3/merchants/{mId}/atomic_order/checkouts` endpoint.  

### Learn how

Tour a full working example with this recipe.

[block:tutorial-tile]
{
  "backgroundColor": "#0864ba",
  "emoji": "🛒",
  "id": "6340731dbc65d00016b10163",
  "link": "https://docs.clover.com/v3/recipes/order-cart",
  "slug": "order-cart",
  "title": "Order Cart"
}
[/block]


> 👍 TIP
> 
> **[Recipes](https://docs.clover.com/recipes)** provide response details and are a great option if you do not have an OAuth token.

### Example

```curl Build an order
curl --request POST \
     --url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/atomic_order/checkouts' \
     --header 'accept: application/json' \
     --header 'authorization: Bearer {OAuth Token}' \
     --header 'content-type: application/json' \
     --data '
{
     "orderCart": {
          "lineItems": [
               {
                    "item": {
                         "id": "MXHW24RNRHW16"
                    },
                    "discounts": [
                         {
                              "name": "$2 Tuesday",
                              "amount": -200
                         }
                    ],
                    "modifications": [
                         {
                              "modifier": {
                                   "available": "true",
                                   "id": "4KAZY3PXJQ4P0",
                                   "name": "Whip cream"
                              },
                              "amount": 25
                         }
                    ]
               }
          ],
          
     }
}
'
```
```python
import requests

url = "https://sandbox.dev.clover.com/v3/merchants/{mId}/atomic_order/checkouts"

payload = {"orderCart": {
        "lineItems": [
            {
                "item": {"id": "MXHW24RNRHW16"},
                "printed": "false",
                "discounts": [
                    {
                        "name": "$2 Tuesday",
                        "amount": -200
                    }
                ],
                "modifications": [
                    {
                        "modifier": {
                            "available": "true",
                            "id": "4KAZY3PXJQ4P0",
                            "name": "Whip cream"
                        },
                        "amount": 25
                    }
                ],
                "refund": {"transactionInfo": {
                        "isTokenBasedTx": "false",
                        "emergencyFlag": "false"
                    }},
            }
        ],
    }}
headers = {
    "accept": "application/json",
    "content-type": "application/json",
    "authorization": "Bearer {OAuth Token}"
}

response = requests.post(url, json=payload, headers=headers)

print(response.text)
```

# Create an order

- Use the `/atomic_order/orders` endpoint to create an order and calculate the order totals. 
- If you are using the `/atomic_orders/checkouts` endpoint to calculate the order total, taxes, and discounts, pass the same request body to the `/orders` endpoint to create the order. 
- Merchants can view the orders on their dashboards and devices.

To create a new order, build an `orderCart` object and send it as the body of a `POST` request to the  `/v3/merchants/{mId}/atomic_order/orders` endpoint. 

### Learn how

Tour a full working example with this recipe.

[block:tutorial-tile]
{
  "backgroundColor": "#0864ba",
  "emoji": "📑",
  "id": "633b54045562a600596e9c80",
  "link": "https://docs.clover.com/v3/recipes/create-an-order-with-multiples-items",
  "slug": "create-an-order-with-multiples-items",
  "title": "Create an order with multiples items"
}
[/block]


> 👍 TIP
> 
> **[Recipes](https://docs.clover.com/recipes)** provide response details and are a great option if you do not have an OAuth token.

### Example

The following example uses the Clover-provided inventory item "Espresso" with `modifierid` for whipped cream.

```curl Create an order
curl --request POST \
     --url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/atomic_order/orders' \
     --header 'accept: application/json' \
     --header 'authorization: Bearer {OAuth Token}' \
     --header 'content-type: application/json' \
     --data '
{
     "orderCart": {
          "discounts": [
               {
                    "name": "$2 Tuesday",
                    "amount": -200
               }
          ],
          "lineItems": [
               {
                    "item": {
                         "id": "MXHW24RNRHW16"
                    },
                    "printed": "false",
                    "exchanged": "false",
                    "modifications": [
                         {
                              "modifier": {
                                   "available": "true",
                                   "price": "0"
                              },
                              "id": "4KAZY3PXJQ4P0",
                              "name": "Whip Cream",
                              "amount": 25
                         }
                    ],
                    "refund": {
                         "transactionInfo": {
                              "isTokenBasedTx": "false",
                              "emergencyFlag": "false"
                         }
                    }
               }
          ],
          "orderType": {
               "id": "GAM80DMM3DEDG"
          },
     }
}
'
```

> 👍 TIP
> 
> If you make amount adjustments to the order after its creation, you must manually recalculate and update the total by sending a `POST` request to the `/v3/merchants/{mId}/orders/{orderId}` endpoint.

# Pay for order

> 📘 NOTE
> 
> Base URL `https://scl-sandbox.dev.clover.com` is only applicable for testing and not for production. See [Work with test merchants in sandbox](https://docs.clover.com/docs/use-test-merchants-dashboard) for more information.

To take payment and include a tip, send a POST request to the `v1/orders/{orderId}/pay` endpoint using the base URL: `https://scl-sandbox.dev.clover.com`.

When paying for an order, set the `delete_order_on_failure` parameter to **true** as part of the `metadata`. This deletes an order if the payment fails, such as due to fraud.

See the [Ecommerce API endpoint](https://docs.clover.com/reference/postordersidpay) for more information.

> 📘 NOTE
> 
> - If you want to use a credit card, use the [create a Card token](https://docs.clover.com/reference/create-card-token) endpoint.
> - If you want to use an ACH payment, use the [create an ACH token](https://docs.clover.com/reference/create-ach-token) endpoint.

### Learn how

Tour full working examples with these recipes.

[block:tutorial-tile]
{
  "backgroundColor": "#5b9f2d",
  "emoji": "💳",
  "id": "633ca330f2f35e0092755a28",
  "link": "https://docs.clover.com/v3/recipes/pay-for-an-order-w-a-cc",
  "slug": "pay-for-an-order-w-a-cc",
  "title": "Pay for an Order w/ a 'CC'"
}
[/block]


[block:tutorial-tile]
{
  "backgroundColor": "#5b9f2d",
  "emoji": "🔑",
  "id": "633ca07f1ee24f00235a09d5",
  "link": "https://docs.clover.com/v3/recipes/create-a-card-token",
  "slug": "create-a-card-token",
  "title": "Create a Card Token"
}
[/block]


> 👍 TIP
> 
> **[Recipes](https://docs.clover.com/recipes)** provide response details and are a great option if you do not have an OAuth token.

# Handle 400 Bad Request errors

`JSON` response consists of two properties - message and details. If the server detects a specific error, it returns an `UUID` of the failed element.

Consider a scenario where the server detects that an order-related element does not exist, and the `JSON` includes the following message: `item_does_not_exist`.

The following example displays the error response, including the `UUID`.

```json Error response
response: {"message": "item_does_not_exist", "details": "8NR072YTBZ52W"}
```

To fix this error, remove or replace the missing or invalid element in your request. 

For the following message values, the `details` value is unrecognized `UUID`:

- `item_does_not_exist`
- `service_charge_does_not_exist`
- `invalid_modifier`

The following are human-readable error messages:

- `cart_is_empty_or_missing`
- `bad_request`
- `order_uuid_is_null`
- `insufficient_customer_info`
- `invalid_discount_attribute` 

See the API Reference for more information on using Atomic APIs:

- [Create an atomic order](https://docs.clover.com/reference/ordercreateatomicorder)
- [Checkout an atomic order](https://docs.clover.com/reference/ordercheckoutatomicorder)
