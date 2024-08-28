---
title: "Paginate requests"
slug: "ecommerce-paginating-requests"
excerpt: ""
hidden: false
metadata: 
  description: "Ecommerce requests can be paginated using specific query parameters."
  image: 
    - "https://files.readme.io/22ce0bd-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Wed Jun 10 2020 19:33:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Clover merchant data sets can be very large. This is why results are returned 10 items at a time by default.

To ensure you are retrieving results as expected, you can add query parameters to your request. These parameters can be used to page through large result sets. The hard limit is 100 items per request.

Three types of merchant data can be requested with paging parameters: charges, orders, and refunds.

## Paginate using IDs

### Use `ending_before`

Your app may need to display data directly preceding an order, charge, or refund.

![](https://files.readme.io/d27b77a-ending_before.png "ending_before.png")

The following example shows a request for a specific order and two orders preceding it, a total of three indicated by `limit=3`.

```curl Request orders preceding the specified order
curl -s "https://scl-sandbox.dev.clover.com/v1/orders? \
limit=3&ending_before=6E72X1BW38A7T" \
--header "Authorization: Bearer {auth_token}"
```

The response includes the type of object returned (a `list`), an indication that additional data can be retrieved with subsequent requests (`has_more` is `true`), and the `data` array of order objects. The first order object is the order with the `id` set as the parameter value.

```json
{
  "object": "list",
  "url": "/v1/orders",
  "has_more": true,
  "data": [
    {
      "id": "6E72X1BW38A7T",
      "amount": 730,
      "currency": "USD",
      "items": [
        {
          "quantity": 1,
          "amount": 730,
          "description": "Mouse pad"
        }
      ]
    },
    {
      "id": "AH4FZD4FXQ07P",
      "amount": 333,
      "currency": "USD"
    },
    {
      "id": "4GW5A6GDWA12J",
      "amount": 10300,
      "currency": "USD",
      "charge": "MZHCSGW4T1KGR",
      "items": [
        {
          "parent": "839XNWK1ZFFQG",
          "amount": 10208,
          "description": "Keyboard"
        },
        {
          "amount": 92,
          "description": "Charity Donation"
        }
      ]
    }
  ]
}
```

### Use `starting_after`

Your app may need to display data that follows a specific order, charge, or refund. 

![](https://files.readme.io/231f9ca-starting_after.png "starting_after.png")

The following example shows a request for a specific order and the four following it, a total of five indicated by `limit=5`.

```curl Request orders after the specified order
curl -s "https://scl-sandbox.dev.clover.com/v1/orders? \ 
starting_after=KHZKKMAFPEPKW&limit=5" \
--header "Authorization: Bearer {auth_token}"
```

The response includes the type of object returned (a `list`), an indication that additional data can be retrieved with subsequent requests (`has_more` is `true`), and the `data` array of order objects. The first order object is the order with the `id` set as the parameter value.

```text starting_after response
{
  "object": "list",
  "url": "/v1/orders",
  "has_more": true,
  "data": [
    {
      "id": "KHZKKMAFPEPKW",
      "amount": 1899,
      "currency": "USD",
      "items": [
        {
          "quantity": 1,
          "amount": 1899,
          "description": "Mouse"
        }
      ]
    },
    {
      "id": "4GW5WA12WA4SJ",
      "amount": 10300,
      "currency": "USD",
      "charge": "MZHCSGW4T1KGR",
      "items": [
        {
          "parent": "83A6GDWAZFFQG",
          "amount": 10208,
          "description": "USB-C cable"
        }
      ]
    },
    {
      "id": "0XKSYBWV0R9TW",
      "amount": 354,
      "currency": "USD",
      "charge": "ASZ9SGWX8Z2K4",
      "items": [
        {
          "quantity": 1,
          "amount": 354,
          "description": "Capacitor"
        }
      ]
    },
    {
      "id": "JAKQDHRFX5XKM",
      "amount": 411,
      "currency": "USD",
      "charge": "T19YVH7NCV4AM",
      "items": [
        {
          "quantity": 1,
          "amount": 411,
          "description": "Bluetooth interface"
        }
      ]
    }
    {
      "id": "4GW5A6GDWA12J",
      "amount": 10208,
      "currency": "USD",
      "charge": "MZHCSGW4T1KGR",
      "items": [
        {
          "parent": "839XNWK1ZFFQG",
          "amount": 10208,
          "description": "Headphones"
        }
      ]
    }
  ]
}
```

## Request data using date and time

To return information about orders, charges, or refunds relative to a certain date and time, requests can be refined using the `created` timestamp. You can specify an exact Unix timestamp (in milliseconds) or define an interval in which to search. 

The following request retrieves the first five charges created during the specified range.

```curl Request first five charges for a date/time range
curl -s "https://scl-sandbox.dev.clover.com/v1/charges? \
created.gt=1585699200000&created.lt=1586044800000&limit=5" \
--header "Authorization: Bearer {auth_token}"
```

~~~text \`created\` range response
{
  "object": "list",
  "url": "/v1/charges",
  "has_more": true,
  "data": [
    {
      "id": "QNMZE1X9ZVT8T",
      "amount": 347,
      "currency": "usd",
      "created": 1585849840000,
      ...
    },
    {
      "id": "ASZ9SGWX8Z2K4",
      "amount": 354,
      "currency": "usd",
      "created": 1585896286590,
      ...
    },
    {
      "id": "P031SMNP173HG",
      "amount": 462,
      "currency": "usd",
      "created": 1585796590000,
      ...
    },
    {
      "id": "MZHCSGW1T1KGR",
      "amount": 10300,
      "currency": "usd",
      "created": 1585799269800,
      ...
    },
    {
      "id": "N8P065DGDVM72",
      "amount": 10502,
      "currency": "usd",
      "created": 1585699400000,
      ...
    }
  ]
}
~~~

Note that the response includes the `has_more` property to indicate that additional results exist in the range. You can then use the `starting_after` parameter in a subsequent request to retrieve the next set of results.
