---
title: "Update a customer"
slug: "update-a-customer"
excerpt: ""
hidden: true
createdAt: "Wed Aug 03 2022 22:29:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
Use the [Update a customer](doc:update-a-customer) Ecomm endpoint to update an existing customer's profile, including a card associated with the customer.

## Request example

The following is a sample request when issuing a [create a customer](doc:create-a-customer) endpoint:

```curl
curl --request PUT \
     --url https://scl-sandbox.dev.clover.com/v1/customers/customerId \
     --header 'Accept: application/json' \
     --header 'Authorization: Bearer ab86a5e8-48f3-b3bd-8c45-d415e9867833' \
     --header 'Content-Type: application/json' \
     --data '{"ecomind":"ecom"}'
```

## Path Parameters

The following table describes the path parameters to use when updating a customer. Refer to [Response example](https://docs.clover.com/docs/update-a-customer#response-example) for a sample response when running this endpoint:

| Object       | Type   | Description                                   |
| :----------- | :----- | :-------------------------------------------- |
| `customerId` | string | Required. Indicates the customer's unique ID. |

## Request Parameters

The following table describes the request parameters to use when updating a customer.

| Object          | Type   | Description                                                                                                                                                               |
| :-------------- | :----- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `ecomind`       | string | Indicates who entered the card data used for a customer, which can be either a customer (`ecom`) or a merchant (`moto`).                                                  |
| `email`         | string | Required. Indicates the customer's email address.                                                                                                                         |
| `firstName`     | string | First name of the customer.                                                                                                                                               |
| `lastName`      | string | Last name (surname) of the customer.                                                                                                                                      |
| `name`          | string | Full name of the customer                                                                                                                                                 |
| `source`        | string | Required. The tokenized card (cToken) that is saved as a card-on-file, which is to be used for future transactions. Refer to [Using OAuth 2.0](doc:configuring-oauth-20). |
| `receipt_email` | string | Email address that receives the charge receipt.                                                                                                                           |
| `phone`         | string | Phone number of the customer                                                                                                                                              |
| `shipping`      | object | Indicates the shipping address. Refer to the [Shipping parameters](https://docs.clover.com/docs/update-a-customer#shipping-parameters).                                   |

## Shipping parameters

The following table describes the request parameters to use when updating a customer:

| Object            | Type   | Description                                                                                        |
| :---------------- | :----- | :------------------------------------------------------------------------------------------------- |
| `city`            | string | Indicate the city, district, suburb, town, or village.                                             |
| `country`         | string | Two-letter country code. Refer to the [ISO 3166 — Country Codes](https://www.iso.org/home.html).   |
| `line1`           | string | First line of the address, including the street address, PO box, or company name.                  |
| `line2`           | string | Second line of the address, including the apartment, suite, unit, or building number.              |
| `postal_code`     | string | ZIP or postal code.                                                                                |
| `state`           | string | The state, county, province, or region.                                                            |
| `carrier`         | string | Delivery service used to ship physical products, including DHL, FedEx, US Postal Service, etc.     |
| `name`            | string | Product recipient's name.                                                                          |
| `phone`           | string | Product recipient's phone, including extension.                                                    |
| `tracking_number` | string | Shipment number provided by the carrier. Use a comma-separated list for multiple tracking numbers. |

## Response example

The following is a sample response when issuing a [Create a customer](doc:create-a-customer).

```java
{
  "id": "T5YMNM7HEW91Y",
  "object": "customer",
  "created": 1659654474478,
  "currency": "USD",
  "email": "jdoe@gmail.com",
  "phone": "4085555555",
  "name": "John Data",
  "sources": {
    "object": "list",
    "data": [
      "XBFPVYKY9G6SG"
    ]
  },
  "shipping": {
    "name": "Joe Doe",
    "phone": "4085555555"
  }
}
```

## Responses

The following table describes the possible responses when running this endpoint:

[block:parameters]
{
  "data": {
    "h-0": "Message",
    "h-1": "Description",
    "h-2": "Variable",
    "h-3": "Description",
    "0-0": "`200`",
    "0-1": "string",
    "0-2": "charge",
    "0-3": "Returns the charge object with any captured value set to `true`.",
    "1-0": "`400`",
    "1-1": "string",
    "1-2": "code",
    "1-3": "Provides additional information about the error that you can use to provide user-friendly handling of the issue.",
    "2-0": "`400`",
    "2-1": "string",
    "2-2": "decline_code",
    "2-3": "Returned when a card issuer declines the transaction. This includes the reason for the decline, if specified by the card issuer.",
    "3-0": "`400`",
    "3-1": "string",
    "3-2": "doc_url",
    "3-3": "Returns a URL for more information about the reported error code.",
    "4-0": "`400`",
    "4-1": "string",
    "4-2": "message",
    "4-3": "Provides detailed information about the error code. For card-related errors, this information can be used to inform users.",
    "5-0": "`400`",
    "5-1": "string",
    "5-2": "param",
    "5-3": "If the error is related to a specific parameter, this value lists the parameter, so that you can inform users entering card information of a particular problem with their entry.",
    "6-0": "`400`",
    "6-1": "string",
    "6-2": "type",
    "6-3": "Returned error type:  \n- `api_connection_error`  \n- `api_error`  \n- `authentication_error`  \n- `card_error`  \n- `idempotency_error`  \n- `invalid_request_error`  \n- `rate_limit_error`"
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
