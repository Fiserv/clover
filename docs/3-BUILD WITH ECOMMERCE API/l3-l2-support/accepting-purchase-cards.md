---
title: "Levels and processing of purchasing cards"
slug: "accepting-purchase-cards"
excerpt: ""
hidden: false
metadata: 
  description: "The Ecommerce API allows you to process purchase card transactions that include Level 2 card data. Read more to find out how to use this feature to improve B2B transactions."
  image: []
  robots: "index"
createdAt: "Wed Jun 30 2021 19:34:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:20:29 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

## Purchasing card levels

There are three levels of data for processing purchase cards. Each level decides whether a transaction is qualified. 

### Level 1

Level 1, also known as `level I`, card data is processed for most consumer transactions. It provides authorization and settlement information to cardholders and is limited to the purchase data returned to a cardholder. Level 1 purchasing data is usually the same information as captured during a traditional credit card purchase transaction, including the purchase amount, date, category code, retailer name, and so on. 

### Level 2

Level 2, also known as `level II`, card data is processed for business or corporate purchase cards that are used for B2B transactions, such as order number, freight amount, source/destination postal codes, and so on. These cards can have lower processing expenses for merchants. Level 2 cards provide the same information captured at Level 1, but may also include tax amount, accounting code, tax ID number, and so on. Level 2 data can be processed through either a standard credit card transaction or a purchasing card. For more information, see [Level 2 data](https://docs.clover.com/docs/understanding-level-2-data).

### Level 3

Level 3, also known as `level III`, card data includes the same information captured at Levels I and II, and can also include quantities, product codes, product descriptions, freight amount, duty amount, order number, unit of measure, discount indicator, discount amount, tax rate applied, debit or credit indicator, and so on. Level 3 provides comprehensive line-item detail. Level 3 processing data is similar to the information on an itemized invoice, requiring greater system capability. For more information, see [Level 3 data](https://docs.clover.com/docs/understanding-level-3-data).

> 📘 NOTE
> 
> Level 2 and Level 3 card payment features are currently available only for Mastercard<sup>®</sup> and Visa<sup>®</sup> in the United States (US).

## Check if a merchant is set up for purchase cards

For Clover merchants that accept purchase cards, you can include the `level2` and `level3` objects when creating charges or paying for orders. To check if a merchant is set up for purchase cards, send a GET request to the `/v3/merchants/{mId}/ecomm_payment_configs` endpoint. In the response, check that the `purchase_card.supported` value is `true`.

```curl
curl --request GET \
  --url 'https://sandbox.dev.clover.com/v3/merchants/ecomm_payment_configs' \
  --header 'accept: application/json'
```
```json
{
  "purchase_card": {
    "supported": true,
  }
  ...
}
```

If a merchant is not configured for purchasing cards, the transaction is still processed, but any data passed in the `level2` object is ignored, and the following warning message is returned:  
`Purchase card Level2 Data disregarded, merchant account does not support purchase cards`.

## Set level 2 data in a charge request

In the request body, set the required `amount` (in cents), `source`, and `currency`. When using a purchasing card, set the required fields in the `level2` object. See the [Create a charge](ref:createcharge) for a list of possible fields that you can set.

```json
{
  "amount": 33400,
  "currency": "usd",
  "source": "clv_1TSTA399021D...",
  "level2": {
    "tax_amount": 2353,
    "tax_indicator": 1,
    "pc_order_number": "21-200394",
    "discount_amount": 2200,
    "freight_amount": 37500,
    "duty_amount": 0,
    "destination_postal_code": "80919",
    "shipping_from_postal_code": "94145",
    "destination_country_code": 840,
    "product_description": "",
    "merchant_tax_id": ""
  }
}
```

> 📘 NOTE
> 
> Processing the level 2 data included with purchase cards depends on upstream systems being available when creating a payment. If a system is unavailable, the transaction is processed as a normal credit card payment and the following warning is returned:  
> `Purchase card Level2 Data disregarded, purchase card support is currently unavailable`.

<!--

 

hidden-text

- <br />

## Set level 3 data in a charge request

See the following subsection to set the required fields for the `level3` object. See the [Configure L3 parameters](doc:configuring-l3-parameters) for a list of possible fields that you can set.

```json
{

  
  }
}
```

- <br />

\-->

## Get data for a charge

If a charge includes level 2 or level 3 data, you can retrieve these details using the [Get a single payment](https://docs.clover.com/reference/paygetpayment) endpoint. To view the purchase-card-related information in the response `purchaseCardL2` object, add the `purchaseCardL2` expansion.

```curl
curl --request GET \
  --url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/payments/{paymentId}?expand=purchaseCardL2' \
  --header 'Accept: application/json'
```
```json
{
  "id": "HBQ8V3PZH481E",
  "amount": 808
  "purchaseCardL2": {
    "taxIndicator": "NON_TAXABLE",
    "purchaseIdentifier": "19873208776",
    "discountAmount": 2200,
    "freightAmount": 30000,
    "dutyAmount": 333,
    "destinationPostalCode": "80919",
    "shipFromPostalCode": "80903",
    "destinationCountryCode": "840",
    "merchantTaxId": "****0153",
    "productDescription": "Bike",
    "paymentRef": {
      "id": "HBQ8V3PZH481E"
    }
  }
}
```
