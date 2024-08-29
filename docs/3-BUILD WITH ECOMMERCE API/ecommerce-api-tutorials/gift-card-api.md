---
title: "Use the Gift Card API"
slug: "gift-card-api"
excerpt: ""
hidden: false
metadata: 
  description: "The Gift Card API allows you to use Clover gift card solutions on Ecommerce platforms."
  image: []
  robots: "index"
createdAt: "Fri Jul 14 2023 13:45:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 02 2024 20:30:33 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--2024.Apr.8: Added RegionIcon-US-CAN reusable content to replace long form html -cd\n<!--2024.Jul.2: DS-6674 changed paramer label from \"card_number\" to \"number\" -cd-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

## What is a gift card

A gift card is a prepaid payment card used to make purchases at participating restaurants, stores, or online retailers. A gift card can have different denominations. You can redeem the value of these cards for services, merchandise, or even cash, depending on the terms and conditions set by the card issuer.

## Clover Gift Cards 💳

You can:

- Use Clover Gift Card Solutions to check out online or in person at the point of sale (POS). This is a native gift card with an SCV (security code value) that uses the integrated gift card solution payment gateway from Fiserv.
- Use a non-native gift card with an FCA (foreign access code). A non-Fiserv gift card or a gift card that does not use the Fiserv payment gateway.
- Use the purchase or split tender feature to start the transaction with a gift card and complete the transaction with another credit or debit card.
- Use the Gift Card API to perform the following actions:

  - Activation
  - Balance inquiry
  - Redeem
  - Reload
  - Cashout
  - Refund or void a transaction

## Use the Clover Gift Card API

### Prerequisites for merchants

