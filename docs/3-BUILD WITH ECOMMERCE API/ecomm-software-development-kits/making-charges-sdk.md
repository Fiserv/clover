---
title: "Make simple charges (SDK)"
slug: "making-charges-sdk"
excerpt: ""
hidden: false
metadata: 
  description: "This tutorial shows how to make a simple charge request using a Clover Ecommerce SDK."
  image: 
    - "https://files.readme.io/50a5857-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Thu Jan 30 2020 09:44:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 08:56:16 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Complete the following steps to accept a simple payment using an Ecommerce SDK.

# 1. Create a card token

Apps using an SDK must provide the card token Clover uses to process secure payments.

> 🚧 IMPORTANT
> 
> While your app can generate tokens, storing and processing non-tokenized card data on the server side may increase your PCI compliance burden. Clover recommends using the hosted `iframe` to collect card data on the client side instead. **The following steps should only be used when client-side tokenization is not feasible or possible.**

## Encrypt card data

The `card` object in the `create()` method contains the details of the card being tokenized. To tokenize an encrypted card, use the `encrypted_pan` property.

```python
{
    card={
        'encrypted_pan': '{encrypted_card_number}',
        'first6': '601136',
        'last4': '6668',
        'exp_month': '12',
        'exp_year': '2021',
        'cvv': '123',
        'brand': 'DISCOVER'
    }
}
```

1. To get the encryption information required for `encrypted_pan`, send a GET request to `/v2/merchant/{mId}/pay/key`.

```json
{
    "modulus": "{modulus}", // base-10
    "exponent": "{exponent}",
    "prefix": "{prefix}" 
}
```

2. Encrypt the card information. Follow the encryption example code from the <a href="https://drive.google.com/file/d/1QmQGpLQn-5NiIbjYa2G_qVjeLD-JftfI/view?usp=sharing" target="_blank">Java example app</a>.
   - Prepend the `prefix` value to the card number.
   - Generate an RSA public key using the `modulus` and `exponent` values.
   - Using the public key, encrypt the combined prefix and card number.
   - Base64 encode the resulting encrypted data into a string. This string is the `encrypted_pan` value in the `/v1/tokens` request.

In response, an encrypted card number is generated. All `encrypted_pan` values are alphanumeric and end with `==`.

> 📘 NOTE
> 
> The `modulus` returned by Clover is in base 10. Various libraries expect moduli in different bases.

## Tokenize encrypted card data

To create a token, call the `[create a card token](https://docs.clover.com/reference/createtoken)` method and pass in the minimum required card information:

- `encryted_pan`
- `first6`
- `last4`
- `brand`
- `exp_month`
- `exp_year`
- `cvv`

```python Python
from clover import Token

token = clover.Token.create(
    card={
        'encrypted_pan': '{encrypted_card_number}',
        'first6': '601136',
        'last4': '6668',
        'exp_month': '12',
        'exp_year': '2021',
        'cvv': '123',
        'brand': 'DISCOVER'
    }
)
```
```javascript Node
require('dotenv').config();
const Clover = require("clover-ecomm-sdk");

let ACCESS_TOKEN = process.env.ACCESS_TOKEN;
let ENVIRONMENT = process.env.ENVIRONMENT;

const cloverInst = new Clover(ACCESS_TOKEN, {
  environment: ENVIRONMENT
});

let token = cloverInst.charges.create({
  card: {
       'encrypted_pan': '{encrypted_card_number}',
       'first6': '601136',
       'last4': '6668',
       'exp_month': '12',
       'exp_year': '2021',
       'cvv': '123',
       'brand': 'DISCOVER'
  },
  'apiKey': API_KEY
});
```

This returns a token object in JSON. The `id` value will be used in later steps to complete the payment.

```json Create token response
{
  'id': 'clv_1TSTSpbfbN6Jh5CqCm3bMQne',
  'object': 'token',
  'card': {
    'exp_month': '12',
    'exp_year': '2021', 
    'last4': '6668', 
    'brand': 'DISCOVER'
  }
}
```

Clover provides several [sandbox test cards](doc:test-card-numbers) that can be used when developing your app. 

# 2. Create a charge

Once you have a token, you can charge the customer's card for the required amount. To do so, call the   associated `[create a charge](https://docs.clover.com/reference/createcharge)` method and pass in the minimum required order data:

