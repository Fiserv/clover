---
title: "Create custom orders - DS-5840"
slug: "create-custom-orders-copy"
excerpt: ""
hidden: true
createdAt: "Fri Aug 09 2024 12:04:29 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Aug 09 2024 12:05:31 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Use the `v3/orders/` endpoints to create orders with:  

- Custom or adhoc line items based on non-Clover inventory.
- Line items that reference Clover inventory but allow you to override properties like tax rates or item price.

When you create or update an order, the Clover server synchronizes the order data with the merchant's Clover devices. Use the [Atomic orders](doc:working-with-orders) endpoint to create orders using Clover inventory and leverage the real-time totals and tax calculation features using a single API call.

**Create an `order` object**—Clover merchants create orders before completing transactions with the Register or Sale app. You can also create orders using the  [Clover REST API](doc:making-rest-api-calls).

**Update an `order` object**—An order is updated after merchant actions, such as adding `line_items` for inventory `items` or adding custom `amount` values.

> 👍 TIP
> 
> Money **amount** values are represented in cents. For example, $20.99 is represented as an `amount` value of `2099`.

**Associate orders with payments**—When a customer pays for an order, a new `payments` object is associated with the order.

**Associate orders with refunds**—To handle refunds, a `refund` object is associated with the order. For manual refunds, a `credits` object is associated with the order.

> 🚧 IMPORTANT
> 
> Order totals are calculated dynamically and updated by the app that the merchant is using to handle orders. This means that if your app modifies an order, it must update the total as well.
> 
> See [Calculate order totals](doc:calculating-order-totals) for more information.

See [Use Clover REST API](doc:making-rest-api-calls) for more information on how to make REST API calls.

# Create an order

To create a new `order` object, send a `POST` request to `/v3/merchants/{mId}/orders`. While you can add options with your `POST` requests, none of these options are required.

## 1. Set order state

You must treat the initial `order` object as unfinished when the`state` is `null`. If you have not set the order's state to `open`, you can only `GET` the individual order using the UUID. You can't `GET` a `v3/merchants/{mId}/orders` response for orders in the `null` state.

For orders to display in the merchant's order list or in the **Orders** app, set the order's state to `open` as shown in the following example.

```curl Creating an order & setting the order state
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"state":"open"}'
```

> 📘 NOTE
> 
> Orders with a `null` state won't be visible on the **Orders** app on the device, but will be visible on the dashboard if you have a total set.

## 2. Set order type

You can classify merchant orders as different order types, such as online, delivery, pick-up, or dine-in. Each order type is specific to the merchant.

To create an order type, send a `POST` request to `/v3/merchants/{mId}/order_types`. You can also assign specific rules, such as `minOrderAmount` or `hoursAvailable`. While other values can be set in this `POST` request, none of the values are required. The response returns a unique order type `id`.

> 👍 TIP
> 
> To view a deleted order, filter your request with `deletedTime`. You can retrieve it by sending a `GET` request to `/v3/merchants/{mId}/orders`. 
> 
> For example, `/v3/merchants/mId/orders?filter=deletedTime>=1596501066`. See [Apply filters](doc:applying-filters) for more information about using filters in the REST API.

## 3. View orders

To view all orders created by a merchant, send a `GET` request to `/v3/merchants/{mId}/orders`. In response, all the merchant's orders are retrieved. 

To view a single order created by a merchant, send a `GET` request to `/v3/merchants/{mId}/orders/{orderId}`. In response, the specified order is retrieved.

You can also view orders using the **Orders** app on your test merchant's dashboard. See [Clover Help](https://www.clover.com/help) for more information about how merchants use orders.

# Add order line Items

After you create an `order` object, you can add line items by sending a `POST` request to `/v3/merchants/{mId}/orders/{orderId}/line_items`.

