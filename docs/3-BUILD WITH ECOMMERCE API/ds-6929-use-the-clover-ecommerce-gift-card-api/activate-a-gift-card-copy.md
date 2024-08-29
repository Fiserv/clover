---
title: "Reload an active gift card"
slug: "activate-a-gift-card-copy"
excerpt: ""
hidden: true
createdAt: "Mon Aug 12 2024 09:14:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Aug 12 2024 09:17:01 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--2024.Apr.8: Added RegionIcon-US-CAN reusable content to replace long form html -cd\n<!--2024.Jul.2: DS-6674 changed paramer label from \"card_number\" to \"number\" -cd-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

<br />

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
