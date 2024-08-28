---
title: "Manage tags"
slug: "managing-tags"
excerpt: ""
hidden: false
metadata: 
  description: "Merchants use tags or labels for keeping track of these items in reports. With the REST API, you can build custom solutions for creating, managing, and querying tags."
  image: []
  robots: "index"
createdAt: "Tue Feb 02 2021 22:08:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


In the REST API, item labels are identified as tags. Merchants use tags or labels for keeping track of these items in reports. With the REST API, you can build custom solutions for creating, managing, and querying tags.

# Create a tag

1. Send a `POST` request to `/v3/merchants/{mId}/tags`. 
2. Enter required information—`name`.
3. Set the `showInReporting` value to `true` for using the tag as a summary label in the Clover Reporting app.

```curl Create a tag
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/tags' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
--data '{"name":"Food & beverages","showInReporting":"true"}'
```

```json Sample response
{
    "id": "3VC6H9Y72N1NG" // tag ID
    "name": "Food & beverages"
    "showInReporting": true
}
```

In response, a unique tag `id` is generated.

# Manage tags

## Associate items with a tag

1. Send a `POST` request to `/v3/merchants/{mId}/tag_items`. 
2. Enter required information—tag `id` and item `id`.

```curl Associate items with a tag
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}tag_items' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"elements":[{"tag":{"id":"{tagId}"},"item":{"id":"{item1Id}"}},{"tag":{"id":"{tagId}"},"item":{"id":"{item2Id}"}}]}'
```

## Search tags associated with an item

1. Send a `GET` request to `/v3/merchants/{mId}/items/{itemId}?expand=tags`. 
2. Enter required information—item `id`.

```curl Search tags associated with an item
curl --request GET \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/items/{itemId}?expand=tags' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```

```json Sample response
{
    "id": "N2WWSQBTAADZC", // item ID
    "hidden": false,
    "name": "Greek Salad",
    ...
    "tags": { // expansion
        "elements": [
            {
                "id": "3VC6H9Y72N1NG",
                "name": "Food & beverages",
                "showInReporting": true,
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

In response, the `tags` expansion displays tags associated with the item. See [Use expandable fields](doc:expanding-fields) for more information on working with `expand` parameters in your requests.

## Delete item associations

To delete an association between an item and tag:

1. Send a `POST` request to `/v3/merchants/{mId}/tag_items?delete=true`. 
2. Enter required information—tag `id` and item `id`. 
3. Set the `delete` value as `true`.

```curl Delete an association between an item and tag
curl --request POST \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}tag_items?delete=true' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}' \
--data '{"elements":[{"tag":{"id":"{tagId}"},"item":{"id":"{itemId}"}}]}'
```

# Search items with a tag

1. Send a `GET` request to `/v3/merchants/{mId}/tags/{tagId}/items`. 
2. Use filters and expansions to indicate your search parameters.

In the following example, the `filter` parameter is used to filter by price and the `expand` parameter is used to provide more information about categories and modifier groups.

```curl Search items with a tag
curl --request GET \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/tags/{tagId}/items?filter=price=1000&expand=categories&expand=modifierGroups' \
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
            "price": 1000,
            ...
            "modifierGroups": { // expansion
                "elements": [
                    {
                        "id": "QZ587JT76N80Y",
                        "name": "Salad Add-in",
                        "showByDefault": true,
                        "modifierIds": "S47VGYX913K4T,JRMCKCQK1XCGT",
                        ...
                    }
                ]
            },
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
    "href": "http://sandbox.dev.clover.com/v3/merchants/{mId}/tags/{tagId}/items?filter=price%3E%3D1000"
}
```

In response, items that match the search filter are displayed.

See [Apply filters](doc:applying-filters) and [Use expandable fields](doc:expanding-fields) for more information on working with `filter` and `expand` parameters in your requests. See the [API reference](https://docs.clover.com/reference/api-reference-overview) for more information on available filters and expansions.