Each line item represents a single inventory item, a single portion of a variable-price item, or an individual custom item or manual transaction amount. You can build the line item using the current state of the referenced inventory item. Any additional line item properties you provide on the request, such as tax rates or item prices, are ignored. Use the [`bulk_line_items` endpoint] \(#creating-multiple-line-items) to override Clover inventory properties.

You can add order line items in two ways:

## 1. Add an inventory item

```curl Creating a line item with an inventory item ID
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/line_items' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"item":{"id":"{itemId}"}}'
```

In response, a line item `id` is generated.

## 2. Add a custom line item

To create a custom line item, include the price and tax information.

Merchants can add tax rates under **Setup > Taxes & Fees** on the Merchant Dashboard. To add tax rates, send a `POST` request to `/v3/merchants/mId/tax_rates`. To retrieve a merchant's tax rate information, send a `GET` request to `/v3/merchants/{mId}/tax_rates`.

See the [Clover Help](https://www.clover.com/en-US/help) for more information about how merchants use taxes and fees.

```curl Creating a line item with a price
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/line_items' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"price":1200,"name":"Caesar Salad",
"taxRates":[{"rate":1000000,"id":"{taxRateId}","name":"State tax","isDefault":true}]}'
```

In response, a line item `id` is generated.

> 👍 TIP
> 
> If your payload for a request to the `line_items` endpoint includes more than one item, only the last item in the payload is added to the order. Use the `bulk_line_items` endpoint to add multiple line items.

# Create multiple line items

Use the `v3/merchants/mId/orders/orderId/bulk_line_items` endpoint to create multiple line items in a single request.  This endpoint allows you to add ad hoc line items or reference Clover inventory while overriding its properties such as taxRates, price, name, and so on.

```curl Override tax rate
curl --request POST \
  --url 'https: //sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/bulk_line_items' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'Content-Type: application/json'
  --data-raw '{
    "items": [
        {
            "item": {
                "id": "{CloverInventoryItemUUID}"
            },
            "price": 100,
            "name": "Hamburger",
            "taxRates": [
                {
                    "id": "{taxRate UUID}",
                    "rate": 200000,
                    "name": "Sales Tax"
                }
            ]
        },
        {
            "item": {
                "id": "{CloverInventoryItemUUID}"
            },
            "price": 1000,
            "name": "Coke"
        }
    ]
}'
```
```curl Flat tax
curl --request POST \
  --url 'https: //sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/bulk_line_items' \
  --header 'Authorization: Bearer {access_token}' \
  --header 'Content-Type: application/json'
  --data-raw '{
    "items": [
        {
            "item": {
                "id": "{CloverInventoryItemUUID}"
            },
            "price": 500,
            "name": "Coffee",
            "taxRates": [
                {
                    "id": "{taxRate UUID}",
                    "taxAmount": 100,
                    "rate": 0,
                    "name": "Sales Tax"
                }
            ]
        },
        {
            "item": {
                "id": "{CloverInventoryItemUUID}"
            },
            "price": 300,
            "name": "Muffin"
        }
    ]
}'
```

> 👍 TIP
> 
> If your app caches inventory items, you should also register for Webhook notifications so that you know when item prices are updated or when items are added or removed from the inventory.

# Add item modifiers

You can add modifiers to customize individual `line_items`. Use modifiers to add any extras to an order, such as salad add-ins or extra toppings on ice cream.

To create a modifier, you first create a modifier group (`Salad add-ins`) with `/v3/merchants/{mId}/modifier_groups` and then add a modifier (`Avocado`) to the group with `/v3/merchants/{mId}/modifier_groups/{modifierId}/modifiers`. You can also add modifier groups and modifiers under **Inventory > Modifier Groups** on the Merchant Dashboard.

See [Clover Help](https://www.clover.com/en-US/help) for more information about how merchants use modifiers.

To add a modifier to a line item, send a `POST` request to `/v3/merchants/{mId}/orders/{orderId}/line_items/{lineItemId}/modifications`.

```curl Adding a modifier to a line item
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/line_items/{lineItemId}/modifications' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"modifier":{"id":"{modifierId}"}}'
```

# Add discounts

You can add custom discounts to a single line item or an entire order.

## 1. Add discounts to a single line item

To add a discount to a single line item, send a `POST` request to `/v3/merchants/{mId}/orders/{orderId}/line_items/{lineItemId}/discounts`. The `name`, and  `percentage` or negative `amount` values are required.

```curl 25% line item discount
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/line_items/{lineItemId}/discounts' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"name":"25% off select salads","percentage":25}'
```
```curl $1 line item discount
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/line_items/{lineItemId}/discounts' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"name":"lunch deal","amount":-100}'
```

## 2. Add discounts to an entire order

To add a discount to an entire order, send a `POST` request to `/v3/merchants/{mId}/orders/{orderId}/discounts`. The `name`, and `percentage` or negative `amount` values are required.

```curl 15% order discount
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/discounts' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"name":"15th visit 15% off","percentage":15}'
```

See [Clover Help](https://www.clover.com/en-US/help) for more information about how merchants use discounts.

# Add service charges

Clover merchants can add service charges based on local, state, and country laws or card brand rules. Merchants can add service changes under **Setup** > **Additional Charges** on the dashboard. To retrieve a merchant's service charge information, send a `GET` request to: `/v3/merchants/{mId}/default_service_charge`.

To add a service charge modifier to a line item, send a `POST` request to: `/v3/merchants/{mId}/orders/{orderId}/line_items/{lineItemId}/service_charge`.

```curl 5% service charge
curl --request POST  \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/service_charge' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"id":"{serviceChargeId}","name":"Service charge",
"enabled":true,"percentageDecimal":50000}'
```

See [Clover Help](https://www.clover.com/en-US/help) for more information about how merchants use service charges.
