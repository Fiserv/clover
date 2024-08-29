---
title: "Work with customers (SDK)"
slug: "working-with-customers-sdk"
excerpt: ""
hidden: false
metadata: 
  description: "This tutorial explains how you can use a Clover Ecommerce SDK to create and update customers."
  image: 
    - "https://files.readme.io/8e634d4-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Jan 31 2020 17:07:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Knowing customer information is central to running a business, so the SDK provides ways for apps to create and maintain up-to-date customer data. Especially important is the ability to connect a customer and card token so that return customers can make payments quickly and easily.

# Create a customer

To create an order, call the [`create a customer`](https://docs.clover.com/reference/createcustomer) endpoint and pass in the minimum required customer information, the customer's `email` and a `source`, the card token used for payments.

```python Python
from clover import Customer

customer = Customer.create(
    email='sample.email@example.com',
    source='clv_1TSTSpbfbN6Jh5CqCm3bMQne'
)
```
```javascript Node
require('dotenv').config();
const Clover = require("clover-ecomm-sdk");

let ACCESS_TOKEN = process.env.ACCESS_TOKEN;
let ENVIRONMENT = process.env.ENVIRONMENT;

const cloverInst = new Clover(ACCESS_TOKEN, {
  environment: ENVIRONMENT
});

let customer = cloverInst.customers.create({
    email:'sample.email@example.com',
    source:'clv_1TSTSpbfbN6Jh5CqCm3bMQne'
});
```

This returns a token object in JSON. The `id` value is the unique identifier of the customer.

```json Create customer response
{
    "id": "ANKHTCV4BZCVW",
    "object": "customer",
    "created": 1580489482717,
    "currency": "usd",
    "email": "sample.email@example.com",
    "sources": {
        "object": "list",
        "data": [
            "7E8EH4WWHK5N6"
        ],
        "has_more": False
    },
    "shipping": {}
}
```

Additional customer data, such as their `name`, `phone` and `shipping` details, can be included in the request.

```python
from clover import Customer

customer = Customer.create(
    email='sample.email@example.com',
    source='clv_1TSTSpbfbN6Jh5CqCm3bMQne',
    shipping={
        'address': {
            'city': 'Sunnyvale',
            'state': 'CA',
            'line1': '415 N Mathilda Ave',
            'postal_code': '94085'
        }
    },
    name='New Customer',
    phone='555-0125'
)
```
```javascript Node
require('dotenv').config();
const Clover = require("clover-ecomm-sdk");

let ACCESS_TOKEN = process.env.ACCESS_TOKEN;
let ENVIRONMENT = process.env.ENVIRONMENT;

const cloverInst = new Clover(ACCESS_TOKEN, {
  environment: ENVIRONMENT
});

let customer = cloverInst.customers.create({
    email:'sample.email@example.com',
    source: 'clv_1TSTSpbfbN6Jh5CqCm3bMQne',
    shipping: {
      'address': {
          'city': 'Sunnyvale',
          'state': 'CA',
          'line1': '415 N Mathilda Ave',
          'postal_code': '94085'
      }
  },
  name: 'New Customer',
  phone: '555-0125'
});
```

# Update customer information

A customer may need to update their information if they get a new credit card, change addresses, or for a number of other reasons. To update the customer, call the [`update a customer`](https://docs.clover.com/reference/updatecustomer) method with the `id` of the customer and any data to be changed.

```python Python
from clover import Customer

update = Customer.modify(customerId, name="Updated Name")
```
```javascript Node
require('dotenv').config();
const Clover = require("clover-ecomm-sdk");

let ACCESS_TOKEN = process.env.ACCESS_TOKEN;
let ENVIRONMENT = process.env.ENVIRONMENT;

const cloverInst = new Clover(ACCESS_TOKEN, {
  environment: ENVIRONMENT
});

cloverInst.customers.update({
  customerId: customerId,
  name: 'Updated Name'
});
```

This returns a customer object in JSON. See the [REST API Reference](doc:rest-api-reference) for complete information about the returned values.

```json Update customer response
{
  'id': 'AKK8FZK1NCPWC', 
  'object': 'customer',
  'created': 1582322821472,
  'currency': 'usd',
  'email': 'sample.email@example.com',
  'phone': '555-0125', 
  'name': 'Updated Name',
  'sources': {
    'object': 'list',
    'data': ['01B0G1CT3GCBT'],
    'has_more': False},
  'shipping': {
    'name': 'Updated Name',
    'phone': '555-0125',
    'address': {
      'line1': '415 N Mathilda Ave',
      'city': 'Sunnyvale',
      'state': 'CA',
      'postal_code': '94085',
      'country': 'US'
      }
    }
}
```
