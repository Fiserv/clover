---
title: "Save a card for future transactions"
slug: "ecommerce-saving-card"
excerpt: ""
hidden: false
metadata: 
  description: "This tutorial explains how an app can save cards on file for future transactions and associate that information with a customer account."
  image: 
    - "https://files.readme.io/af79df9-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue Jan 21 2020 09:30:38 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 08:24:15 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=\"Learn how to create a card-on-file (COF) customer record for e-commerce transactions.\">\n\n<!--DS-4708-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# What is card on file (COF)?

Card on file (COF) transactions are payments in which the cardholders have authorized merchants to store their credit or debit card information to use for future purchases or recurring payments. You can use [sandbox test cards](https://docs.clover.com/docs/test-card-numbers) to build and test the COF feature. A COF payment requires that the Clover merchants have multi-pay tokens enabled in their gateway settings. After you generate a card token, use the `source` token to save COF.

> 🚧 IMPORTANT
> 
> Clover requires getting the customer’s consent before you save card-on-file in the customer’s profile.

## Prerequisites

Before you create a customer, complete the following: 

1. [Create a sandbox account](doc:create-a-sandbox-account). 
2. [Create an app](doc:creating-an-app).
3. [Install your app to your test merchant](doc:installing-your-app-to-your-test-merchant).

# Save a card for a new customer

1. Send a POST request to the `/v1/customers` endpoint to create a card-on-file customer.
2. Enter the values in the following required parameters in the request body:
   1. `email`
   2. `source`

## Request example

The following is a sample request when issuing a [Create a card on file customer](doc:create-a-customer) endpoint:

```curl
curl --request POST \
     --url https://scl-sandbox.dev.clover.com/v1/customers \
     --header 'Accept: application/json' \
     --header 'Authorization: Bearer ab86a5e8-48f3-b3bd-8c45-d415e9867833' \
     --header 'Content-Type: application/json' \
     --data '{"ecomind":"ecom"}'
```

## Request parameters

The following table describes the request parameters to use when creating a card-on-file customer:

| Parameter   | Type   | Description                                                                                                     |
| :---------- | :----- | :-------------------------------------------------------------------------------------------------------------- |
| `ecomind`   | string | Indicates who entered the card data used for a charge - customer (`ecom`) or merchant (`moto`). Default: `ecom` |
| `email`     | string | Required. Customer's email address.                                                                             |
| `firstName` | string | Customer's first name.                                                                                          |
| `lastName`  | string | Customer's last name.                                                                                           |
| `name`      | string | Customer's full name.                                                                                           |
| `source`    | string | Payment source to charge, such as a **card**, **gift card**, or **ACH**.                                        |
| `phone`     | string | Customer's phone number.                                                                                        |
| `shipping`  | object | Shipping information of the customer.                                                                           |

## Response parameters

The following is a sample response when issuing a [Create a card on file customer](doc:create-a-customer) endpoint.

```java
{
  "id": "SSHHCDEXTF550",
  "object": "customer",
  "created": 1659650347317,
  "currency": "USD",
  "email": "jdoe@gmail.com",
  "phone": "4085551858",
  "name": "Joe Doe",
  "sources": {
    "object": "list",
    "data": [
      "ND2EFTHF8HM34"
    ]
  },
  "shipping": {
    "name": "Joe Doe",
    "phone": "4085551858"
  }
}
```

In response, a unique `id` (customer ID) is generated for the created customer. You can use this customer `id` as the `source` value to submit payments with a saved customer card or card-on-file. See [Use customer ID](https://docs.clover.com/docs/ecommerce-saving-card#use-customer-id).

***

# Save a new card for an existing customer

To save a new card for an existing customer, you need to complete two steps:

1. Revoke the existing card.
2. Add the new card information.
3. Send a DELETE request to `/v1/customers/{customerId}sources/{cardId}`.

```curl
curl --request DELETE \
--url 'https://scl-sandbox.dev.clover.com/v1/customers/{customerId}/sources/{cardId}' \
--header 'accept: application/json' \
--header 'authorization: Bearer {accessToken}'\
```

4. After the existing card is revoked, send  a `PUT` request to the `/v1/customers/{customerId} `endpoint to add a new card to the existing customer record:
5. Complete or review the information in the required fields:

- `source` token value
- `customerId`
- `email address`—Used to notify the customers that their card data is saved to their profile. See the [API reference](https://docs.clover.com/reference/updatecustomer) for more information about other values you can set.

6. Set the `authorization: Bearer` as your OAuth-generated `access_token`.
7. Retokenize the card using your OAuth-generated `access_token`. See [Generate a card token](https://docs.clover.com/docs/ecommerce-generating-a-card-token).

```curl
curl --request PUT \
  --url 'https://scl-sandbox.dev.clover.com/v1/customers/{customerId}' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'content-type: application/json' \
  --data '{"source":"{token}"}'
```

***

# Make subsequent payments with saved cards

To make a payment and then subsequent payments with a saved customer card, you can use either the customer `id` or the multi-pay card token as the `source` value in your payment request.

## Use customer ID

To create a charge request, set the `amount` (in cents), `currency`, and `source` as the customer `id`.

```curl Subsequent charge with a customer ID
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'idempotency-key {uuid4_key}' \
  --header 'content-type: application/json' \
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"amount":2300,
  				"currency":"usd",
          "Source":"{customer_id}"}'
```

> 📘 NOTE
> 
> If your use case requires you to save one card per customer, set the `source` as the customer `id` in any subsequent payments for that customer. If you are saving multiple cards per customer, use the multi-pay token for that customer in subsequent payments.

## Use a multi-pay card token

When you save a card on file using `/v1/customers`, Clover sets the card `source` token as a multi-pay token for the customer. If you set the `source` value as this multi-pay token for the customer, you must also include the required `stored_credentials` values in the payment request:

[block:parameters]
{
  "data": {
    "h-0": "Object",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "`sequence`",
    "0-1": "string",
    "0-2": "Indicates the sequence of the transaction for the same payment card.  \nValues:  \n  \n- First  \n- Subsequent",
    "1-0": "`is_scheduled`",
    "1-1": "boolean",
    "1-2": "Indicates whether the transaction is scheduled or part of an installment.  \nValues:  \n  \n- True - Transaction is scheduled.  \n- False - Transaction is part of an installment.  \n  Installments are only available in the US.",
    "2-0": "`initiator`",
    "2-1": "string",
    "2-2": "Indicates whether the transaction is initiated by the merchant or with cardholder consent.  \nValues:  \n  \n- Merchant  \n- Cardholer",
    "3-0": "`installment_info`",
    "3-1": "string",
    "3-2": "Installment information for the transaction.",
    "4-0": "`bill_pay_indicator`",
    "4-1": "string",
    "4-2": "Indicates whether the transaction is a recurring or installment payment.  \nValues:  \n  \n- Installment  \n- Recurring - For Canadian merchants, the value must be \"Recurring\"",
    "5-0": "`invoice_number`",
    "5-1": "string",
    "5-2": "`Invoice number` of the installment or recurring transaction.",
    "6-0": "`description`",
    "6-1": "string",
    "6-2": "Description of the` installment_info` or recurring transaction."
  },
  "cols": 3,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Multi-pay card token example

```curl Subsequent charge with a multi-pay card token for the customer
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'idempotency-key {uuid4_key}' \
  --header 'content-type: application/json' \
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"amount":1800,
  "currency":"usd",
  "source":"{multi_pay_token}",
  "stored_credentials":{
  "sequence": "SUBSEQUENT",
  "is_scheduled": false,
  "initiator": "CARDHOLDER"}}'
```

See the [Create a charge](https://docs.clover.com/reference/createcharge) for more information about other`POST /v1/charges` values you can set.

```curl Order payment with a multi-pay card token for the customer
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/orders/{orderId}/pay' \
  --header 'accept: application/json'
  --header 'authorization: Bearer {access_token}'
  --header 'content-type: application/json'
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"source":"{multi_pay_token}",
  "email":"customer@example.com",
  "stored_credentials":{
  "sequence": "SUBSEQUENT",
  "is_scheduled": false,
  "initiator": "CARDHOLDER"}}'
```

See the [Create an order](https://docs.clover.com/reference/postorders) for more information about other`POST /v1/orders/{orderId}/pay` values you can set.

## Possible responses

The following table describes the possible responses when running the create a card-on-file customer endpoint:

[block:parameters]
{
  "data": {
    "h-0": "Message",
    "h-1": "Description",
    "h-2": "Variable",
    "h-3": "Description",
    "0-0": "`200 Successful response`",
    "0-1": "string",
    "0-2": "",
    "0-3": "Successful response. Returns the customer object.",
    "1-0": "`400 Bad Request`",
    "1-1": "string",
    "1-2": "code",
    "1-3": "Additional information about the error to help users identify the issue.",
    "2-0": "`400 Bad Request`",
    "2-1": "string",
    "2-2": "decline_code",
    "2-3": "Returned when a card issuer declines the transaction. This includes the reason for the decline if specified by the card issuer.",
    "3-0": "`400 Bad Request`",
    "3-1": "string",
    "3-2": "doc_url",
    "3-3": "URL (link) for more information about the reported error code.",
    "4-0": "`400 Bad Request`",
    "4-1": "string",
    "4-2": "message",
    "4-3": "Detailed information about the error code. For card-related errors, this can provide more information to users.",
    "5-0": "`400 Bad Request`",
    "5-1": "string",
    "5-2": "param",
    "5-3": "If the error is related to a specific parameter, this value lists the parameter. You can use this to inform users entering card information of a specific problem with their entry.",
    "6-0": "`400 Bad Request`",
    "6-1": "string",
    "6-2": "type",
    "6-3": "Returned error type:  \n  \n- `api_connection_error`  \n- `api_error`  \n- `authentication_error`  \n- `card_error`  \n- `idempotency_error`  \n- `invalid_request_error`  \n- `rate_limit_error`"
  },
  "cols": 4,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]
