---
title: "Manage transaction data (REST API)"
slug: "working-with-transaction-data-rest"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to manage transaction data with Clover REST API. Retrieve detailed information and understand surcharges for use in your app."
  image: 
    - "https://files.readme.io/5b14ceb-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Mon Aug 31 2020 14:56:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Aug 06 2024 10:29:17 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--DS-3009; Region pill icon added to topic on 3.22.2023-->\n<!-- Mar 25 2024: replaced pill icon html with reusable pill icon set -cd-->\n<!--DS-6441: Fixed bug re wrong domains used in samples: apisandbox.dev.clover.com -cd -->\n<!--DS-6387: Added reusable content block for credit card surcharges - Aneesha -->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

<meta name=" description" content="Learn how to manage transaction data with Clover REST API. Retrieve detailed information and understand surcharges for use in your app.">

# Retrieve transaction information

Clover REST API enables access to detailed transaction data for utilization and display in your application. Your application must possess [read payment permission](https://docs.clover.com/docs/permissions) to access this data. If your app enables the merchant to update payment or authorization data, it must also request permission to write payments.

# Understand credit card surcharge

A credit card surcharge is a percentage of the post-tax order total collected to partially or fully cover the merchant's costs associated with processing credit card payments. Some merchants are configured to add a surcharge to eligible credit BIN credit card transactions they process. Surcharges are only applied when the customer pays with an eligible credit BIN credit card; they are not added to debit, cash, or other forms of payment. Surcharge rules are set by the card networks.

Clover onboards merchants for credit card surcharging in the following countries:

- Canada, excluding Quebec
- United States, excluding states with legal restrictions or prohibitions

Canada uses a flat 2.40% credit card surcharge rate, while in the US, the surcharge can vary by merchant, with most US merchants having a surcharge of 3.00%.

If you display transaction data in your app, you must include data from a few fields. 

## Check if a merchant is set up for surcharging

To check if a merchant is set up for surcharging

1. Send a GET request to the `/v3/merchants/{mId}/ecomm_payment_configs` endpoint. 
2. In the response, check that the `surcharging.supported` value is `true`. You can also see the merchant's credit card surcharge rate in the `rate` field.

```curl
curl --request GET \
  --url 'https://apisandbox.dev.clover.com/v3/merchants/{merchantUUID}/ecomm_payment_configs' \
  --header 'accept: application/json'
```
```json
{
  "surcharging": {
    "supported": true,
    "rate": 0.035
  }
  ...
}
```

## View surcharge for a paid transaction

To view the surcharge data for a transaction, add the `expand` query parameter with the value  `additionalCharges` as shown in the following example.

### Request

```curl
curl --request GET \
  --url 'https://apisandbox.dev.clover.com/v3/merchants/{merchantUUID}/payments/{paymentUUID}?expand=additionalCharges' \
  --header 'accept: application/json'
```
```json
{
  "id": "RCFSJ33GPYM3D",
  "amount": 3500,
  ...
  "additionalCharges": {
    "elements": [
      {
        "id": "AGPT72N3N5TDM",
        "amount": 122,
        "rate": 35000,
        "type": "CREDIT_SURCHARGE",
        "payment": {
          "id": "RCFSJ33GPYM3D"
        }
      }
    ]
  }
}
```

### Response

The response includes an `additionalCharges` object with the following information:

[block:parameters]
{
  "data": {
    "h-0": "Response parameter",
    "h-1": "Description",
    "0-0": "`amount`",
    "0-1": "Amount in cents paid as a surcharge on the credit card transaction.",
    "1-0": "`rate`",
    "1-1": "Percentage of the total used to calculate the `amount` multiplied by 10000.  \nExample: A 3.5% `rate` displays as `35000`.",
    "2-0": "`type`",
    "2-1": "Additional charge type processed for the transaction.  \nValues:  \n  \n- `CREDIT_SURCHARGE`—Percentage fee added to a credit card transaction from an eligible credit BIN to cover the cost of processing.  \n- `INTERAC_V2`—Fixed amount added to Interac debit transactions.",
    "3-0": "`payment`",
    "3-1": "Universally unique identifier (UUID) of the associated payment."
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


Total amount paid by the customer is the sum of the payment `amount` and `additionalCharges.amount`. In the example, the customer was charged $36.22, which is the $35.00 `amount` plus a 3.5% surcharge of $1.22.

## View surcharge for a refund transaction

The paid transaction calculation is applicable for refund data. You can retrieve the updated order and surcharge for a partial refund to display in your app.

```curl
curl --request GET \
  --url 'https://apisandbox.dev.clover.com/v3/merchants/{merchantUUID}/refunds/{refundUUID}?expand=additionalCharges' \
  --header 'accept: application/json'
```
```json
{
  "id": "JRWNWS4Y7SSTP",
  "orderRef": {
    "id": "KTRPNSER0FA5W",
    "total": 2000
  },
  "amount": 1500,
  "payment": {
    "id": "ZV67XE59NGF1Y"
    "amount": 3500,
  },
  "additionalCharges": {
    "elements": [
      {
        "id": "AGPT72N3N5TDM",
        "amount": 52,
        "rate": 35000,
        "type": "CREDIT_SURCHARGE",
        "refund": {
          "id": "JRWNWS4Y7SSTP"
        }
      }
    ]
  }
}
```

In this example, the customer was refunded $15.00 of the original $35.00. The customer paid with a credit card so was was refunded an additional $0.52 of the original surcharge for a total refund of $15.52.

Total amount refunded to the customer is the sum of the refund `amount` and `additionalCharges.amount`. In the example, the customer was refunded $15.52, which includes the $15.00 `amount` plus a 3.5% surcharge refund of $0.52.

## Surcharge and tips

A customer can add a tip to a payment in two ways: 

- **On the Clover device**—If a customer adds a tip on the device, the `tipAmount` is added to the payment `amount` and then the sum is multiplied by the surcharge `rate` to determine the total charged to the customer's card. For example, if the order `amount` is $25.00, and the customer adds a 20% tip ($5). If they pay with a credit card, they are charged an additional 3.5% surcharge ($1.05).  
  Total amount = `(2500 + 500) * 1.035 = 3105`

- **On a paper receipt**—If a customer adds a tip on a paper receipt, the tip _is not_ included when calculating the surcharge.

***

# Understand convenience fees

Merchants can collect a fixed convenience fee using the Virtual Terminal as an alternative payment channel. If you display transaction data in your app, you must use data from several fields to ensure proper reporting for merchants.

## View convenience fee for a paid transaction

To view the convenience fee collected for a transaction, add the `expand` query parameter with the value  `additionalCharges` as shown in the following example.

### Request

```curl
curl --request GET \
  --url 'https://apisandbox.dev.clover.com/v3/merchants/{merchantUUID}/payments/{paymentUUID}?expand=additionalCharges' \
  --header 'accept: application/json'
```
```json
{
  "id": "MERQ5J3KFETNY",
  "amount": 2000,
  ...
  "additionalCharges": {
    "elements": [
      {
        "id": "3NTR8H89C1D8M",
        "amount": 300,
        "type": "CONVENIENCE_FEE",
        "payment": {
          "id": "MERQ5J3KFETNY"
        }
      }
    ]
  }
}
```

### Response

The response includes an `additionalCharges` object with the following:

| Response parameter | Description                                                                       |
| :----------------- | :-------------------------------------------------------------------------------- |
| `amount`           | Amount in cents paid as a convenience fee on the transaction.                     |
| `type`             | Additional charge processed for the transaction, in this case, `CONVENIENCE_FEE`. |
| `payment`          | Universally unique identifier (UUID) of the associated payment.                   |

The total amount paid by the customer is the sum of the payment `amount` and `additionalCharges.amount`. In the preceding example, the customer was charged $23.00, that is the $20.00 `amount` plus a $3.00 convenience fee.

## View convenience fee for a refund transaction

### Request

```curl
curl --request GET \
  --url 'https://apisandbox.dev.clover.com/v3/merchants/{merchantUUID}/refunds/{refundUUID}?expand=additionalCharges' \
  --header 'accept: application/json'
```
```json
{
  "id": "CY3XR7R6D9B3P",
  "amount": 1550,
  "additionalCharges": {
    "elements": [
      {
        "id": "12DB2D19N2SXE",
        "amount": 300,
        "type": "CONVENIENCE_FEE",
        "refund": {
          "id": "CY3XR7R6D9B3P"
        }
      }
    ]
  }
}
```

### Response

The response includes the following information:

| Response parameters                 | Description                                                                         |
| :---------------------------------- | :---------------------------------------------------------------------------------- |
| `amount`                            | Amount in cents that is refunded to the customer.                                   |
| `additionalCharges.elements.amount` | Amount in cents, originally charged as a convenience fee, refunded to the customer. |
| `additionalCharges.elements.type`   | Additional charge processed for the transaction, in this case, `CONVENIENCE_FEE`.   |
| `additionalCharges.elements.refund` | Universally unique identifier (UUID) of the associated refund.                      |

The total amount refunded to the customer is the sum of the refund `amount` and `additionalCharges.amount`. In the example, the customer was refunded $18.50. The refunded amount includes the $15.50 `amount` plus a $3.00 convenience fee.
