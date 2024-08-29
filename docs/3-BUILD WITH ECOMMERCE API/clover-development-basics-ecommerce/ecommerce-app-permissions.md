---
title: "Ecommerce app permissions"
slug: "ecommerce-app-permissions"
excerpt: ""
hidden: false
metadata: 
  description: "Ecommerce apps require the merchant to grant specific permissions to access and modify data on their behalf. This page provides an endpoint-by-endpoint breakdown of the permissions."
  image: 
    - "https://files.readme.io/41d951c-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue Jan 21 2020 01:42:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:08:29 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to the \npartner docs. -->\n\n<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->"
}
[/block]


Your app must request specific permissions from merchants to access and update their data. In addition, on the Developer Dashboard, you must specify the [Ecommerce integration type](doc:ecommerce-integration-types) you are using for your app.

# Required app permissions

Merchants using your app grant your app permissions during installation, and your app will use the associated OAuth token to use for all API calls on behalf of the merchant. For more information, see [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth).

Your app should only request the minimum permissions required for your app to function.

## PAKMS service endpoint

[block:parameters]
{
  "data": {
    "h-0": "Operation",
    "h-1": "Required permission",
    "0-0": "Get public key  \n`GET /pakms/apikey`",
    "0-1": "Online payments"
  },
  "cols": 2,
  "rows": 1,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Tokenization service endpoint

[block:parameters]
{
  "data": {
    "h-0": "Operation",
    "h-1": "Required permissions",
    "0-0": "Create token  \n`POST /v1/tokens`",
    "0-1": "None"
  },
  "cols": 2,
  "rows": 1,
  "align": [
    "left",
    "left"
  ]
}
[/block]


> 🚧 IMPORTANT
> 
> To create a token using `POST /v1/tokens`, you need a public key retrieved from the PAKMS service.

## Ecommerce service endpoints

### Charge endpoints

[block:parameters]
{
  "data": {
    "h-0": "Operation",
    "h-1": "Required permissions",
    "0-0": "Create a charge  \n`POST /v1/charges`",
    "0-1": "Online payments",
    "1-0": "Capture an open charge  \n`POST /v1/charges/{chargeId}/capture`",
    "1-1": "Read payments  \nWrite payments  \nOnline payments",
    "2-0": "Get charges  \n`GET /v1/charges`",
    "2-1": "Read payments",
    "3-0": "Get a single charge  \n`GET /v1/charges/{chargeId}`",
    "3-1": "Read payments"
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


### Customer endpoints

[block:parameters]
{
  "data": {
    "h-0": "Operation",
    "h-1": "Required permissions",
    "0-0": "Create a card-on-file customer  \n`POST /v1/customers`",
    "0-1": "Read customers  \nWrite customers  \nOnline payments",
    "1-0": "Add a card to an existing customer  \n`PUT /v1/customers`",
    "1-1": "Read customers  \nWrite customers  \nOnline payments",
    "2-0": "Remove a card from an existing customer  \n`DELETE /v1/customers`",
    "2-1": "Read customers  \nWrite customers  \nOnline payments"
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]


### Order endpoints

[block:parameters]
{
  "data": {
    "h-0": "Operation",
    "h-1": "Required permissions",
    "h-2": "Additional permissions",
    "0-0": "Create an order  \n`POST /v1/orders`",
    "0-1": "Read merchant  \nRead orders  \nWrite orders",
    "0-2": "To add a customer:  \nRead customers  \n  \nTo add `tax_rates` to `items`:  \nRead inventory",
    "1-0": "Get orders  \n`GET /v1/orders`",
    "1-1": "Read orders  \nRead payments",
    "1-2": "",
    "2-0": "Get an order  \n`GET /v1/orders/{orderId}`",
    "2-1": "Read customers  \nRead merchant  \nRead orders  \nRead payments",
    "2-2": "",
    "3-0": "Pay for an order  \n`POST /v1/orders/{orderId}/pay`",
    "3-1": "Read customers  \nRead inventory  \nRead merchant  \nRead orders  \nRead payments  \nOnline payments",
    "3-2": "",
    "4-0": "Return an order  \n`POST /v1/orders/{orderId}/returns`",
    "4-1": "Read customers  \nRead merchant  \nRead orders  \nRead payments  \nOnline payments",
    "4-2": ""
  },
  "cols": 3,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


> 📘 NOTE
> 
> Getting an order with `GET /v1/orders/{orderId}` expands the following fields:
> 
> - `lineItems`
> - `lineItems.taxRates`
> - `payments`
> - `refunds`
> - `customers`

### Refund endpoints

[block:parameters]
{
  "data": {
    "h-0": "Operation",
    "h-1": "Required permissions",
    "0-0": "Get refunds  \n`GET /v1/refunds`",
    "0-1": "Read payments",
    "1-0": "Get a refund  \n`GET /v1/refunds/{refundId}`",
    "1-1": "Read payments",
    "2-0": "Refund a charge  \n`POST /v1/refunds`",
    "2-1": "Read customers  \nRead merchant  \nRead orders  \nRead payments  \nOnline payments"
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Recurring Payments service endpoints

### Plan endpoints

[block:parameters]
{
  "data": {
    "h-0": "Operation",
    "h-1": "Required permissions",
    "0-0": "Create plan  \n`POST /v1/plans`",
    "0-1": "Read merchant  \nWrite merchant",
    "1-0": "Get a plan  \n`GET /v1/plans/{planId}`",
    "1-1": "Read merchant",
    "2-0": "Edit a plan  \n`PUT /v1/plans/{planId}`",
    "2-1": "Read merchant  \nWrite merchant",
    "3-0": "Deactivate a plan  \n`PUT /v1/plans/{planId}`",
    "3-1": "Read merchant  \nWrite merchant"
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


### Subscription endpoints

[block:parameters]
{
  "data": {
    "h-0": "Operation",
    "h-1": "Required permissions",
    "0-0": "Create a subscription  \n`POST /v1/plans/{planId}/subscriptions`",
    "0-1": "Read customers  \nWrite customers",
    "1-0": "Get a subscription  \n`GET /v1/subscriptions/{subscriptionId}`",
    "1-1": "Read merchant  \nRead customers",
    "2-0": "Edit a subscription  \n`PUT /v1/subscriptions/{subscriptionId}`",
    "2-1": "Read customers  \nWrite customers",
    "3-0": "Cancel a subscription  \n`PUT /v1/subscriptions/{subscriptionId}`",
    "3-1": "Read customers  \nWrite customers  \nRead merchants"
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


# Set app permissions and integration type

1. Log in to the Developer Dashboard.
2. From the left navigation menu, click **Your Apps **> _App name_ > **App Settings**. The _App name_ - App Settings page allows you to view and configure settings and permissions that your app requires for accessing Clover merchant data.
3. Click **Requested Permissions**. The Edit Requested Permission page appears.
4. Select your app's read or write permissions for Ecommerce API, as required. For any selected permission, provide an in-line comment about how your app is using this information.
5. Click **Save**. Your selected permissions are displayed on the App Settings page.
6. Click **Ecommerce Settings**. The Edit Ecommerce Settings page appears.
7. Select your integration type. See [Integration types](doc:ecommerce-integration-types) for more information.
8. Click **Save**. Your selected integration type displays on the App Settings page.
