---
title: "Manage item availability"
slug: "managing-item-availability"
excerpt: ""
hidden: false
metadata: 
  description: "Manage inventory item availability automatically or manually."
  image: []
  robots: "index"
createdAt: "Tue Feb 08 2022 17:10:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


With the REST API, you can build custom solutions for your merchants to manage item availability.  
Example: You can create a custom solution to remove an out-of-stock item from the ordering process until the item is available for ordering again. This solution improves order accuracy because customers can order only the available items in the stock.

## Manage item availability on the Merchant Dashboard

Merchants can manage an item's availability automatically or manually on the Merchant Dashboard.

- **Auto-manage item availability**—To use the auto-manage feature, merchants must turn on **Track stock** on the Inventory Setup page. If Track stock is turned off, the merchant can only manually control an item's availability.

- **Automatically decrease stock count**—When a merchant is tracking stock, they can also turn on the **Update item count** after each sale to automatically adjust the stock count for point of sale (POS) and online orders.

  - When the stock count reaches zero, items are unavailable for ordering.
  - When the stock is updated to at least one, the item is available for ordering.

- **Manually manage item availability—**Merchants can use the Inventory app on the Dashboard and the Register, Dining, and Inventory apps on their devices to manually manage the availability of items.

## Webhook notifications and developer action

When an item becomes unavailable, Clover sends a webhook notification that the item is updated. The webhook message contains the merchantId, webhook topic, and the item Universally Unique Identifier (UUID).  
You need to send a GET request for information about the item's status.

## View item stock count, availability, and auto-manage status

The `items` object indicates each item in the merchant inventory. To view an item stock count, whether or not an item is available for ordering, and if the item is auto-managed, send a `GET` request to `/v3/merchants/{merchant_id}/items/{item_id}`. 

### Request sample

```curl Search items
curl --request GET \
--url 'https://sandbox.dev.clover.com/v3/merchants/{merchant_id}/items/{item_id}' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```

### Response sample

Response values:

- `"available": false` if the item is not available for ordering.
- `"available": true` if the item is available for ordering.
- `"autoManage": true` if the merchant has set up auto-managing.
- `"autoManage": false` is the default setting. 

The following sample response displays that the item `"20 Wings"` is auto-managed (`"autoManage": true`). Since the stock count is zero (`"itemStock": 0`), the item (`"20 Wings"`) is unavailable for ordering (`"available": false`).

```json Sample response
{
  "id": "0ZHZ8Y66S63EP", 
  "hidden": false, 
  "available": false, 
  "autoManage": true,
  "name": "20 Wings", 
  "alternateName": "", 
  "code": "", 
  "sku": "", 
  "price": 1295, 
  "priceType": "FIXED", 
  "defaultTaxRates": false, 
  "unitName": "", 
  "cost": 0, 
  "isRevenue": true, 
  "itemStock": 0, 
  "modifiedTime": 1495477636000
}
```

## Set item as unavailable (manually)

If an item is managed manually, it is not dependent on the stock count and must be removed manually from ordering when it is unavailable:

1. Send a POST request to`/v3/merchants/{merchant_id}/items/{item_id}`.
2. Set `"available:"` to `false`.

On the **Merchant Dashboard **> **Inventory** > **Items page**, the merchant can manually change an item's availability.

## Update item stock quantity

1. Send a `POST` request to `/v3/merchants/{mId}/item_stocks/{itemId}`.
2. Include the required `quantity` value. For more information, see [Manage items and item groups](doc:managing-items-item-groups#updating-item-stock).

On the **Merchant Dashboard** > **Inventory **> **Items page**, the merchant can manually add to or remove from an item stock count. On the Item tracking page, the merchant can change the item to unavailable or available.
