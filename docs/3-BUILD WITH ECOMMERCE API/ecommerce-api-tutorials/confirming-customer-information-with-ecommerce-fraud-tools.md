---
title: "Confirm customer information with fraud tools"
slug: "confirming-customer-information-with-ecommerce-fraud-tools"
excerpt: ""
hidden: false
metadata: 
  description: "The Clover Ecommerce API provides fraud prevention tools to help protect merchants from unauthorized transactions."
  image: 
    - "https://files.readme.io/eef72d7-clover-symbol-green_3.png"
    - "clover-symbol-green (3).png"
    - 512
    - 512
    - "#228800"
  robots: "index"
createdAt: "Tue Feb 02 2021 18:38:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


## Overview

When you create a card token or charge a customer's card, Clover checks some of the submitted data against the issuer's cardholder information to verify the card is being used legitimately. These checks include three possible values that correspond to fields in the response:

- The CVC/CVV provided by the customer - `cvc_check`
- The first line of the customer's address - `address_line1_check`
- The postal code provided by the customer - `address_zip_check`

The checks return one of four values:

- `pass` - the data provided matches the cardholder information
- `failed` - the data provided does not match the information on file
- `unavailable` - the issuer was not able to confirm the CVC or address at the time of the request
- `unchecked` - the data was provided, but the issuer system did not provide a response

## Examples

> 🚧 IMPORTANT
> 
> Because the sandbox environment uses an emulated payment gateway, some fraud check fields may not appear in API responses.

### Charging a tokenized card

The following example shows how to construct a token request that includes all data to be checked.

```json
{
  "card": {
    "number": "6011361000006668",
    "exp_month": "12",
    "exp_year": "2021",
    "cvv": "123",
    "brand": "DISCOVER",
    "address_line1": "415 N Mathilda Ave",
    "address_city": "Sunnyvale",
    "address_state": "CA",
    "address_zip": "94085",
    "address_country": "US"
  }
}
```

The CVC and address information is not checked when the card is tokenized. For the fraud checks to occur, your app must use the token as the `source` for a charge or order payment request. If you examine the response in either case, you will see the fraud check fields in the `source` object.

```json
{
  "id": "KYZ5X18N6ZX7P",
  "amount": 563,
  "paid": true,
  "status": "succeeded",
  "source": {
    "id": "clv_1TSTSC9WX8G52NFGikM9YWuW",
    "address_city": "Colorado Springs",
    "address_country": "US",
    "address_line1": "2424 Garden of the Gods Rd",
    "address_line1_check": "pass",
    "address_line2": "Ste 1400",
    "address_state": "CO",
    "address_zip": "80919",
    "address_zip_check": "pass",
    "brand": "DISCOVER",
    "cvc_check": "pass",
    "exp_month": "12",
    "exp_year": "2021",
    "first6": "601136",
    "last4": "6668"
  }
}
```

## Recommendations for AVS checks

If the customer-provided postal code does not match the cardholder's code, the response includes `"address_zip_check": "failed"`. Your app should automatically refund the payment in this case using the [Create a refund](https://docs.clover.com/reference/createrefund) or [Return an order](https://docs.clover.com/reference/postordersidreturns) endpoint.

The `address_line1_check` may return a false negative result due to factors like how the address was formatted in the request and how the address is formatted in the issuer's system. If `address_line1_check` is the only one that fails, your app may advise the merchant to take action and verify the validity of the transaction. In general, a payment should not be automatically refunded based on this check alone.

## Recommendations for CVC checks

If the customer's PIN does not match the PIN stored with the issue, the response includes \`"cvc_check": "failed". Your app should automatically refund the payment in this case using the [Create a refund](https://docs.clover.com/reference/createrefund) or [Return an order](https://docs.clover.com/reference/postordersidreturns) endpoint.
