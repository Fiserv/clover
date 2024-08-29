---
title: "DS - 2993 - Saving a card for future transactions"
slug: "ds-2993-saving-a-card-for-future-transactions"
excerpt: ""
hidden: true
createdAt: "Wed Mar 01 2023 07:29:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
After [generating a card token](doc:ecommerce-generating-a-card-token), you can use the `source` token to save cards-on-file. With card-on-file payments, customers authorize merchants to store their payment details and also to use those details to complete payments for future transactions.

> 🚧 IMPORTANT
> 
> Clover requires that all apps saving cards on file get the customer's consent before updating a customer profile with card information.

Clover provides several [sandbox test cards](doc:test-card-numbers) that can be used when building your app. 

# Saving a card for a new customer

To save a card for a new customer, create a customer by sending a `POST` request to the `/v1/customers` endpoint.

> 📘 NOTE
> 
> When you save a card on file using `/v1/customers`, Clover sets the card `source` token as a multi-pay token for the customer.

In the following example, set the `source` token value and relevant information about the customer. Set the `authorization: Bearer` as your OAuth-generated `access_token`. See the API reference for more information about other values you can set.

```curl
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/customers' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'content-type: application/json' \
  --data '{"email":"john.doe@customer.com","firstName":"John","lastName":"Doe",
  "source":"{token}","shipping":{"address":{"city":"Sunnyvale","country":"US",
  "line1":"415 N Mathilda Ave","postal_code":"94085","state":"CA"}}}'
```

> 📘 NOTE
> 
> Email address is a required field. This field helps customers to be notified that their card data has been saved to their profile.

In response, a unique `id` (customer ID) is generated for the created customer. You can use this customer `id` as the `source` value to submit payments with a saved customer card.

# Saving a card for an existing customer

To save a card for an existing customer, update the customer record by sending a `PUT` request to the `/v1/customers/{customerId}` endpoint using the `source` token value.

In the following example, set the `customerId` and `source` token values. Set the `authorization: Bearer` as your OAuth-generated `access_token`. See the API reference for more information about other values you can set.

```curl
curl --request PUT \
  --url 'https://scl-sandbox.dev.clover.com/v1/customers/{customerId}' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'content-type: application/json' \
  --data '{"source":"{token}"}'
```

# Subsequent payments with saved cards

To make a payment and then subsequent payments with a saved customer card, you can use either the customer `id` or the multi-pay card token as the `source` value in your payment request.

## Using customer ID

To construct a charge request, set the `amount` (in cents), `currency`, and `source` as the customer `id`.

```curl Subsequent charge with a customer ID
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'idempotency-key {uuid4_key}' \
  --header 'content-type: application/json' \
  --data '{"amount":2300,
  "currency":"usd",
  "source":"{customer_id}"}'
```

> 📘 NOTE
> 
> If your use case requires you to save one card per customer, set the `source` as the customer `id` in any subsequent payments for that customer. If you are saving multiple cards per customer, use the multi-pay token for that customer in subsequent payments.

## Using a multi-pay card token

When you save a card on file using `/v1/customers`, Clover sets the card `source` token as a multi-pay token for the customer. If you set the `source` value as this multi-pay token for the customer, you must also include the required `stored_credentials` values in the payment request:

[block:parameters]
{
  "data": {
    "h-0": "Object",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "`sequence`",
    "0-1": "string",
    "0-2": "Indicates whether the transaction is the FIRST or SUBSEQUENT for the a payment card. Note: Master Card  supports both FIRST and SUBSEQUENT type transactions.",
    "1-0": "`is_scheduled`",
    "1-1": "boolean",
    "1-2": "Indicates if the transaction is scheduled or part of an installment.  \nValues:  \n- True - Transaction is scheduled.  \n- False - Transaction is part of an installment. (Installments are only available in the US).",
    "2-0": "`initiator`",
    "2-1": "string",
    "2-2": "Indicates if the transaction is scheduled or part of an installment.  \nValues:  \n- True - Transaction is scheduled.  \n- False - Transaction is part of an installment. (Installments are only available in the US).",
    "3-0": "`installment_info`",
    "3-1": "string",
    "3-2": "Installment information for the transaction.",
    "4-0": "`bill_pay_indicator`",
    "4-1": "string",
    "4-2": "Indicates if the transaction is a recurring or installment payment.  \nValues:  \n- Installment  \n- Recurring - For Canadian merchants, the value must be  \n\"Recurring.\"",
    "5-0": "`invoice_number`",
    "5-1": "string",
    "5-2": "Invoice number of the installment or recurring transaction.",
    "6-0": "`description`",
    "6-1": "string",
    "6-2": "Associated with the `installment_info` parameter).  \n  \nDescription of the installment or recurring transaction."
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
  --data '{"amount":1800,
  "currency":"usd",
  "source":"{multi_pay_token}",
  "stored_credentials":{
  "sequence": "SUBSEQUENT",
  "is_scheduled": false,
  "initiator": "CARDHOLDER"}}'
```

See the [API reference](https://docs.clover.com/reference/createcharge) for more information about other `POST /v1/charges` values you can set.

```curl Order payment with a multi-pay card token for the customer
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/orders/{orderId}/pay' \
  --header 'accept: application/json'
  --header 'authorization: Bearer {access_token}'
  --header 'content-type: application/json'
  --data '{"source":"{multi_pay_token}",
  "email":"customer@example.com",
  "stored_credentials":{
  "sequence": "SUBSEQUENT",
  "is_scheduled": false,
  "initiator": "CARDHOLDER"}}'
```

See the [API reference](https://docs.clover.com/reference/postordersidpay) for more information about other `POST /v1/orders/{orderId}/pay` values you can set.
