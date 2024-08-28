---
title: "Capture charge for split shipment"
slug: "capture-charge-for-split-shipment"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to capture a charge for split shipment."
  image: []
  robots: "index"
createdAt: "Thu Jul 13 2023 11:03:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n  <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


A split shipment is when a single order containing multiple products is sent in separate shipments due to product availability or sizing issues. The multi-capture feature allows merchants to split any payment into several captures initiated from a single authorization within a specified time frame. The pre-auth period for a split shipment depends on the card type.

To use the split-shipment feature, merchants need to contact the merchant help desk to get access to multi-capture setting on the Merchant dashboard. Once the support team provides access, merchants can enable or disable this feature from the **Merchant Web Dashboard → Account & Setup → Ecommerce Payments → Multi-Capture**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4b5dbd5-split_shipment.png",
        "",
        ""
      ],
      "align": "center",
      "sizing": "600px"
    }
  ]
}
[/block]


**Note: **The split-shipment feature is enabled globally in the sandbox environment for the test merchants to test the feature.

The `split_shipment` field in the  [Capture a charge](https://docs.clover.com/reference/capturecharge) endpoint allows you to capture a single pre-authorization multiple times. When you enter information in the field, a separate capture request is sent for shipment. See [Create pre-authorization](https://docs.clover.com/docs/create-pre-authorization) for more information.

> 📘 Note
> 
> Tips are charged with the first split-shipment amount. However, taxes and the surcharge are charged on a prorated basis for each split shipment.

## Path Parameters

Path parameter to use when capturing a charge for split shipment:

| Object     | Type   | Description                                         | Required |
| :--------- | :----- | :-------------------------------------------------- | :------- |
| `chargeId` | string | Universally unique identifier (UUID) of the charge. | Required |

## Body parameters

Body parameters to use when capturing a charge:

[block:parameters]
{
  "data": {
    "h-0": "Object",
    "h-1": "Type",
    "h-2": "Description",
    "h-3": "Required",
    "0-0": "`amount`",
    "0-1": "int64",
    "0-2": "Charge amount in the smallest monetary unit of the merchant's currency. If you do not specify an amount, the total of the original charge is captured.  \nFormat: Cents",
    "0-3": "Required",
    "1-0": "`split-shipment`",
    "1-1": "string",
    "1-2": "Provides partial shipment information for a single pre-authorization.  \nValues: 1 to 99  \nFormat: n/m; where,  \n- n is the the current shipment. The value begins by 1 and increments by 1 with each subsequent shipment.  \n- m is the total number of shipments. Default: 99  \nExample: If total shipments in a transaction are 5, then the last shipment will be 5/5.",
    "1-3": "Required"
  },
  "cols": 4,
  "rows": 2,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Create split shipment

1. Create preauth using `v1/charges/`. See [Create pre-authorization](https://docs.clover.com/docs/create-pre-authorization).
2. Send a `POST` request to `/v1/charges/{{charge_id}}/capture`.

**Example:**

```json JSON request
POST /v1/charges/{{charge_id}}/capture
{
    "amount": "150",
    "split_shipment": "1/3"
```
```json JSON response
{
    "id": "1AB2CDEF3G4H",
    "amount": 150,
    "payment_method_details": "card",
    "currency": "usd",
    "created": 1656626930000,
    "description": "this is split shipment",
    "captured": true,
    "ref_num": "316300528100",
    "auth_code": "723015",
    "order": "KQ2J82T5ZCYEM",
    "outcome": {
        "network_status": "approved_by_network",
        "type": "authorized"
    },
    "paid": true,
    "status": "succeeded",
    "source": {
        "id": "clv_1ABCD23efghI45JklmN6o7p",
        "brand": "MC",
        "first6": "123456",
        "last4": "1234"
    }
}
```

## Cancel the balance from the pre-authorization

Send a `PUT` request to `v1/charges/{{charge_id}}` to make the adjustment call to release the remaining balance from the pre-auth.

**Example:** The original pre-auth is for $10.00, and the first split shipment was captured for $4.40. The PUT call immediately releases the remaining balance ($5.60). 

```json JSON request
PUT v1/charges/{{charge_id}}
{
    "amount": "440"
}
```
```json JSON response
{
    "id": "94V2KC7YASTE2",
    "amount": 150,
    "payment_method_details": "card",
    "currency": "usd",
    "created": 1686587177000,
    "description": "this is split shipment",
    "captured": true,
    "ref_num": "316300528100",
    "auth_code": "723015",
    "order": "KQ2J82T5ZCYEM",
    "outcome": {
        "network_status": "reversed_after_approval"
    },
    "paid": true,
    "status": "succeeded",
    "source": {
        "id": "clv_1ABCD23efghI45JklmN6o7p",
        "brand": "MC",
        "first6": "518701",
        "last4": "2435"
    },
    "amount_captured": 1150
}
```
