---
title: "Level 2 data"
slug: "understanding-level-2-data"
excerpt: ""
hidden: false
metadata: 
  description: "Level 2 card data is additional information attached to a credit card transaction."
  image: []
  robots: "index"
createdAt: "Tue May 31 2022 23:16:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:21:40 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# Understand Level 2 data

The Level 2 card data is additional information attached to a credit card transaction. It is recommended for established businesses with a requirement to process large volumes per transaction or a high number of transactions on a recurring basis.

## Endpoints

See the following endpoints when configuring Level 2 data:

- [Create a charge](https://docs.clover.com/reference/createcharge) 
- [Capture a charge](https://docs.clover.com/reference/capturecharge)

## Collected data

Along with Level 1 data, such as personal consumer card transaction data, Level 2 data includes tax amount, tax indicator, tax ID, customer code, and shipping information. Different data is collected based on whether the card is American Express<sup>®</sup>, Mastercard<sup>®</sup>, and Visa<sup>®</sup>. You can add default values for Level 2 data when you set up purchasing card payments on the Web Dashboard. This data is auto-populated during the transaction.

## Issuer requirements

Each issuing credit card company provides specific qualifying requirements. The credit card company accepts the enhanced Level 2 payment data only when the business meets the requirements.

### Level 2 data requirements

The following fields are part of the Level 2 data requirements:

[block:parameters]
{
  "data": {
    "h-0": "Object",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "`tax_amount`",
    "0-1": "int64",
    "0-2": "Part of the transaction amount that indicates the sales tax. A `pc_order_number` is required when including a `tax_amount`.",
    "1-0": "`tax_indicator`",
    "1-1": "integer",
    "1-2": "Taxable status of the transaction.  \nValues:  \n0 – No tax information provided  \n1 – Tax amount is provided  \n2 – Purchase item is tax exempt or non-taxable",
    "2-0": "`purchase_identifier`",
    "2-1": "string",
    "2-2": "Identifier, such as stock keeping unit (SKU), code or reference number that the merchant or customer uses to identify the purchase.",
    "3-0": "`pc_order_number`",
    "3-1": "string",
    "3-2": "Order number or customer reference number reported as part of the purchase card data.",
    "4-0": "`discount_amount`",
    "4-1": "int64",
    "4-2": "Discount amount for the transaction.  \nFormat: Cents",
    "5-0": "`freight_amount`",
    "5-1": "int64",
    "5-2": "Freight amount included for the transaction.  \nFormat: Cents",
    "6-0": "`duty_amount`",
    "6-1": "int64",
    "6-2": "Duty amount included for the transaction.  \nFormat: Cents",
    "7-0": "`destination_postal_code`",
    "7-1": "string",
    "7-2": "Postal or ZIP code of the delivery location.",
    "8-0": "`shipping_from_postal_code`",
    "8-1": "string",
    "8-2": "Postal or ZIP code of the shipping location.",
    "9-0": "`destination_country_code`",
    "9-1": "integer",
    "9-2": "Delivery location country code.  \nFormat: 3-digit code; see the [Country code reference](doc:country-code-reference) for a list of valid values.",
    "10-0": "`merchant_tax_id`",
    "10-1": "string",
    "10-2": "Only for Mastercard. Identifier (ID) for the tax collected by the merchant for the transaction.",
    "11-0": "`product_description`",
    "11-1": "string",
    "11-2": "Description of the purchased item."
  },
  "cols": 3,
  "rows": 12,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Credit card breakdown

The following table provides the parameters to use for a specific credit card.

| Card issuer         | General information                         |
| :------------------ | :------------------------------------------ |
| American Express    | - `product_description` - `discount_amount` |
| Mastercard and Visa | - `tax_amount` - `discount_amount`          |
