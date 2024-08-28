---
title: "Request a checkout"
slug: "making-a-checkout-request"
excerpt: ""
hidden: false
metadata: 
  description: "The create checkout endpoint is used to request a new checkout session for a customer transaction. Requests for this endpoint are authenticated with the merchant's hosted checkout private token."
  image: []
  robots: "index"
createdAt: "Fri Nov 20 2020 16:51:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


# REST endpoint

Use the [Create checkout](https://docs.clover.com/reference/createcheckout) endpoint to request a new checkout session for a customer transaction. Requests for this endpoint are authenticated with the merchant's hosted checkout private token. When the merchant sets up hosted checkout, the tokens created are automatically set with the required Clover permissions.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/90f31d4-hc-tokens.png",
        "hc-tokens.png",
        1038
      ],
      "border": true
    }
  ]
}
[/block]


> 📘 Note
> 
> Tokens created when the merchant sets up hosted checkout are automatically set with the required Clover permissions.

## Required data

At a minimum, a checkout session request must include an empty `customer` object and a `shoppingCart` with one or more items.

```json
{
  "customer": {},
  "shoppingCart": {
    "lineItems": [
      {
        "name": "Floor lamp",
        "unitQty": 1,
        "price": 10900
      }
    ]
  }
}
```

The cart provides information about the item or items being purchased. Items are represented in a `shoppingCart` object composed of the following fields. The cart contains a `lineItems` array of one or more `lineItem` objects. A `lineItem` must include a `price` in cents, a `name`, and the `unitQty` (the number of the item the customer is purchasing).

### Optional customer information

You can provide a better user experience by sending additional data in your request. If you include the customer’s name and contact information, this data will be populated in the checkout form. The `customer` object can include the following fields:

- `firstName`
- `lastName`
- `phoneNumber`
- `email` (this address receives a receipt when the checkout process is finished)

```json
{
  {
    "customer": {
      "email": "customer@example.name",
      "firstName": "Customer",
      "lastName": "Name",
      "phoneNumber": "6205551010"
    }
  }
}
```

### Optional cart information

A cart’s `lineItems` can include a `note` to further describe the item. For example, you may need to provide additional information about the item if there are variants available for purchase. If you want to add tax information to a line item, see [Adding taxes to transactions](https://docs.clover.com/docs/making-a-checkout-request#adding-taxes-to-transactions).

```json
{
  "lineItems": [
    {
      "note": "No pulp",
      "name": "Orange juice",
      "price": 600,
      "unitQty": 2
    },
    {
      "note": "Non-dairy",
      "name": "French toast",
      "price": 1200,
      "unitQty": 1
    }
  ]
}
```

### Adding taxes to transactions

Because your requests are not linked to the merchant’s Clover inventory, any default tax configuration is not applied to hosted checkout payments. There are two requirements for taxes to be applied to a request: 

- The merchant must have an existing tax rate.
- The tax is included on any applicable line items in the request. Add the `taxRates` array and a `rate` whose value matches one of the merchant’s tax rates. The `rate` is an integer where a 10% tax is defined as `1000000`. If more than one rate has the same value, the first will be used for the checkout process.

```json
{
  "lineItems": [
    {
      "name": "Mug",
      "price": 1000,
      "unitQty": 1,
      "taxRates": [
        {
          "name": "CO state tax",
          "rate": 1000000
        }
      ]
    }
  ]
}
```
