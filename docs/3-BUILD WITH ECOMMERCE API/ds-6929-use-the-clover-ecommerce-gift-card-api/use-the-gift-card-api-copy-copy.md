---
title: "Activate a gift card"
slug: "use-the-gift-card-api-copy-copy"
excerpt: ""
hidden: true
createdAt: "Mon Aug 12 2024 09:14:12 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Aug 12 2024 09:16:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--2024.Apr.8: Added RegionIcon-US-CAN reusable content to replace long form html -cd\n<!--2024.Jul.2: DS-6674 changed paramer label from \"card_number\" to \"number\" -cd-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

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