- `amount`
- `currency`
- `source`

```python Python
from clover import Charge

charge = Charge.create(
    amount=1358,
    currency='usd',
    tax_rate_uuid='{tax_uuid}',
    source='clv_1TSTSpbfbN6Jh5CqCm3bMQne'
)
```
```javascript Node
require('dotenv').config();
const Clover = require("clover-ecomm-sdk");

let ACCESS_TOKEN = process.env.ACCESS_TOKEN;
let API_KEY = process.env.API_KEY;
let ENVIRONMENT = process.env.ENVIRONMENT;

const cloverInst = new Clover(ACCESS_TOKEN, {
  environment: ENVIRONMENT
});

let charge = cloverInst.charges.create({
  amount: 1358,
  currency: 'usd',
  tax_rate_uuid: '{tax_uuid}',
  source: 'clv_1TSTSpbfbN6Jh5CqCm3bMQne'
});
```

In this example, tax is set using the `tax_rate_uuid` object. You can set tax values for your charge amount in two ways.

[block:parameters]
{
  "data": {
    "h-0": "Tax object",
    "h-1": "Description",
    "0-0": "Tax as UUID (recommended)",
    "0-1": "To set the tax based on merchant tax information, use `tax_rate_uuid`. This is the recommended approach.  \nTaxes are set under **Setup > Taxes & Fees** on the Merchant Dashboard. You can retrieve this merchant tax information with `/v3/merchants/{mId}/tax_rates`.",
    "1-0": "Tax as amount",
    "1-1": "To set a flat fee, use `tax_amount`."
  },
  "cols": 2,
  "rows": 2,
  "align": [
    "left",
    "left"
  ]
}
[/block]


> 📘 NOTE
> 
> When adding taxes in your charge request, the `amount` must be the sum of the items and any tax or tip. For example, if the cost of the item is $10 and the tax is $1. the `amount` value must be `1100` ($11).

In response, a charge `id` is created. See the [Create a charge tutorial](doc:create-a-charge) for complete information about the returned values when creating a charge.

```json Create charge response
{
  'id': 'CEDW57FP91ZB6',
  'amount': 1358, // (item cost + tax)
  'tax_amount': 135,
  'amount_refunded': 0,
  'currency': 'usd', 
  'created': 1580408081825,
  'captured': false,
  'ref_num': '015600501490',
  'auth_code": "OK0433',
  'outcome': {
    'network_status': 'approved_by_network',
    'type': 'authorized'
  },
  'paid': True,
  'refunded': False,
  'status': 'succeeded',
  'source': {
    'id': 'clv_1TSTSpbfbN6Jh5CqCm3bMQne',
    'brand': 'DISCOVER', 
    'cvc_check': 'pass',
    'exp_month': '12',
    'exp_year': '2021',
    'last4': '6668'
  }
}
```

# 3. Add a tip to your charge

You can use the `tip_amount` (in cents) value to add a tip before paying for a charge.

```python
from clover import Charge

charge = Charge.create(
    amount=1358,
    tip_amount=200,
    currency='usd',
    source='clv_1TSTSpbfbN6Jh5CqCm3bMQne'
)
```
```javascript Node
require('dotenv').config();
const Clover = require("clover-ecomm-sdk");

let ACCESS_TOKEN = process.env.ACCESS_TOKEN;
let API_KEY = process.env.API_KEY;
let ENVIRONMENT = process.env.ENVIRONMENT;

const cloverInst = new Clover(ACCESS_TOKEN, {
  environment: ENVIRONMENT
});

let charge = cloverInst.charges.create({
  amount: 1358,
  tip_amount: 200,
  currency: 'usd',
  source: 'clv_1TSTSpbfbN6Jh5CqCm3bMQne'
});
```

## Calculations with tips

Always submit the charge amount and tip separately. In the above Python example, for a subtotal of $13.58 and a tip of $2:

|               | Subtotal      | Tip              |
| :------------ | :------------ | :--------------- |
| **Correct**   | `amount=1358` | `tip_amount=200` |
| **Incorrect** | `amount=1558` | `tip_amount=200` |

> 📘 NOTE
> 
> Tipping is available only for card-present transactions.
