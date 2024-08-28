---
title: "Manage categories"
slug: "managing-categories"
excerpt: ""
hidden: false
metadata: 
  description: "Use the REST API, to build custom solutions for creating, managing, and querying categories."
  image: []
  robots: "index"
createdAt: "Tue Feb 02 2021 19:31:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to\nthe partner docs. -->\n\n<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Merchants group similar items into categories. For example, in a restaurant, a merchant can create categories for `Salads` and `Beverages`. In the Clover Register app, merchants see categories and items under those categories.

Using the REST API, you can build custom solutions to create, manage, and query categories.

# Create a category

1. Send a `POST` request to `/v3/merchants/{mId}/categories`. 
2. Enter required information—`name` . 
3. Assign a `colorCode` to a category using the hex values.

```curl Create a category
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/categories' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"name":"Salads",'colorCode': '#FF00Z011'}'
```

```json Sample response
{
    "id": "AN7WTGHSKE9XG", // category ID
    "name": "Salads",
    'colorCode': '#FF00Z011'
    "sortOrder": 0
}
```

In response, a unique category `id` is generated. By default, the `sortOrder` value is set as the last category in the Clover Register and Dining apps. For example, if you already have five categories, the new category is sixth in the sort order.

# Manage items in a category

## Associate items with a category

1. Send a `POST` request to `/v3/merchants/{mId}/category_items`. 
2. Enter required information—category `id` and item `id`.

```curl Associate items with a category
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/category_items' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"elements":[{"category":{"id":"{categoryId}"},"item":{"id":"{item1Id}"}},{"category":{"id":"{categoryId}"},"item":{"id":"{item2Id}"}}]}'
```

## Search categories associated with an item

1. Send a `GET` request to `/v3/merchants/{mId}/items/{itemId}?expand=categories`. 
2. Enter required information—item `id`.

```curl Search categories associated with an item
curl --request GET \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/items/{itemId}?expand=categories' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```

```json Sample response
{
    "id": "N2WWSQBTAADZC", // item ID
    "hidden": false,
    "name": "Greek Salad",
    ...
    "categories": { // expansion
        "elements": [
            {
                "id": "AN7WTGHSKE9XG",
                "name": "Salads",
             		“colorCode”: “#FF00Z011”
                "sortOrder": 0
            }
        ]
    },
    "modifiedTime": 1611643817000
}
```

In response, the `categories` expansion displays categories associated with the item. See [Use expandable fields](doc:expanding-fields) for more information on working with `expand` parameters in your requests.

## Delete item associations

To delete an association between an item and a category:

1. Send a `POST` request to `/v3/merchants/{mId}/category_items?delete=true`.
2. Enter required information—category `id` and item `id`.
3. Set the `delete` value as `true`.

```curl Delete an association between an item and category
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/category_items?delete=true' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"elements":[{"category":{"id":"{categoryId}"},"item":{"id":"{itemId}"}}]}'
```

# Search items in a category

1. Send a `GET` request to `/v3/merchants/{mId}/categories/{categoryId}/items`. 
2. Use filters and expansions to indicate the search parameters.

```curl Search items in a category
curl --request GET \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/categories/{categoryId}/items?filter=modifiedTime>={unix_time}' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```

```json Sample response
{
    "elements": [
        {
            "id": "N2WWSQBTAADZC", // item ID
            "hidden": false,
            "name": "Greek Salad",
            ...
          	"modifiedTime": 1611643817000
        },
        {
            "id": "9J1F7WW503CZW", // item ID
            "hidden": true,
            "name": "Caesar Salad",
            ...
          	"modifiedTime": 1611644393000
        }
    ],
    "href": "http://sandbox.dev.clover.com/v3/merchants/{mId}/categories/{categoryId}/items?filter=modifiedTime%3E%3D1611643817000&limit=100"
}
```

See [Apply filters](doc:applying-filters) for more information on working with the `filter` parameter. See the [API reference](https://docs.clover.com/reference/api-reference-overview) for more information about available filters.
