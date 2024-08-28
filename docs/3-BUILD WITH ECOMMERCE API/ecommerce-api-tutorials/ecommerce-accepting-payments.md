---
title: "Accept payments and tips"
slug: "ecommerce-accepting-payments"
excerpt: ""
hidden: false
metadata: 
  description: "This tutorial explains the API calls needed to complete a payment with the Clover Ecommerce API. It also provides steps for adding tips to transactions."
  image: 
    - "https://files.readme.io/cff00d0-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue Jan 21 2020 09:30:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Feb 02 2024 07:45:40 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Clover offers multiple ways to accept payments and tips for orders and charges. You can:

- Create an order or a charge to accept and complete a payment.
- Capture a payment after pre-authorization.
- Use multiple payment methods for a single charge.
- Use alternate merchant-specified tenders to complete a payment.

# Before you begin

Create a `source` token to use to create a charge and pay for order endpoints. This is a single-use token and can be created using the following endpoints:

- For the card token. See [create a card token](https://docs.clover.com/reference/create-card-token).
- For the ACH token. See [create an ACH token](https://docs.clover.com/reference/create-ach-token).

# Pay for a charge

If there is no order associated with a payment, send a POST request to the [create a charge](https://docs.clover.com/reference/createcharge) endpoint. Clover creates an order for the transaction. The payment is charged to a source—a credit or debit card tokenized with the hosted tokenizer or a single-use token for Automated Clearing House (ACH) payments. This is useful for [recurring subscriptions](https://docs.clover.com/docs/recurring-payments-and-subscriptions-apis), where you do not have to create orders for the recurring payment instances.

If there is no order associated with a payment, simply create a charge by sending a POST request to the [create a charge](ref:createcharge) endpoint. 

## Use idempotency keys

An idempotency key is a required value your app generates for Clover to recognize subsequent retries of the [create a charge](ref:createcharge) request without accidental double charges. If your app uses an idempotency key with a [create a charge](ref:createcharge) request, and a network connection error occurs. Use the same key to retry the request and prevent any duplicate charges. Your idempotency key must be a [version 4 UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier#Version_4_(random)) or equivalent. You can generate a key with the Python or Node `uuid` package. See [idempotent requests](https://docs.clover.com/docs/api-tutorials#idempotent-requests) to learn more about the idempotency key.

```python Python
import uuid
print uuid.uuid4()
```
```javascript JavaScript
import { v4 as uuidv4 } from 'uuid';
uuidv4();
```

## Create a charge and set up the tax amount

When you [create a charge](ref:createcharge), Clover creates an order for the transaction. 

### Required parameters

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "0-0": "`amount`",
    "0-1": "Charge amount. If the charge request includes tax (`tax_rate_uuid` or `tax_amount`), this value must be the sum of item prices, including the tax or tip. For example, if the item cost = $10 and the tax is $1, the amount is 1100 cents ($11).  \nFormat: Cents",
    "1-0": "`source`",
    "1-1": "Payment source to charge, such as `token` or `alternate_tender`.",
    "2-0": "`currency`",
    "2-1": "Three-letter [ISO 4217 currency code](https://www.iso.org/iso-4217-currency-codes.html).  \n**Note:** Merchants in the United States (US) can now accept customer payments in currency other than the US Dollar (USD).  \nFormat: Lowercase  \nLength: Maximum 3",
    "3-0": " `authorization`",
    "3-1": "Your OAuth-generated `access_token`. See [OAuth at Clover](https://docs.clover.com/docs/oauth-intro).",
    "4-0": "`idempotency-key`",
    "4-1": "Your generated `uuid4_key`."
  },
  "cols": 2,
  "rows": 5,
  "align": [
    "left",
    "left"
  ]
}
[/block]


You can set tax values for the charge amount in two ways:

| Parameter                     | Description                                                                                                                                                                                                                                                                                                                                                                                                     |
| :---------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `tax_rate_uuid` (recommended) | Tax rate universally unique identifier (UUID). Use the [get all tax rates endpoint](https://docs.clover.com/reference/taxrategettaxrates) to retrieve merchant tax UUID information. The tax is not automatically added to the total amount. Your app must ensure the Amount property is the total final amount to charge the customer. Taxes are set under **Setup > Taxes & Fees** on the Merchant Dashboard. |
| `tax_amount`                  | Amount paid in taxes. This value is not automatically added to the total amount. Your app must ensure the Amount property is the total final amount to charge the customer.                                                                                                                                                                                                                                     |

### Response

- Unique `id` (charge ID) is generated if the payment is successful using the tokenized card.
- Payment status value indicates whether the payment was successful. 
- Object `additional_charges` provides details of the surcharge for the payment.

```curl Request
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'idempotency-key {uuid4_key}' \
  --header 'content-type: application/json' \
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"amount":1100,
  "currency":"usd",
  "tax_rate_uuid":"{tax_uuid}",
  "Source":"{token}"}'
```
```javascript Response
{
  "id" : "2G1RQC0VTH7WY",
  "amount" : 1100,
  "tax_amount" : 100,
  "amount_refunded" : 0,
  "currency" : "usd",
  "created" : 1623551758243,
  "captured" : true,
  "ref_num" : "116400500490",
  "auth_code" : "OK4447",
  "outcome" : {
    "network_status" : "approved_by_network",
    "type" : "authorized"
  },
  "paid" : true,
  ...
  card source details
  ...
  }
}
```

# Use pre-authorization and capture charge

When you create a payment, you can place a hold on an eligible payment method to reserve funds that you can capture later. This process is called pre-authorization.

The pre-authorization validity depends on the transaction and card type. Hence, you need to capture the funds before the authorization expires. For example, car rental companies authorize the initial cost of the service and capture a different amount where additional charges are required if the rental car is damaged.

1. Send a POST request to the [create a charge](https://docs.clover.com/reference/createcharge) endpoint. 
2. Required. Set the `capture` value to **false**. See [create pre-authorization](https://docs.clover.com/docs/create-pre-authorization).
3. When the charge is ready for capture, send a POST request to the [capture a charge](https://docs.clover.com/reference/capturecharge) endpoint.

```curl Request
curl --request POST \
  --url https://scl-sandbox.dev.clover.com/v1/charges/{chargeId}/capture
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'idempotency-key {uuid4_key}' \
  --header 'content-type: application/json' \
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"amount":1100,
  "currency":"usd",
  "tax_rate_uuid":"{tax_uuid}",
  "capture": "false",
  "Source":"{token}"}'
```
```javascript Response
{
  "id" : "2G1RQC0VTH7WY",
  "amount" : 1100,
  "payment_method_details": "card",
  "tax_amount" : 100,
  "currency" : "usd",
  "created" : 1623551758243,
  "captured" : "false",
  "ref_num" : "116400500490",
  "auth_code" : "OK4447",
  "order": "3TQ8KJXBQMJ7W",
  "outcome" : {
    "network_status" : "approved_by_network",
    "type" : "authorized"
  },
  "paid" : true,
  ...
  card source details
  ...
  }
}
```

# Create order and pay

Clover has multiple APIs for creating orders. We recommend using our [Atomic Orders API](https://docs.clover.com/docs/working-with-orders) to create orders in most situations. However, you can also create an order using the [create an order](https://docs.clover.com/reference/postorders) endpoint when you have a single-use token of tokenized card token or an ACH.

- **Orders and checkouts-**The [/atomic_order/orders](https://docs.clover.com/reference/ordercreateatomicorder) and [/atomic_order/checkouts](https://docs.clover.com/reference/ordercheckoutatomicorder) endpoints provide our most full-featured API for creating an order in a single request with line items, modifiers, discounts, and so on.
- **Pay for orders-**Use the Ecommerce API [pay for an order](https://docs.clover.com/reference/postordersidpay) endpoint to pay for orders created with any of our Order APIs.

## Create an order

To create an order using your tokenized card or an ACH single-use token, send a POST request to the [create an order](https://docs.clover.com/reference/postorders) endpoint.

### Required parameters

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "0-0": "`currency`",
    "0-1": "Three-letter [ISO 4217 currency code](https://www.iso.org/iso-4217-currency-codes.html).  \nFormat: Lowercase  \nLength: Maximum 3",
    "1-0": "`email`",
    "1-1": "Email address of the customer placing the order.",
    "2-0": "`amount`",
    "2-1": "Amount of an item in the inventory.",
    "3-0": "`address`",
    "3-1": "Shipping address for the order. Required, if the stock keeping unit (SKU) of an item in the order has a `shippable` value of **true**.",
    "4-0": "`name`",
    "4-1": "Name of the customer.",
    "5-0": "`authorization`",
    "5-1": "Your OAuth-generated `access_token`."
  },
  "cols": 2,
  "rows": 6,
  "align": [
    "left",
    "left"
  ]
}
[/block]


### Response

- Unique `id` (order ID) is generated for the created order.
- Order `status` value is set to **created**.

### Sample

```curl Request
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/orders' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'content-type: application/json' \
  --data '{"currency":"usd",
  "customer":"{customer_uuid}",
  "email":"john.doe@customer.com",
  "items":[{"amount":1800,
  "currency":"usd",
  "description":"Test item #1",
  "quantity":1,"type":"sku"
  "tax_rates":[{"name":"Sale","tax_rate_uuid":"{tax_uuid}"}]}],
  "shipping":{"address":{city":"Sunnyvale",
  "country":"US",
  "line1":"415 N Mathilda Ave",
  "postal_code":"94085",
  "state":"California"},"name":"John Doe"}}'
```
```javascript Response
{
  "id" : "96JN5MP2QJ47C", // order ID of the created order
  "object" : "order",
  "amount" : 1980,
  "currency" : "usd",
  "created" : 1623566507000,
  "customer" : "BJA5CF0M0C4ST",
  "email" : "john.doe@customer.com",
  "items" : [ {
    "type" : "sku",
    "quantity" : 1,
    "amount" : 1800,
    "currency" : "usd",
    "description" : "Test item #1",
    "tax_rates" : [ {
      "name" : "Sale",
      "tax_rate_uuid" : "77FAGR71YYD5M"
    } ]
  }, {
    "type" : "tax",
    "amount" : 180,
    "description" : "Sales Tax"
  } ],
  ...
  shipping information
  ...
  },
  "status" : "created" // order created
}

```

In this example, the item-level tax is set using the `tax_rates` object. Using [ create an order](https://docs.clover.com/reference/postorders), you can set the tax value for each item in three ways.

[block:parameters]
{
  "data": {
    "h-0": "Tax object",
    "h-1": "Description",
    "0-0": "`TAX AS UUID `(recommended)",
    "0-1": "Tax rate object defining an item-level tax with a universally unique identifier (UUID).  \n  \nThe recommended approach to set the tax based on merchant tax information is to use the`TAX AS UUID`. Taxes are set under **Setup > Taxes & Fees** on the Merchant Dashboard. You can retrieve this merchant tax information with the`/v3/merchants/{mId}/tax_rates`.",
    "1-0": "`TAX AS PERCENTAGE`",
    "1-1": "Tax rate object defining an item-level tax as a percentage (%).  \nTo set a tax percentage, set the rate as an integer. For example, use 1000000 for a 10% tax.",
    "2-0": "`TAX AS AMOUNT`",
    "2-1": "Tax rate object defining a flat item-level tax amount.  \nTo set a flat fee, use the`tax_amount`.  \nFormat: Cents"
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]


> 📘 NOTE
> 
> If you have already built applications using `/v3` Clover endpoints (such as Inventory (`/v3/merchants/{mId}/items`) or Orders (`/v3/merchants/{mId}/orders`), it is recommended that you continue using those endpoints. 
> 
> The [create an order](https://docs.clover.com/reference/postorders) endpoint is meant for streamlined app creation and does not include all the same features as `/v3` Clover endpoints. Inventory stock counts are not [automatically adjusted](https://www.clover.com/help/apply-inventory-setup-settings/?device=ZKF1GcCo6sus0GkgWw6ku) with the [create an order](https://docs.clover.com/reference/postorders) endpoint.

## Pay for the order

To pay for your created order, send a POST request to the [pay for an order](https://docs.clover.com/reference/postordersidpay) endpoint.

### Required Parameters

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "0-0": "`orderId`",
    "0-1": "Universally unique identifier (UUID) of the order.",
    "1-0": "`customer`",
    "1-1": "Universally unique identifier (UUID) of the customer being charged for the order. The customer indicated here is charged instead of the customer associated with the order creation. See [Create a customer](https://docs.clover.com/reference/createcustomer).  \n**Important:** Either a payment `source `or `customer` must be associated with an order for payment. If a customer is not attached to the order, then the source in this field is charged for the order.",
    "2-0": "`authorization`",
    "2-1": "Your OAuth-generated access_token."
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]


### Response

- Unique `id` (charge ID) is generated, if the payment is successful using the tokenized card.
- Order status value is set to paid.
- Object `additional_charges` object provides details of the surcharge for the payment, if the merchant is set up for credit surcharging.

### Sample

```curl
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/orders/{orderId}/pay' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'content-type: application/json' \
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"ecomind":"ecom","customer":"{customerId}"}'
```
```json Order response
{
  "id": "M8W63PVQ6BDSM",
  "object": "order",
  "amount": 212,
  "amount_paid": 212,
  "currency": "USD",
  "charge": "TJGQQ90THNY1J",
  "warning_message": "Subsequent credential on file pay request sent for without Initial credential on file pay request.",
  "created": 1705383316000,
  "customer": "GWMCWCFH5Y4SR",
  "ref_num": "1949774325",
  "auth_code": "876652",
  "items": [
    {
      "quantity": 1,
      "amount": 212
    }
  ],
  "source": {
    "brand": "DISCOVER",
    "exp_month": "12",
    "exp_year": "2025",
    "first6": "601136",
    "last4": "6668"
  },
  "status": "paid",
  "status_transitions": {
    "paid": 1705383427235
  },
  "ecomind": "ecom"
}
```

# Submit multiple payments for an order

In some cases, customers use multiple payment methods for an order. For example, a buyer purchases a sweater for $14, and the gift card balance is $10. In this case, the gift card payment is authorized for the full card balance, and a credit card covers the remaining purchase amount of $4. You need to submit multiple requests to the [pay for an order](https://docs.clover.com/reference/postordersidpay) endpoint and enter the `amount` for each payment.

## Example

Step 1: Create an order.

```json Order response
{
  "id": "PND09C6WNW2Y3",
  "object": "order",
  "amount": 1400,
  "currency": "usd",
  "created": 1610131014000,
  "customer": "2S6XE98MP58YE",
  "email": "customer@example.com",
  "items": [
    {
    "type" : "sku",
    "quantity" : 1,
    "amount" : 1400,
    "currency" : "usd",
    "description" : "Item"
 		}
  ],
  "shipping": {
    ...
  },
  "status": "created"
}
```

Step 2: Send a POST request to [pay for an order](https://docs.clover.com/reference/postordersidpay) endpoint.

- Use the `gift card` as the `source`.
- Set the `amount` as `1000`.

```json First payment request ($10)
{
  "source": "{giftCardToken}"
  "amount": 1000
}
```

In the response, the `amount_paid` field shows that $10 has been applied to the $14 order.

```json First payment response
{
  "id": "0DHG92XRFFXKP",
  "object": "order",
  "amount": 1400,
  "amount_paid": 1000,
  "currency": "USD",
  "charge": "69Q0S9BK2ZTNA",
  ...
}
```

Step 2: Send another POST request to the [pay for an order](https://docs.clover.com/reference/postordersidpay).

- Use the credit card as the `source`.
- Set the `amount` as `400`.

```json Second payment request ($4)
{
  "source": "{creditCardToken}"
  "amount": 400
}
```

In the response to the second charge, the `past_charges` shows the first payment made with the gift card. The `amount_paid` is now `1400` (equal to the total order `amount`).

```json Second payment response
{
  "id": "0DHG92XRFFXKP",
  "object": "order",
  "amount": 1400,
  "amount_paid": 1400,
  "currency": "USD",
  "charge": "69Q0S9BK2ZTNA",
  ...
  "past_charges": [
    {
      "id": "EVW3V8TDJQT0C",
      "amount": 1000,
      "currency": "usd",
      ...
    }
  ],
  ...
}
```

# Add tips to charges and orders

You can add the tip before paying for the charge or an order. To help merchants avoid chargebacks, tips are not adjustable and can only be included in the initial request. For example, you cannot add a tip after an order receipt is printed.  
To add a tip amount, send a POST request to [pay for an order ](https://docs.clover.com/reference/postordersidpay)or [create a charge](https://docs.clover.com/reference/createcharge) endpoint, as applicable. Clover recommends you submit the charge or order amount and tip separately. Example:

```curl
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'idempotency-key {uuid4_key}' \
  --header 'content-type: application/json' \
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"amount":1800,
  "tip_amount":200,
  "currency":"usd",
  "source":"{token}"}'
```

## Order calculations with tips

Always submit the charge or order amount and tip separately. In the above example, for a subtotal of $18 and a tip of $2:

|               | Subtotal         | Tip                 |
| :------------ | :--------------- | :------------------ |
| **Correct**   | `"amount": 1800` | `"tip_amount": 200` |
| **Incorrect** | `"amount": 2000` | `"tip_amount": 200` |

# Set the transaction type indicator

When your app submits a charge, pays for an order, or creates a customer with a card on file, the `ecomind` parameter can be set to one of two values to indicate who initiated the payment. If no value is set, the default is `ecom`.

- `ecom`—a payment where the customer enters their card details for a single transaction
- `moto`—a payment where the merchant enters the customer's card details received over the phone or by mail

## `ecom` payment

In this example, the customer uses an iframe-based app to submit a charge request for an online `ecom` payment. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c956270-ecom2.png",
        "ecom2.png",
        1630
      ],
      "align": "center",
      "sizing": "80",
      "border": true,
      "caption": "ecom payment"
    }
  ]
}
[/block]


## `moto` payment

The customer can also make their purchase over the phone and provide their card details to the merchant. The indicator should be set as `moto` because the merchant is entering the card information on the customer's behalf.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fcc7fc5-moto2.png",
        "moto2.png",
        1630
      ],
      "align": "center",
      "sizing": "80",
      "border": true,
      "caption": "moto payment"
    }
  ]
}
[/block]


# Pay with an alternate tender

If the merchant using your app accepts alternate, non-card tenders such as cash or check, you can submit charge or order payment requests using these tender types.

## Get a merchant's available tenders

You can use the [get a single merchant](ref:merchantgetmerchant) endpoint to see the custom tenders a merchant accepts. To get the data, expand the `tenders` as shown in the following example.

### Required Parameters

```curl
curl --request GET \
  --url 'https://sandbox.dev.clover.com/v3/merchants/mId?expand=tenders' \
  --header 'Accept: application/json'
```

In the response, examine the object of the `tender` and note the following important information for each element:

[block:parameters]
{
  "data": {
    "h-0": "Key",
    "h-1": "Description",
    "0-0": "`tenders.elements.id`",
    "0-1": "Universally unique identifier (UUID) of the tender",
    "1-0": "`tenders.elements.labelKey`",
    "1-1": "Internal name of the tender.  \nValues:  \n- Clover system tenders start with com.clover.tender  \n- [Custom tenders](https://docs.clover.com/docs/custom-tenders)",
    "2-0": "`tenders.elements.label`",
    "2-1": "Name of the tender.",
    "3-0": "`tenders.elements.enabled`",
    "3-1": "If `true`, the tender is currently accepted as payment for transactions."
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Charge a customer using an alternate tender

Alternate tenders require different values in the request body but use the same [ create a charge](https://docs.clover.com/reference/createcharge) or [pay for an order](https://docs.clover.com/reference/postordersidpay) endpoint. 

Note the following differences:

- Required. Use an `alternate_tender` string for the `source` value.
- Required.  A tender object that identifies the tender with a  `label_key`, `label`, or `id`. The label_key is an enumerated field with two possible values for  Clover system tenders: `com.clover.tender.cash` and `com.clover.tender.check`.
- Set a `label` or `id` for any custom tenders that the merchant has enabled.

### Charge a customer using cash

For an in-person cash payment, set the `label_key` value to `com.clover.tender.cash`.

```curl Alternate tender for cash payment
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  --data '{"tender":{"label_key":"com.clover.tender.cash"},"source":"alternate_tender","currency":"usd","amount":1833}'
```

### Charge a customer using a check

For a check payment as a non-card tender, set the `label_key` value to `com.clover.tender.check`.

```curl Alternate tender for check payment
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  --data '{"tender":{"label_key":"com.clover.tender.check"},"source":"alternate_tender","currency":"usd","amount":6520}'
```

### Charge a customer using a custom tender

For payment with tender, enter the `tender id `or `label`.

```curl Alternate tender by id
curl --request POST \
  --url' https://scl-sandbox.dev.clover.com/v1/orders/{orderId}/pay' \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"tender":{"id":"3ER64K904R7R8"},"source":"alternate_tender"}'
```
```curl Alternate tender by label
curl --request POST \
  --url https://scl-sandbox.dev.clover.com/v1/orders/{orderId}/pay \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  --data '{"tender":{"label":"Gift card"},"source":"alternate_tender"}'
```
