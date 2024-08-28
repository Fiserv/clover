---
title: "Funding API—appendix"
slug: "funding-api-description"
excerpt: ""
hidden: false
metadata: 
  description: "This appendix contains information on Funding API descriptions, data mapping, and category codes."
  image: []
  robots: "index"
createdAt: "Wed Apr 06 2022 15:51:12 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 06 2024 00:14:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


This appendix has the following information:

- [API descriptions](doc:funding-api-description#API-descriptions)
- [Data mapping](doc:funding-api-description#data-mapping)
- [Category codes](doc:funding-api-description#category-codes)

# API descriptions

The following section lists and defines the Funding API parameters.

| Parameter                        | Type   | Description                                                                                       |
| :------------------------------- | :----- | :------------------------------------------------------------------------------------------------ |
| `dateFunded`                     | Long   | Date the money was deposited.                                                                     |
| `startDate`                      | Long   | Start date of report.                                                                             |
| `endDate`                        | Long   | End date of report.                                                                               |
| `amountSubmitted`                | Long   | All deposits (+) less any debits (-).                                                             |
| `amountTransferred`              | Long   | Amount submitted. This includes fees, adjustments (+/-), charge backs, and reversals.             |
| `paidByOthers`                   | Long   | Funded outside of Fiserv.                                                                         |
| `transfers`                      | Long   | Number of transfers.                                                                              |
| `feesDetails.name`               | String | Name of fee.                                                                                      |
| `feesDetails.majorCatCode`       | String | Fee details code.                                                                                 |
| `feesDetails.amount`             | Long   | Dollar amount of the fee.                                                                         |
| `feesDetails.count`              | Long   | The number of this type of fee.                                                                   |
| `feesDetails.categoryKey`        | String | Used to show the category of `fees` using a key in the Clover namespace.                          |
| `chargeBackDetails.name`         | String | Name of charge back.                                                                              |
| `chargeBackDetails.majorCatCode` | Long   | Charge back details code.                                                                         |
| `chargeBackDetails.amount`       | Long   | Dollar amount for a charge back.                                                                  |
| `chargeBackDetails.count`        | Long   | Number of charge backs/reversals.                                                                 |
| `chargeBackDetails.categoryKey`  | String | Displays the category of `chargeBack` using a key in a Clover namespace.                          |
| `taxDetails.name`                | String | Name of the tax (for example, `IGST`, `CGST`, `SGST`).                                            |
| `taxDetails.majorCatCode`        | String | Indicates a category code. Refer to [Category codes](doc:funding-api-description#category-codes). |
| `taxDetails.amount`              | Long   | Always `INR`.                                                                                     |
| `taxDetails.count`               | Long   | Indicates the number of tax transactions.                                                         |
| `taxDetails.categoryKey`         | String | Displays a category of tax using a key in a Clover namespace.                                     |
| `cardTypes.name`                 | String | Name of the card network.                                                                         |
| `cardTypes.amount`               | Long   | Dollar amount.                                                                                    |
| `cardTypes.productCode`          | String | Product code.                                                                                     |

# Data mapping

## Card types

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Value Description",
    "h-2": "Region",
    "0-0": "0",
    "0-1": "OTHER",
    "0-2": "US",
    "1-0": "1",
    "1-1": "MASTERCARD<sup>®</sup>",
    "1-2": "US",
    "2-0": "2",
    "2-1": "VISA<sup>®</sup>",
    "2-2": "US",
    "3-0": "3",
    "3-1": "DISCOVER<sup>®</sup>",
    "3-2": "US",
    "4-0": "4",
    "4-1": "PRIVATE LABEL",
    "4-2": "US",
    "5-0": "5",
    "5-1": "AMEX<sup>®</sup>",
    "5-2": "US",
    "6-0": "6",
    "6-1": "JAPANESE CR BUR",
    "6-2": "US",
    "7-0": "7",
    "7-1": "AMEX ACQ",
    "7-2": "US",
    "8-0": "8",
    "8-1": "SIZES UNLIMITED",
    "8-2": "US",
    "9-0": "9",
    "9-1": "VOYAGER",
    "9-2": "US",
    "10-0": "10",
    "10-1": "DEBIT CARD",
    "10-2": "US",
    "11-0": "11",
    "11-1": "JBS",
    "11-2": "US",
    "12-0": "12",
    "12-1": "TELECHECK",
    "12-2": "US",
    "13-0": "13",
    "13-1": "CHECK WARRANTY",
    "13-2": "US",
    "14-0": "14",
    "14-1": "SWITCH DEBIT",
    "14-2": "US",
    "15-0": "15",
    "15-1": "PURCHASING CARD",
    "15-2": "US",
    "16-0": "16",
    "16-1": "EBT",
    "16-2": "US",
    "17-0": "17",
    "17-1": "GATEWAY DEBIT CARD",
    "17-2": "US",
    "18-0": "18",
    "18-1": "STORED VALUE FUNDED",
    "18-2": "US",
    "19-0": "19",
    "19-1": "STORED CARD VALUE",
    "19-2": "US",
    "20-0": "20",
    "20-1": "PRIVATE LBL GEN",
    "20-2": "US",
    "21-0": "21",
    "21-1": "WEX",
    "21-2": "US",
    "22-0": "22",
    "22-1": "REWDS/REDM",
    "22-2": "US",
    "23-0": "23",
    "23-1": "FLEETCAR",
    "23-2": "US",
    "24-0": "24",
    "24-1": "FLEET ONE",
    "24-2": "US",
    "25-0": "25",
    "25-1": "BML",
    "25-2": "US",
    "26-0": "26",
    "26-1": "APM",
    "26-2": "US",
    "27-0": "27",
    "27-1": "PAYPAL",
    "27-2": "US",
    "28-0": "28",
    "28-1": "MAESTRO",
    "28-2": "US",
    "29-0": "29",
    "29-1": "VPAY",
    "29-2": "US",
    "30-0": "30",
    "30-1": "INTERNATIONAL MAESTRO",
    "30-2": "US",
    "31-0": "31",
    "31-1": "VISA ELECTRON SIG",
    "31-2": "US",
    "32-0": "32",
    "32-1": "VISA DEBIT",
    "32-2": "US",
    "33-0": "33",
    "33-1": "VISA PURCHASING",
    "33-2": "US",
    "34-0": "34",
    "34-1": "VISA DEBIT CHIP",
    "34-2": "US",
    "35-0": "35",
    "35-1": "VISA CHIP",
    "35-2": "US",
    "36-0": "36",
    "36-1": "MASTERCARD CONSUMER",
    "36-2": "US",
    "37-0": "37",
    "37-1": "MASTERCARD CHIP",
    "37-2": "US",
    "38-0": "38",
    "38-1": "MASTERCARD PURCHASING",
    "38-2": "US",
    "39-0": "39",
    "39-1": "MASTERCARD DEBIT",
    "39-2": "US",
    "40-0": "40",
    "40-1": "DINERS",
    "40-2": "US",
    "41-0": "41",
    "41-1": "MASTERCARD DEBIT CHIP",
    "41-2": "US",
    "42-0": "42",
    "42-1": "TELECREDIT",
    "42-2": "US",
    "43-0": "43",
    "43-1": "EUROPAY",
    "43-2": "US",
    "44-0": "44",
    "44-1": "DINERS CLUB",
    "44-2": "US",
    "45-0": "45",
    "45-1": "JCB",
    "45-2": "US",
    "46-0": "46",
    "46-1": "MDS",
    "46-2": "US",
    "47-0": "47",
    "47-1": "STAR",
    "47-2": "US",
    "48-0": "48",
    "48-1": "AUS DOM DEBIT",
    "48-2": "US",
    "49-0": "49",
    "49-1": "CUP",
    "49-2": "US",
    "50-0": "50",
    "50-1": "ELV",
    "50-2": "US",
    "51-0": "51",
    "51-1": "GOOGLE",
    "51-2": "US",
    "52-0": "52",
    "52-1": "AUSTRIA DD",
    "52-2": "US",
    "53-0": "53",
    "53-1": "FRANCE DD",
    "53-2": "US",
    "54-0": "54",
    "54-1": "ITALY DD",
    "54-2": "US",
    "55-0": "55",
    "55-1": "BELGIUM DD",
    "55-2": "US",
    "56-0": "56",
    "56-1": "RTBT GERMANY",
    "56-2": "US",
    "57-0": "57",
    "57-1": "RTBT NETHERLANDS",
    "57-2": "US",
    "58-0": "58",
    "58-1": "BANKSERV MC",
    "58-2": "US",
    "59-0": "59",
    "59-1": "BANKSERV VISA",
    "59-2": "US",
    "60-0": "60",
    "60-1": "BANKSERV DINERS",
    "60-2": "US",
    "61-0": "61",
    "61-1": "ONUS",
    "61-2": "US",
    "62-0": "62",
    "62-1": "MISCELLANEOUS",
    "62-2": "US",
    "63-0": "63",
    "63-1": "BLACKHAWK",
    "63-2": "US",
    "64-0": "64",
    "64-1": "EWIC",
    "64-2": "US",
    "65-0": "65",
    "65-1": "OTHERS",
    "65-2": "US",
    "66-0": "66",
    "66-1": "SVS GIFT CARDS",
    "66-2": "US",
    "67-0": "67",
    "67-1": "VALUELINK",
    "67-2": "US",
    "68-0": "68",
    "68-1": "FUELMAN",
    "68-2": "US",
    "69-0": "69",
    "69-1": "SUPERVALU HOUSE CHAR",
    "69-2": "US",
    "70-0": "70",
    "70-1": "ULTRA DIAMOND SHAMRO",
    "70-2": "US",
    "71-0": "71",
    "71-1": "LOCAL DOMESTIC VISA",
    "71-2": "US",
    "72-0": "72",
    "72-1": "LOCAL DOMESTIC MASTERCARD",
    "72-2": "US",
    "73-0": "73",
    "73-1": "CASH ADVANCE VISA",
    "73-2": "US",
    "74-0": "74",
    "74-1": "CASH ADVANCE MASTERCARD",
    "74-2": "US",
    "75-0": "75",
    "75-1": "CASH ADVANCE DISCOVER",
    "75-2": "US",
    "76-0": "76",
    "76-1": "CASH ADVANCE LOCAL PAPER VISA",
    "76-2": "US",
    "77-0": "77",
    "77-1": "CASH ADVANCE LOCAL PAPER MASTERCARD",
    "77-2": "US",
    "78-0": "78",
    "78-1": "VISA DCC",
    "78-2": "US",
    "79-0": "79",
    "79-1": "MASTERCARD DCC",
    "79-2": "US",
    "80-0": "80",
    "80-1": "VISA PASS THRU",
    "80-2": "US",
    "81-0": "81",
    "81-1": "VISA LOCAL TRANS",
    "81-2": "US",
    "82-0": "82",
    "82-1": "MASTERCARD LOCAL TRANS",
    "82-2": "US",
    "83-0": "83",
    "83-1": "VISA INTL DEBIT",
    "83-2": "US",
    "84-0": "84",
    "84-1": "VISA LOCAL PAPER DEBIT",
    "84-2": "US",
    "85-0": "85",
    "85-1": "MASTERCARD INTL DEBIT",
    "85-2": "US",
    "86-0": "86",
    "86-1": "MASTERCARD LOCAL PAPER DEBIT",
    "86-2": "US",
    "87-0": "87",
    "87-1": "PRI-VAL",
    "87-2": "US",
    "88-0": "88",
    "88-1": "VISA SIG DEBIT",
    "88-2": "US",
    "89-0": "89",
    "89-1": "VISA SIG DEBIT LOCAL",
    "89-2": "US",
    "90-0": "90",
    "90-1": "VISA SIG DEBIT CASH ADVANCE",
    "90-2": "US",
    "91-0": "91",
    "91-1": "MASTERCARD SIG DEBIT",
    "91-2": "US",
    "92-0": "92",
    "92-1": "MASTERCARD SIG DEBIT LOCAL",
    "92-2": "US",
    "93-0": "93",
    "93-1": "MC SIG DEBIT CASH ADVANCE",
    "93-2": "US",
    "94-0": "94",
    "94-1": "VISA MOB CREDIT LOCAL",
    "94-2": "US",
    "95-0": "95",
    "95-1": "MASTERCARD MOB CREDIT LOCAL",
    "95-2": "US",
    "96-0": "96",
    "96-1": "MOBILE DDA",
    "96-2": "US",
    "97-0": "97",
    "97-1": "UPI DEBIT",
    "97-2": "US",
    "98-0": "98",
    "98-1": "UPI CREBIT",
    "98-2": "US"
  },
  "cols": 3,
  "rows": 99,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Category codes

```text
DEPOSITS("1")
ADJUSTMENTS("2","4","8","9","10","15")
FEES("6")
PROCESSING_SERVICE_CHARGES("11","13")
INTERCHANGE_CHARGES("7","14)
CHARGEBACKS("12")
REVERSALS("3")
```
