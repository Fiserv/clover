---
title: "Manage items and item groups"
slug: "managing-items-item-groups"
excerpt: ""
hidden: false
metadata: 
  description: "Clover merchants create and manage inventory items with the Clover Inventory app. With the REST API, you can build custom solutions for creating and managing items, stock quantities, and item groups."
  image: []
  robots: "index"
createdAt: "Tue Feb 02 2021 18:45:11 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to\nthe partner docs. -->\n\n<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Each item in the merchant inventory is represented by an `items` object. Clover merchants create and manage inventory items with the Clover Inventory app.

With the REST API, you can build custom solutions to create and manage items, stock quantities, and item groups.

# Create an item for the inventory

1. Send a `POST` request to `/v3/merchants/{mId}/items`. 
2. Enter required information—`name` and `price` (in cents).
3. Assign a colorCode to an item using the hex values.

```curl Create an item
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/items' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"name":"Caesar Salad","price":1200,”colorCode”:#FF0080”}'
```

> 📘 NOTE
> 
> All money amount values are represented in cents. For example, $20.99 is represented as an amount value of `2099`.
> 
> For merchants that use value-added tax (VAT), the `price` value includes tax. In this case, set `priceWithoutVat` as the base price without VAT.

```json Sample response
{
    "id": "9J1F7WW503CZW", // item ID
    "hidden": false,
    "name": "Caesar Salad",
    "price": 1200,
    "priceType": "FIXED",
    "defaultTaxRates": true,
    "isRevenue": true,
    "modifiedTime": 1611609459000
  	"colorCode": "#FF0080"
}
```

In response, a unique item `id` is generated. The `hidden`, `priceType`, and `isRevenue` values are set by default. See the [API reference](https://docs.clover.com/reference/inventorycreateitem) for more information on the complete list of values you can set.

# Update item stock

1. Send a `POST` request to `/v3/merchants/{mId}/item_stocks/{itemId}`. 
2. Enter required information—`quantity`.

```curl Update item stock
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/item_stocks/{itemId}' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"item":"9J1F7WW503CZW","quantity":4,”colorCode”:#FF0080”}'
```

In response, the `quantity` value is updated.

# View track and update inventory stock status for the merchant

On the Merchant Dashboard > **Inventory > Setup**, merchants can update settings for the Clover Inventory app to track and update the stock of items. Send a `GET` request to view the track and update inventory stock status for a merchant `/v3/merchants/{mId}/properties`.

In response:

- The `trackStock` value specifies whether the Clover Inventory app is used to track item stock count.
- The `updateStock` value specifies whether the Clover Inventory app is used to automatically update item stock count.

# Search items in the inventory

1. Send a `GET` request to `/v3/merchants/{mId}/items`. 
2. Use filters and expansions to indicate the search parameters.

In the following example, the `filter` parameter is used to filter by modified time and the `expand` parameter is used to provide more information about item stock.

```curl Search items
curl --request GET \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/items?filter=modifiedTime>={unix_time}&expand=itemStock' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```

```json Sample response
{
    "elements": [
        {
            "id": "N2WWSQBTAADZC", // item matches filter
            "hidden": false,
            "name": "Greek Salad",
            ...
            "itemStock": {  // expansion
                "item": {
                    "id": "N2WWSQBTAADZC"
                },
               ...
                "quantity": 5.0,
                "modifiedTime": 1611643868000
            },
            "modifiedTime": 1611643817000
        }
    ],
    "href": "http://sandbox.dev.clover.com/v3/merchants/{mId}/items?filter=modifiedTime%3E%3D1611609459000&limit=100"
}
```

In response, items that match the search filter are displayed. The `itemStock` expansion displays the `quantity` of each listed item.

See [Apply filters](doc:applying-filters) and [Use expandable fields](doc:expanding-fields) for more information on working with `filter` and `expand` parameters in your requests. See the [API reference](https://docs.clover.com/reference/inventorycreateitem) for more information about available filters and expansions.

# Create an item group for item variants

Merchants use item groups to manage variants of a single item.

For example, in a T-shirt item group, you can create variants for color (Red, Blue, Green) and size (Small, Medium, Large). In the Clover Register app, merchants can select a `Long sleeve crew neck` item in color `Blue` and size `Large`.

To create an item group:

1. Send a `POST` request to `/v3/merchants/{mId}/item_groups`. 
2. Enter required information—group `name`.

```curl Create an item group
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/item_groups' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"name":"T-shirt"}'
```

```json Sample response
{
    "id": "FBAAX81VXHDP0", // item group ID
    "name": "T-shirt"
}
```

2. To add attributes to the item group, send a `POST` request to `/v3/merchants/{mId}/attributes`. 
3. Enter required information—group `id` and attribute `name`.

```curl Create an attribute
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/attributes' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"itemGroup":{"id":"{itemGroupId}"},"name":"Size"}'
```

```json Sample response
{
    "id": "12XGR3RNHG8FW", // attribute ID
    "name": "Size",
    "itemGroup": {
        "id": "FBAAX81VXHDP0" // group ID
    }
}
```

3. To add attributes options, send a `POST` request to `/v3/merchants/{mId}/attributes/{attributeId}/options`. 
4. Enter required information—attribute `id` and option `name`. For example, you can create options like `Small`, `Medium`, and `Large` for the `Size` attribute.

```curl Create an option
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/attributes/{attributeId}/options' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"name":"Large"}'
```

```json Sample response
{
    "id": "V5EKKX8XDA05M", // option ID
    "name": "Large",
    "attribute": {
        "id": "12XGR3RNHG8FW" // attribute ID
    }
}
```

4. Use the item group `id` (from step 1) and send a `POST` request to create (`/v3/merchants/{mId}/items`) or update (`/v3/merchants/{mId}/items/{itemId}`) an item with variants.

```curl Create an item and associate it with an item group ID
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/items' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"name":"Long sleeve crew neck","price":3000,"itemGroup":{"id":"FBAAX81VXHDP0"}}'
```

5. Create an association between items and options by sending a `POST` request to `/v3/merchants/{mId}/option_items`. The option `id` and item `id` values are required.

```curl Create an association between items and an option
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/option_items' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"elements":[{"option":{"id":"{optionId}"},"item":{"id":"{item1Id}"}},{"option":{"id":"{optionId}"},"item":{"id":"{item2Id}"}}]}'
```
