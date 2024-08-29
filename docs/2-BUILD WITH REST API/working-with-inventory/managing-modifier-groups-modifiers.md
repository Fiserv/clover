---
title: "Manage modifier groups and modifiers"
slug: "managing-modifier-groups-modifiers"
excerpt: ""
hidden: false
metadata: 
  description: "With the REST API, you can build custom solutions for creating, managing, and querying modifier groups."
  image: []
  robots: "index"
createdAt: "Tue Feb 02 2021 19:52:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
In restaurants and online ordering services, merchants use modifier groups and modifiers for customizing orders. These modifiers help restaurant kitchens to receive all the required details for an order. Clover Register, Counter Service, and Table Service apps in the US and Canada all support modifiers, modifier groups, and [variants](doc:managing-items-item-groups#creating-an-item-group-for-item-variants).

For example, in a `Salad Add-in` modifier group, you can have modifiers like `Tofu` and `Avocado`. In the Clover Register app, merchants can customize a `Caesar Salad` item with two `Tofu` modifier and three `Avocado` modifier additions.

With the REST API, you can build custom solutions to create, manage, and query modifier groups.

# Create a modifier group

1. Send a `POST` request to `/v3/merchants/{mId}/modifier_groups`. 
2. Enter required information—`name` value. 
3. Enter additional values—`minRequired` and `maxAllowed` for modifier limits that can be associated with order line items in the Clover Register app.

```curl Create a modifier group
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/modifier_groups' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
--data '{"name":"Salad Add-on"}'
```

```json Sample response
{
    "id": "QZ587JT76N80Y", // modifier group ID
    "name": "Salad Add-in",
    "showByDefault": true
}
```

In response, a unique modifier group `id` is generated. By default, the `showByDefault` value is set to `true`  for prompting merchants to add modifiers in the Clover Register app.

# Create a modifier

1. Send a `POST` request to `/v3/merchants/{mId}/modifier_groups/{modifierGroupId}/modifiers`. 
2. Enter required information—modifier `name` and `price`.

```curl Create a modifier
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/modifier_groups/{modifierGroupId}/modifiers' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"price":100,"name":"Tofu"}'
```

```json Sample response
{
    "id":"S47VGYX913K4T" // modifier ID
    "name":"Tofu"
    "price":100
    "modifierGroup":{
    "id":"QZ587JT76N80Y" // modifier group ID
    }
}
```

In response, a unique modifier `id` is generated.

# Manage items in a modifier group

## Associate items with a modifier group

1. Send a `POST` request to `/v3/merchants/{mId}/item_modifier_groups`. 
2. Enter required information—modifier group `id` and item `id`.

```curl Associate items with a modifier group
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/item_modifier_groups' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"elements":[{"modifierGroup":{"id":"{modifierGroupId}"},"item":{"id":"{item1Id}"}},{"modifierGroup":{"id":"{modifierGroupId}"},"item":{"id":"{item2Id}"}}]}'
```

## Search modifier groups associated with an item

1. Send a `GET` request to `/v3/merchants/{mId}/items/{itemId}?expand=modifierGroups`. 
2. Enter required information—item `id`.

```curl Search modifier groups associated with an item
curl --request GET \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/items/{itemId}?expand=modifierGroups' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```

```json Sample response
{
    "id": "N2WWSQBTAADZC", // item ID
    "hidden": false,
    "name": "Greek Salad",
    ...
    "modifierGroups": { // expansion
        "elements": [
            {
                "id": "QZ587JT76N80Y", 
                "name": "Salad Add-in",
                "showByDefault": true,
                "modifierIds": "S47VGYX913K4T,JRMCKCQK1XCGT",
                "items": {
                    "elements": [
                        {
                            "id": "N2WWSQBTAADZC"
                        }
                    ]
                }
            }
        ]
    },
    "modifiedTime": 1611643817000
}
```

In response, the `modifierGroups` expansion displays groups associated with the item. See [Expanding fields](doc:expanding-fields) for more information on working with `expand` parameters in your requests.

## Delete item associations

To delete an association between an item and a modifier group:

1. Send a `POST` request to `/v3/merchants/{mId}/category_items?delete=true`.
2. Enter required information—category `id` and item `id`. 
3. Set the `delete` value as `true`.

```curl Delete an association between an item and modifier group
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/item_modifier_groups?delete=true' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"elements":[{"modifierGroup":{"id":"{modifierGroupId}"},"item":{"id":"{itemId}"}}]}'
```

# Search items in a modifier group

1. Send a `GET` request to `/v3/merchants/{mId}/modifier_groups/{modifierGroupId}/items`.
2. Use filters and expansions to indicate the search parameters.

In the following example, the `filter` parameter is used to filter by price and the `expand` parameter is used to provide more information about categories.

```curl Search items in a modifier group
curl --request GET \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/modifier_groups/{modifierGroupId}/items?filter=price>=1000&expand=categories' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```

```json Sample response
{
    "elements": [
        {
            "id": "N2WWSQBTAADZC", //item matches filter
            "hidden": false,
            "name": "Greek Salad",
            "price": 1200
            ...
            "categories": { // expansion
                "elements": [
                    {
                        "id": "AN7WTGHSKE9XG",
                        "name": "Salads",
                        ...
                    }
                ]
            },
            "modifiedTime": 1611643817000
        }
    ],
    "href": "http://sandbox.dev.clover.com/v3/merchants/{mId}/modifier_groups/{modifierGroupId}/items?filter=price%3E%3D1000&limit=100"
}
```

In response, items that match the search filters are displayed.

See [Apply filters](doc:applying-filters) and [Use expandable fields](doc:expanding-fields) for more information on working with `filter` and `expand` parameters in your requests. See the [API reference](ref:modifiergetmodifiergroupitems) for more information about available filters.
