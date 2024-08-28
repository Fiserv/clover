---
title: "Use object associations"
slug: "using-object-associations"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to use object associations in Clover to create many-to-many associations between objects, such as adding an item to a category, using dedicated endpoints."
  image: 
    - "https://files.readme.io/95cc58b-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Sep 07 2018 03:08:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:24 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n  <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Many-to-many associations between objects require their own endpoints. If you want to add an item to a category, for example, we require that you create the item, create the category, and then use an object association call to link the two. We support object associations with the following calls:

- `/v3/merchants/{mId}/category_items`: category to an item
- `/v3/merchants/{mId}/item_modifier_groups`: modifier group to an item
- `/v3/merchants/{mId}/option_items`: option to an item
- `/v3/merchants/{mId}/tax_rate_items`: tax rate to an item
- `/v3/merchants/{mId}/tag_items`: label to an item

See the [API Reference](ref:api-reference-overview) for more information.

## Example—Associate categories and items

To create an association, `POST` a tuple of the two object IDs to the association endpoint.

```json Associate one item and one category
$ cat /tmp/category_items.json
{
  "elements": [
    { "category": {"id": "Y906VJJHTNCVW"}, "item": {"id": "7PARQ2Z2G0336"}}
  ]
}

$ curl -s -X POST "https://apisandbox.dev.clover.com/v3/merchants/{mId}/category_items" --header "Authorization: Bearer {API_Token}" -H "Content-Type: application/json" --data "[Content from category_items.json]"
```

To create multiple associations in one call, `POST` a list of tuples. The following example associates three items with two categories:

```json Payload for multiple item/category associations
{
  "elements": [
      { "item": {"id": "ABWN2X43EXJN8"}, "category": {"id": "J615DCVPX97JG"} },
      { "item": {"id": "ABWN2X43EXJN8"}, "category": {"id": "PBRT27S9JBSK8"} },
      { "item": {"id": "F1RBG5MKD3SQR"}, "category": {"id": "J615DCVPX97JG"} },
      { "item": {"id": "F1RBG5MKD3SQR"}, "category": {"id": "PBRT27S9JBSK8"} },
      { "item": {"id": "S9230FJR93DFJ"}, "category": {"id": "J615DCVPX97JG"} },
      { "item": {"id": "S9230FJR93DFJ"}, "category": {"id": "PBRT27S9JBSK8"} }
  ]
}
```

To remove an association, add the `?delete=true` query parameter to the URL and send the tuple payload. 

```json Remove item/category association
$ cat /tmp/category_items.json
{
  "elements": [
    { "category": {"id": "Y906VJJHTNCVW"}, "item": {"id": "7PARQ2Z2G0336"}}
  ]
}

$ curl -s -X POST "https://apisandbox.dev.clover.com/v3/merchants/{mId}/category_items?delete=true" --header "Authorization: Bearer {API_Token}" -H "Content-Type: application/json" --data "[Content from category_items.json]"
```

To remove all items from a category, use a payload with the category and no items:

```json Remove all associated items from a category
$ cat /tmp/category_items.json
{
  "elements": [
    { "category": {"id": "Y906VJJHTNCVW"}}
  ]
}

$ curl -s -X POST "https://apisandbox.dev.clover.com/v3/merchants/{mId}/category_items?delete=true" --header "Authorization: Bearer {API_Token}" -H "Content-Type: application/json" --data "[Content from category_items.json]"
```

To remove all categories from an item, use a payload with the item and no category:

```json Remove all category associations from an item
$ cat /tmp/category_items.json
{
  "elements": [
    { "item": {"id": "7PARQ2Z2G0336"}}
  ]
}

$ curl -s -X POST "https://apisandbox.dev.clover.com/v3/merchants/{mId}/category_items?delete=true" --header "Authorization: Bearer {API_Token}" -H "Content-Type: application/json" --data "[Content from category_items.json]"
```
