---
title: "Use 3-D Secure for e-commerce transactions"
slug: "use-3ds"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how Clover uses 3DS to authenticate customers and safeguard e-commerce card-not-present (CNP) transactions from fraud."
  image: []
  robots: "index"
createdAt: "Tue Oct 10 2023 07:29:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Aug 14 2024 09:42:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\" description\" content= \"Learn how Clover uses 3DS to authenticate customers and safeguard e-commerce card-not-present (CNP) transactions from fraud.\" >\n<!--This topic is part of create a charge API and is for non clover developers and this topic is not part of 3DS commercilization -->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

> 🚧 **IMPORTANT**: **Minimum data requirements for Visa Secure authentication requests**
> 
> As per article ID: AI13666, effective August 12, 2024, Visa<sup>®</sup> requires information from three data fields for all tokenized Visa Secure EMV® 3-D Secure (3DS) payment transactions. The three **required** data fields in authentication request messages are:
> 
> - Browser Internet Protocol (IP) address or the device IP address for in-app transactions
> - Cardholder name
> - Cardholder email address or phone number, or both
> 
> Clover recommends merchants to check with their providers for 3D Secure (3DS) enablement.

3-D Secure (3DS) is a protocol that provides an additional security layer for online credit and debit card-not-present (CNP) transactions. Clover uses the EMV® 3DS to authenticate customers and safeguard against CNP fraud. 3D stands for three domains:

1. The card issuer.
2. The merchant receiving the payment.
3. The 3DS infrastructure platform that is a secure go-between for the customer and the merchant.

## Enable 3DS

3DS is required for apps intended for use in the European region. It is optional in other regions, but you can still use it as a tool to reduce fraud. 

To create an additional security layer for CNP transactions, add the 3DS authentication method while using the [Create a charge](https://docs.clover.com/reference/createcharge) endpoint. When you turn on 3D Secure, the cardholder must validate every transaction with a secure personal identification number (PIN) sent to their phone or associated devices from their card issuer.

All major card issuers offer 3DS by a different brand name. Example:

[block:parameters]
{
  "data": {
    "h-0": "Card issuer",
    "h-1": "3DS",
    "0-0": "American Express<sup>®</sup>",
    "0-1": "SafeKey®",
    "1-0": "Discover<sup>®</sup>",
    "1-1": "ProtectBuy®",
    "2-0": "Mastercard<sup>®</sup>",
    "2-1": "SecureCode",
    "3-0": "Visa<sup>®</sup>",
    "3-1": "Visa Secure"
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## 3DS parameter requirement

Add the 3DS object to your [charge](https://docs.clover.com/reference/createcharge) request to initiate the 3DS authentication.

[block:parameters]
{
  "data": {
    "h-0": "Object",
    "h-1": "Type",
    "h-2": "Description",
    "h-3": "Required/Optional",
    "0-0": "`source`",
    "0-1": "String",
    "0-2": "Source of the 3DS authentication, for example NON_CLOVER.",
    "0-3": "Required",
    "1-0": "`authentication_result`",
    "1-1": "Object",
    "1-2": "3DS authentication result. 3DS is a protocol that provides an additional security layer for online credit and debit card-not-present (CNP) transactions.",
    "1-3": "Required",
    "2-0": "\\-  `authentication_status`",
    "2-1": "String",
    "2-2": "Authentication status of 3DS transaction.  \nValues:  \n  \n- Success  \n- Failed  \n- Attempted  \n- Unavailable  \n- Rejected",
    "2-3": "Optional",
    "3-0": "\\- `transaction_id `",
    "3-1": "String",
    "3-2": "3DS transaction identifier.",
    "3-3": "Optional",
    "4-0": "\\- `cryptogram`",
    "4-1": "String",
    "4-2": "3DS cryptogram is an authentication method associated with the cards stored as Android device tokens. Returned payment data includes a (3DS) cryptogram generated on the device.",
    "4-3": "Required for non-Clover 3DS",
    "5-0": "\\- `threeds_version`",
    "5-1": "String",
    "5-2": "3DS authentication version.  \n**Note:** Clover supports 3DS version 2.0 only. Upgrade your version to 2.0, as 1.0 is no longer supported",
    "5-3": "Optional"
  },
  "cols": 4,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Request and response examples

```curl
curl --request POST \
   --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
   --header 'accept: application/json' \
   --header 'authorization: Bearer ab86a5e8-48f3-b3bd-8c45-d415e9867833' \
   --header 'content-type: application/json' \
   --data '
{
 "ecomind": "ecom",
 "metadata": {
  "existingDebtIndicator": false
 },
 "threeds": {
  "authentication_result": {
   "authentication_status": "SUCCESS",
   "transaction_id": "CAACCVVUlwCXUyhQNlSXAAAAAAA",
   "cryptogram": "11B5 2345 49C3 C4DD 931A 27BD 8CA3 CD82",
   "threeds_version": "2"
  },
  "source": "NON_CLOVER"
 },
 "source": "clv_1ABCDefgHI23jKL4m5nOPQrS",
 "amount": 100,
 "currency": "USD",
 "description": "test"
}
‘
```
```json
{
 "id": "3NTR8H89C1D8M", 
 "amount": 100,
 "payment_method_details": "card",
 "amount_refunded": 0,
 "currency": "USD",
 "created": 1234567891234,
 "description": "test",
 "captured": true,
 "ref_num": "1234567891",
 "auth_code": "121212",
 "outcome": {
  "network_status": "approved_by_network",
  "type": "authorized"
 },
 "paid": true,
 "status": "succeeded",
 "source": {
  "id": "clv_1ABCDefgHI23jKL4m5nOPQrS",
  "brand": "DISCOVER",
  "exp_month": "01",
  "exp_year": "2030",
  "first6": "123456",
  "last4": "4321"
 },
 "ecomind": "ecom",
 "threeds": {
  "validation_result": "AUTHENTICATION_STATUS_UNKNOWN",
  "liability_protection_status": "NOT_PROTECTED"

```