- Set up gift card tiers in Gift Solutions. For merchants who use the Clover device, configure a merchant account for the gift card tiers in Clover Gift Card Solutions to enable the processing of gift cards. The Clover server synchronizes the order data with the merchant's Clover devices. You can use the gift card endpoint to leverage the gift card features added to Clover payment solutions.
- Your merchant needs to sign up for [Clover Gift Cards](https://www.clover.com/pos-systems/gift-cards) for gift card plans.

### Prerequisites to use Clover Gift Cards APIs

1. Get an OAuth token and [generate a PAKMS key](https://docs.clover.com/docs/ecommerce-generating-a-card-token#generate-a-pakms-key).
2. [Create a gift card token](https://docs.clover.com/reference/create-giftcard-token), for example: `clv_1TSxxxxxx2S71ECrva7`

### Use the Clover Gift Card API

**Step 1: Generate or retrieve API key**

```curl
curl  --request GET \
--url 'https://dev1.dev.clover.com/pakms/apikey'  
--header 'authorization: Bearer <Token>'
```

See [Create a gift card token](https://docs.clover.com/docs/create-a-gift-card-token).

**Step 2: Generate a token for the gift card using `/v1/tokens`**

Clover receives the gift card number and SCV (security code value associated with the gift card) from the Clover token in an encrypted format.

Example:

```curl
curl --request POST \
--url 'https://token-sandbox.dev.clover.com/v1/tokens' \
--header 'apiKey: <apikey>' \
--header 'content-Type: application/json' \
--data-raw '{
  "gift_card": {
    "number": "98765441066",
    "security_code": "785577",
    "foreign_access_code": "67755"
  }
}'
```

**Gift Card token API request parameters**

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "h-2": "Required/Optional",
    "0-0": "`number`",
    "0-1": "Gift card number.  \nLength: One of the following: 6-digit, 13-digit, 16-digit, or 19-digit",
    "0-2": "Required",
    "1-0": "`security_code`",
    "1-1": "Encrypted security code associated with the gift card.  \nLength: 4-8 characters",
    "1-2": "Optional",
    "2-0": "`foreign_access_code`",
    "2-1": "Foreign access code for merchants converting to CLGC (closed loop gift card) from an external gift card program, if applicable.",
    "2-2": "Optional"
  },
  "cols": 3,
  "rows": 3,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Activate gift card

This transaction creates and activates a new gift card and returns the necessary information to use the account.

- If the card is non-denominated, the amount is required.
- If the card is denominated, the amount field is optional.
- If the amount is entered, it must match the card's value defined in the promotion code.

### Activate virtual gift card

Use the `/v1/activate` endpoint to create and activate a virtual gift card.

Example: Ecomm virtual activation API request and response samples for creating and activating a denominated card:

```curl
curl --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/activate' \
--header 'authorization: Bearer <token>' \
--header 'content-Type: application/json' \
--data '{
    "promotion_code": "67062"
}'
```
```json
{
    "id": "ABC123DE45F6G",
    "amount": 5000,
    "ref_num": "022001",
    "outcome": {
        "network_status": "approved_by_network",
        "type": "authorized"
    },
    "paid": true,
    "status": "succeeded",
    "source": {
        "last4": "0266"
    },
    "gift_card": {
        "security_card_value": "75537209",
        "expiration_date": "3025-01-01",
        "number": "7777373144600266",
        "previous_balance": 0,
        "new_balance": 5000
    }
}
```

Example: Ecomm virtual activation API request and response for creating and activating a non-denominated card:

```curl
curl --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/activate' \
--header 'authorization: Bearer<token>' \
--header 'content-Type: application/json' \
--data '{
    "promotion_code": "67063",
    "amount": 2000,
    "currency": "usd"
}

```
```json
{
    "id": "ABC123DE45F6G",
    "amount": 2000,
    "ref_num": "021717",
    "outcome": {
        "network_status": "approved_by_network",
        "type": "authorized"
    },
    "paid": true,
    "status": "succeeded",
    "source": {
        "last4": "1096"
    },
    "gift_card": {
        "security_card_value": "3256",
        "expiration_date": "3025-01-01",
        "number": "7777373191541096",
        "previous_balance": 0,
        "new_balance": 2000
    }
}
```

### Activate physical gift card

Use the `v1/activate` endpoint to activate an inactive physical gift card. Send a POST request to `v1/activate` endpoint.

Example: Activate a physical denominated gift card of $50 value.

```curl
curl --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/activate' \
--header 'authorization: Bearer <token>' \
--header 'content-Type: application/json' \
--data-raw '{
    "source": "clv_1TSxxxxxx2S71ECrva7"
}'


```
```json
{
    "id": "ABC123DE45F6G",
    "amount": 5000,
    "ref_num": "201108",
    "outcome": {
        "network_status": "approved_by_network",
        "type": "authorized"
    },
    "paid": true,
    "status": "succeeded",
    "source": {
        "last4": "9585"
    },
    "gift_card": {
        "expiration_date": "3025-01-01",
        "previous_balance": 0,
        "new_balance": 5000
    }
}
```

**Activate gift card request parameters**

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "h-2": "Required/Optional",
    "0-0": "`source`",
    "0-1": "Tokenized card (`cToken`) that is saved as a card on file (COF) for future transactions.",
    "0-2": "Required",
    "1-0": "`amount`",
    "1-1": "Amount activated for the gift card in local currency.",
    "1-2": "Required",
    "2-0": "`currency`",
    "2-1": "Three-letter [ISO 4217 currency code](https://www.iso.org/iso-4217-currency-codes.html).  \nFormat: Lowercase  \nLength: Maximum 3",
    "2-2": "Required",
    "3-0": "`promotion_code`",
    "3-1": "Virtual promotional code of the gift card.  \n**Note:** Applicable only for gift card virtual activation if the promo code is not already configured.",
    "3-2": "Optional"
  },
  "cols": 3,
  "rows": 4,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Reload an active gift card

Use the `/v1/reload` endpoint to reload an amount to an active gift card account.

Example:

```curl
curl --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/reload' \
--header 'authorization: Bearer <authToken>' \
--header 'content-Type: application/json' \
--data-raw '{
   "source": "clv_1TSxxxxxx2S71ECrva7",
   "amount": 500,
   "currency": "usd",
}'

```
```json
{
   "id": "ABC123DE45F6G",
   "amount": 500,
   "ref_num": "151415",
   "outcome": {
       "network_status": "approved_by_network",
       "type": "authorized"
   },
   "paid": true,
   "status": "succeeded",
   "source": {
       "id": "clv_1TSxxxxxx2S71ECrva7",
       "last4": "5003"
   },
   "gift_card": {
       "expiration_date": "3025-01-01",
       "previous_balance": 92,
       "new_balance": 592
   }
}
```

**Reload gift card request parameters**

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "h-2": "Required/Optional",
    "0-0": "`source`",
    "0-1": "Tokenized card (`cToken`) that is saved as a card on file (COF) for future transactions.",
    "0-2": "Required",
    "1-0": "`amount`",
    "1-1": "Amount activated for the gift card in local currency.",
    "1-2": "Required",
    "2-0": "`currency`",
    "2-1": "Three-letter [ISO 4217 currency code](https://www.iso.org/iso-4217-currency-codes.html).  \nFormat: Lowercase  \nLength: Maximum 3",
    "2-2": "Required"
  },
  "cols": 3,
  "rows": 3,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Request gift card balance

Use the `/v1/balance_inquiry` endpoint to request the current balance of an active gift card account.

Example:

```curl
curl  --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/balance_inquiry' \
--header 'authorization: Bearer <authToken>' \
--header 'content-Type: application/json' \
--data-raw '{
   "source": "clv_1TSxxxxxx2S71ECrva7"
}'

```
```json
{
   "status": "succeeded",
   "gift_card": {
       "expiration_date": "2025-01-01",
       "previous_balance": 5000,
       "new_balance": 5000,
       "lock_amount": 0
   }
}

```

**Balance inquiry gift card request parameters**

| Field    | Description                                                                              | Required/Optional |
| :------- | :--------------------------------------------------------------------------------------- | :---------------- |
| `source` | Tokenized card (`cToken`) that is saved as a card on file (COF) for future transactions. | Required          |

## Request gift card balance with multi-lock

Multi-lock allows you to:

- Lock a requested amount up to the current available balance of the gift card or up to the requested amount for a preset time.
- Keep one or more locks active on a gift card at any given time until you have a balance on the gift card. The gift card automatically unlocks the preset value for use when:
  - The preset multi-lock time expires.  
    -or-
  - A POST request for Redemption Unlock with multi-lock is sent to `/v1/charges`.  

Example:

```curl
curl  --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/charges' \
--header 'authorization: Bearer <authToken>' \
--header 'content-Type: application/json' \
--data-raw '{
   "source": "clv_1TSxxxxxx2S71ECrva7",
   "amount": 100,
   "currency": "usd",
   "capture": "false",
   "partial_redemption": "true",
}'

```
```json
{
   "id": "ABC123DE45F6G",
   "amount": 100,
   "payment_method_details": "giftCard",
   "amount_refunded": 0,
   "captured": false,
   "ref_num": "151520",
   "outcome": {
       "network_status": "approved_by_network",
       "type": "authorized"
   },
   "status": "succeeded",
   "source": {
       "id": "clv_1TSxxxxxx2S71ECrva7",
       "last4": "5003"
   },
   "partial_auth": true,
   "gift_card": {
       "expiration_date": "2025-01-01",
       "previous_balance": 592,
       "new_balance": 492,
       "lock_id": 251
   }
}
```

## Redeem gift card for insufficient balance (non-sufficient funds)

If a gift card value is less than the charge amount, you can request partial approval to redeem the available amount on an active gift card account. Use `/v1/charges` to redeem the gift card value.

**Note:** A decline is not given for insufficient funds. If the requested amount exceeds the account balance, the account is reduced to 0 (zero) and may be closed.

Examples:

**Redemption for sufficient balance**

```curl
curl --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/charges' \
--header 'authorization: Bearer <authToken>' \
--header 'content-Type: application/json' \
--data-raw '{
   "source": "clv_1TSxxxxxx2S71ECrva7",
   "amount": 100,
   "currency": "usd",
   "capture": "true",
   "partial_redemption": "true",
   "return_gateway_response": "true"
```
```json
{
   "id": "ABC123DE45F6G",
   "amount": 100,
   "payment_method_details": "giftCard",
   "amount_refunded": 0,
   "captured": true,
   "ref_num": "308196",
   "outcome": {
       "network_status": "approved_by_network",
       "type": "authorized"
   },
   "paid": true,
   "status": "succeeded",
   "source": {
       "id": "clv_1TSxxxxxx2S71ECrva7",
       "last4": "5003"
   },
   "partial_auth": true,
   "gift_card": {
       "expiration_date": "2025-01-01",
       "previous_balance": 500,
       "new_balance": 400
   }
}
```

**Redemption for insufficient balance**

```curl
curl --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/charges' \
--header 'authorization: Bearer <authToken>' \
--header 'content-Type: application/json' \
--data-raw '{
   "source": "clv_1TSxxxxxx2S71ECrva7",
   "amount": 100,
   "currency": "usd",
   "capture": "true",
   "partial_redemption": "false",
   "return_gateway_response": "true"
}
```
```json
{
   "id": "CKK5GVZBHB1GA",
   "amount": 10,
   "payment_method_details": "giftCard",
   "amount_refunded": 0,
   "currency": "usd",
   "created": 1681705896145,
   "captured": true,
   "ref_num": "308942",
   "auth_code": "445869",
   "warning_message": "partial_redemption should be true for gift card",
   "outcome": {
       "network_status": "approved_by_network",
       "type": "authorized"
   },
   "paid": true,
   "status": "succeeded",
   "source": {
       "id": "clv_1TSxxxxxx2S71ECrva7",
       "last4": "5003"
   },
   "gift_card": {
       "expiration_date": "2025-01-01",
       "previous_balance": 500,
       "new_balance": 400
   }
}
```

## Request redemption unlock with multi-lock

After a Balance Inquiry with a multi-lock transaction, you can complete the purchase on a gift card and unlock any remaining balance from the transaction. The amount to redeem is removed from the balance of the gift card. To unlock a gift card without affecting the balance, send 0 (zero), use `/v1/charges/{chargeId}/capture` endpoint.

Example:

```curl
curl  --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/charges/chargeId/capture' \
--header 'authorization: Bearer <authToken>' \
--header 'content-Type: application/json' \
--data-raw '{
   "amount": "100"
}
```
```json
{
   "id": "ABC123DE45F6G",
   "amount": 100,
   "payment_method_details": "giftCard",
   "currency": "usd",
   "created": 1680800253000,
   "captured": false,
   "ref_num": "151528",
   "auth_code": "753947",
   "order": "3D7T140NCZ3Z0",
   "outcome": {
       "network_status": "approved_by_network",
       "type": "authorized"
   },
   "paid": true,
   "status": "succeeded",
   "source": {
       "id": "clv_1TSTSBAjam8Fqo1ju5iNq1Tt",
       "brand": "GIFT_CARD",
       "first6": "777732",
       "last4": "5003"
   },
   "gift_card": {
       "expiration_date": "2025-01-01",
       "previous_balance": 592,
       "new_balance": 492,
       "lock_amount": 0,
       "lock_id": 251
   }
}
```

## Refund to a gift card

Use `/v1/refunds` endpoint to refund the value back to the card. This differs from a reload as the customer does not provide funds to add value. This transaction is usually used for merchandise returns or unfulfilled orders where the card was previously charged. 

Example:

```curl
curl  --request POST \
--url 'https: //scl-sandbox.dev.clover.com/v1/refunds' \
--header 'authorization: Bearer <authToken>' \
--header 'content-Type: application/json' \
--data-raw '{
   "reason": "requested_by_customer",
   "charge": "1ABCDEF23GHIJ"
}'
```

**Refund of a gift card request parameters**

| Field    | Description                                                                                                                                                                                                                            | Required/Optional |
| :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------- |
| `charge` | Unique identifier (ID) of the charge to refund. The charge parameter is available in the [get charges ](https://docs.clover.com/reference/getcharges)and [get a charge](https://docs.clover.com/reference/getchargescharge) endpoints. | Required          |

## Void of redemption or cashout

Use `v1/refunds` endpoint to void a redemption or cashout.

Example:

```curl
curl  --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/refunds'  
--header 'authorization: Bearer <authToken>'  
--header 'content-Type: application/json'  
--data-raw '{  
   "reason": "requested_by_customer",  
   "charge": "1ABCDEF23GHIJ"  
}'
```

**Void of redemption a gift card request parameters**

| Field    | Description                                                                                                                                                                                                                            | Required/Optional |
| :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------- |
| `charge` | Unique identifier (ID) of the charge to refund. The charge parameter is available in the [get charges ](https://docs.clover.com/reference/getcharges)and [get a charge](https://docs.clover.com/reference/getchargescharge) endpoints. | Required          |

## Void of reload or refund

Use `/v1/refunds/refundId/cancel` endpoint for the void of refund.

Examples:

```curl
curl  --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/refunds/{{refundId}}/cancel' \
--header 'authorization: Bearer <authToken>' \
--header 'content-Type: application/json' \
--data-raw '{
   "reason": "USER_CANCEL"
}'
```
```json
{  "id": "ABC123DE45F6G",
   "object": "void_on_refund",
   "amount": 100,
   "charge": "1ABCDEF23GHIJ",
   "status": "succeeded",
   "metadata": {
       "refundType": "VOID",
       "authCode": "660762",
       "refNum": "125057",
       "gatewayResponseCode": "00"
   },
   "gift_card": {
       "expiration_date": "2025-01-01",
       "previous_balance": 400,
       "new_balance": 300,
       "lock_amount": 0
   }
}
```

Use `/v1/refunds` endpoint for the void of reload

```curl
curl  --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/refunds' \
--header 'authorization: Bearer <authToken>' \
--header 'content-Type: application/json' \
--data-raw '{
   "reason": "requested_by_customer",
   "charge": "1ABCDEF23GHIJ"
}'
```
```json
{  "id": "ABC123DE45F6G",
   "object": "refund",
   "amount": 500,
   "charge": "1ABCDEF23GHIJ",
   "created": 1681702944579,
   "status": "succeeded",
   "metadata": {
       "refundType": "VOID",
       "authCode": "603796",
       "refNum": "307916",
       "gatewayResponseCode": "00"
   },
   "gift_card": {
       "expiration_date": "2025-01-01",
       "previous_balance": 500,
       "new_balance": 0,
       "lock_amount": 0
   }
}
```

**Void of reload or refund a gift card request parameters**

| Field    | Description                                                                                                                                                                                                                            | Required/Optional |
| :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------- |
| `charge` | Unique identifier (ID) of the charge to refund. The charge parameter is available in the [get charges ](https://docs.clover.com/reference/getcharges)and [get a charge](https://docs.clover.com/reference/getchargescharge) endpoints. | Required          |

## Request gift card balance cashout

Use `/v1/cashout` endpoint to create a cashout request to remove the remaining balance from the card.

Example:

```curl
curl  --request POST \
--url 'https://scl-sandbox.dev.clover.com/v1/cashout'  
--header 'authorization: Bearer <authToken>'  
--header 'content-Type: application/json'  
--data-raw '{  
   "source": "clv_1TSxxxxxx2S71ECrva7"  
}'
```

**Cashout a gift card request parameters**

| Field    | Description                                                                              | Required/Optional |
| :------- | :--------------------------------------------------------------------------------------- | :---------------- |
| `source` | Tokenized card (`cToken`) that is saved as a card on file (COF) for future transactions. | Required          |
