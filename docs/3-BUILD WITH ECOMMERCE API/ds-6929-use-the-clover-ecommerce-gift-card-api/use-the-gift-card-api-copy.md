---
title: "Check gift card balance"
slug: "use-the-gift-card-api-copy"
excerpt: ""
hidden: true
createdAt: "Mon Aug 12 2024 09:09:12 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Aug 12 2024 09:18:30 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--2024.Apr.8: Added RegionIcon-US-CAN reusable content to replace long form html -cd\n<!--2024.Jul.2: DS-6674 changed paramer label from \"card_number\" to \"number\" -cd-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

<br />

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
