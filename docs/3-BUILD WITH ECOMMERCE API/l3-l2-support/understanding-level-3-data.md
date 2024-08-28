---
title: "Level 3 data"
slug: "understanding-level-3-data"
excerpt: ""
hidden: false
metadata: 
  description: "Level 3 data is recommended for large corporations processing a majority of B2B (business-to-business) and B2G (business-to-government) transactions. These transactions require providing the most data at the time of the transaction. Only Mastercard and Visa qualify for Level 3 data processing."
  image: []
  robots: "index"
createdAt: "Tue May 31 2022 23:23:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:22:51 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# Understand Level 3 data

Level 3 data is recommended for large corporations processing most B2B (business-to-business) and B2G (business-to-government) transactions. These transactions require providing the most data at the time of the transaction. Only Mastercard<sup>®</sup> and Visa<sup>®</sup> qualify for Level 3 data processing.

## Endpoints

See the following endpoint when configuring L3 data: [Create a charge](https://docs.clover.com/reference/createcharge).

## Collected data

In addition to tax amounts and customer codes ([Level 2 data](https://docs.clover.com/docs/understanding-level-2-data)), Level 3 data includes item information such as product, code, item quantity, description, unit of measure, unit cost, and more. Different data is collected based on whether the card is Mastercard or Visa. You can add default values for Level 3 data when you set up purchasing card payments on the web dashboard. This data is auto-populated during the transaction. 

## Issuer requirements

In addition to Level 2 data requirements, businesses interested in Level 3 data processing need to submit additional details. For example, Visa requires companies to have between 20,000 and 1 million in e-commerce transactions. These accounts are attractive to fraudsters and identity thieves, making them some of the most expensive credit cards to accept.

### Level 3 data requirements

The following fields are part of the Level 3 data collected for Mastercard and Visa, in addition to the [Level 2](doc:understanding-level-2-data) fields:

[block:parameters]
{
  "data": {
    "h-0": "Object",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "`service_code`",
    "0-1": "string",
    "0-2": "Service code is extracted from the track data. This is required for swiped transactions and is mandatory for all non-keyed transactions.  \n**Note: **Track data is information encoded within the magnetic strip on the back of a credit card that is read by the electronic reader within the terminal or point-of-sale (POS) system.",
    "1-0": "`magnetic_Stripe_Ind`",
    "1-1": "boolean",
    "1-2": "Set to `true` for magnetic stripe-swiped transactions.",
    "2-0": "`level3_line_items`",
    "2-1": "array of objects",
    "2-2": "List of Level 3 line items. See the following table."
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


### Level 3 line items requirements

The following fields are part of the Level 3-line item parameters:

| Object             | Type    | Description                                                                                                                                                                                            |
| :----------------- | :------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `item_description` | string  | Item description for Level 3 line item. Format: Cannot be all spaces or 0s (zeros). The last four digits are implied decimal places, for example: 20.0000.                                             |
| `product_code`     | string  | Required for Mastercard and Visa. Indicates a product or universal product code (UPC). Format: Cannot be all spaces.                                                                                   |
| `unit_cost`        | int64   | Unit cost for Level 3 line item. Format: Visa - Not all spaces or zeros (0s).                                                                                                                          |
| `quantity`         | decimal | Item quantity. Format:  Not all spaces or zeros (0s). Required for reduced interchange. Last four digits are considered decimal places.                                                                |
| `discount_amount`  | int64   | Discount amount applied to level 3-line items. For Visa level 3, this cannot be all zeroes if a discount exists. Also, the last two digits are implied decimal places. Otherwise, it must be zero (0). |
| `unit_of_measure`  | string  | Required for both Mastercard and Visa for reduced interchange. See [Units of measurement codes](doc:units-of-measurement-codes).                                                                       |
| `commodity_code`   | string  | Required for Visa. Indicates the classification of items purchased.                                                                                                                                    |

## Credit card parameters

The following table provides parameters for a specific credit card:

| Card issuer | Description                                                                                                                                                               |
| :---------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Mastercard  | - `item_description` (required) - `product_code` (required) - `unit_of_measure` (required) - `quantity` (required) - `unit_cost` (required)                               |
| Visa        | - `commodity_code` (required) - `product_code` (required) - `unit_of_measure` (required) - `item_description` (required) - `quantity` (required) - `unit_cost` (required) |
