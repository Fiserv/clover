---
title: "(MSC Pilot) Manage service charges for Web apps"
slug: "msc-web-apps"
excerpt: "Learn how to use the MSC REST API to manage multiple service charges (MSC) for Web apps."
hidden: false
metadata: 
  description: "Learn how to use the multiple service charges (MSC) REST APIs to manage service charges for merchants and orders, including endpoints for creating, retrieving, adding, and removing service charges."
  image: []
  keywords: "multiple,service,charges,msc,REST,api"
  robots: "index"
createdAt: "Thu Feb 08 2024 17:23:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 26 2024 06:43:06 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Learn how to use the multiple service charges (MSC) REST APIs to manage service charges for merchants and orders, including endpoints for creating, retrieving, adding, and removing service charges.">

[block:html]
{
  "html": "<!--\n2024.Jul.7-10 (DS-6740) \n+added links to MSC Inventory and MSC Overview ref topics from the API Index\n+added No Tax note to MSC Orders API reference topic\n+added No Tax note (reusable) to MSC Web apps topic -cd\n\n2024.Mar.25: \n+Simplified hiererchy for pilot: \n\t++ merged Merchant-level and Order-level sub-topics into one topic with mini right-nav toc \n\n2024.Mar.20:(DS-6114)\n+reorganized MSC Pilot topics and added top nav  cd \n  ++moved all order-level APIs into one topic -cd\n  ++moved all merchant-level APIs into one topic -cd \n\n2024.Jan.10: (DS-5469)\n+New topic -cd\n-->\n<!-- Jul-15-2024 editorial review (DS-6647) Aneesha -->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]{"html":"<!--Add a top nav throughout the pilot doc content (v2.2: grayscale, no overlap)-->\n<div><!--div set-->\n <div class=\"top-container\">\n    <div class=\"topnav\">\n      <a href=\"https://docs.clover.com/docs/msc-overview\">MSC overview</a>\n      <a href=\"https://docs.clover.com/docs/msc-set-up-and-test-your-app\">MSC set up and test</a>\n      <a href=\"https://docs.clover.com/docs/msc-android-apps\">MSC for Android apps</a>\n      <a href=\"https://docs.clover.com/docs/msc-web-apps\">MSC for Web apps</a>\n      <a href=\"https://docs.clover.com/reference/msc-apiref-index\">MSC REST API index</a>\n      <a href=\"https://docs.clover.com/docs/msc-faqs\">MSC FAQ</a>\n    </div><!--end topnav-->\n  </div><!--end top-container-->\n</div>\n\n<!--css-->\n<style>\n/* Add a background color to the top navigation */\n.topnav {\n  font-family: 'Graphik-Regular', sans-serif;\n  background-color: #5D5D5D;\n  overflow: hidden;\n}\n\n/* Style the links inside the navigation bar */\n.topnav a {\n  font-family: 'Graphik-Regular', sans-serif;\n  float: left;\n  color: #f2f2f2;\n  text-align: center;\n  padding: 10px 12px;\n  text-decoration: none;\n  font-size: 12px;\n}\n\n/* Change the color of links on hover */\n.topnav a:hover {\n  background-color: #D8D8D8;\n  color: black;\n}\n\n/* Add a color to the active/current link */\n.topnav a.active {\n  background-color: #5D5D5D;\n  color: white;\n}\n</style>"}[/block]

This topic describes how to use the MSC REST API to manage multiple service charges (MSC) for Web apps. The endpoints are organized into two sections for merchant-level and order-level endpoints:

[block:parameters]
{
  "data": {
    "h-0": "REST APIs to manage service charges",
    "h-1": "Description",
    "0-0": "[Merchant-level REST API endpoints](https://docs.clover.com/docs/msc-web-apps#merchant-level-rest-api-endpoints)",
    "0-1": "Use to:  \n  \n- Get a list of all service charges  \n- Get details for single service charge",
    "1-0": "[Order-level REST API endpoints](https://docs.clover.com/docs/msc-web-apps#order-level-rest-api-endpoints)",
    "1-1": "Use to:  \n  \n- Add one or more service charges associated with a merchant to a given order  \n- Remove one or more service charges associated with a merchant from an order  \n- Get a single service charge associated with an order  \n- Get the list of service charges associated with a given ord"
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
> To access the complete, testable MSC REST API reference endpoints, see the [MSC REST API Index](https://docs.clover.com/reference/msc-apiref-index).

***

# Merchant-level REST API endpoints

## 1. Get service charges associated with a merchant

Use the `v3/merchants/{mId}/order_fees` endpoint to:

- get a list of all service charges 
- get a single charge associated with a merchant

### 1.1 Get a list of all service charges

1. Send a **GET** request to `v3/merchants/{mId}/order_fees`. 
2. Enter the merchant identifier (`mId`) in the request. 

```curl Request
curl --request GET  \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/order_fees' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```
```json Response
{
    "elements": [
        {
            "id": "DPDDK16CGET6E",
            "name": "StaffMed",
            "percentage": 1000,
            "createdTime": 1705681517000,
            "modifiedTime": 1705681517000
        },
        {
            "id": "7QC732JVN2DXP",
            "name": "Delivery",
            "percentage": 40000,
            "createdTime": 1705029883000,
            "modifiedTime": 1705029883000,
            "type": ""
        },
        {
            "id": "HHBECXV21DRQ4",
            "name": "LargeParty",
            "percentage": 30000,
            "createdTime": 1704480354000,
            "modifiedTime": 1705360002000,
            "type": ""
        }
    ],
    "href": "/v3/merchants/HDHEQBN4ARCF5/order_fees"
}
```

#### Request parameters

[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Type",
    "h-2": "Description",
    "h-3": "Required/ Optional",
    "0-0": "`mId`",
    "0-1": "string",
    "0-2": "Merchant identifier.",
    "0-3": "Required",
    "1-0": "`Query filter`",
    "1-1": "string",
    "1-2": "Filter fields:  \n  \n- modifiedTime  \n- amount  \n- serviceChargeUuid  \n- type  \n- percentage  \n- name  \n- createdTime  \n- id  \n- deletedTime",
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


#### Response parameters

| Property       | Type    | Description                                          |
| :------------- | :------ | :--------------------------------------------------- |
| `id`           | string  | Service charge identifier.                           |
| `name`         | string  | Service charge name.                                 |
| `percentage`   | integer | Service charge amount in percent.                    |
| `createdTime`  | integer | Timestamp when the order fee was created.            |
| `modifiedTime` | integer | Timestamp when the service charge was last modified. |

### 1.2 Get details for a single service charge

1. Send a **GET** request to `v3/merchants/{mId}/order_fees/{orderFeeId}`. 
2. Enter the merchant identifier (`mId`) and the order fee identifier (`orderFeeId`) in the request.

```curl Request
curl --request GET  \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/order_fees/{orderFeeId}' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```
```json Response
{
    "id": "HHBECXV21DRQ4",
    "name": "LargeParty",
    "percentage": 30000,
    "createdTime": 1704480354000,
    "modifiedTime": 1705360002000,
    "type": ""
}
```

#### Request parameters

| Property     | Type   | Description           | Required/ Optional |
| :----------- | :----- | :-------------------- | :----------------- |
| `mId`        | string | Merchant identifier.  | Required           |
| `orderFeeId` | string | Order fee identifier. | Required           |

#### Response parameters

| Property       | Type    | Description                                              |
| :------------- | :------ | :------------------------------------------------------- |
| `id`           | string  | Order fee identifier.                                    |
| `name`         | string  | Service charge (order fee) name.                         |
| `percentage`   | integer | Service charge amount in percent.                        |
| `createdTime`  | integer | Time when the service charge was recorded on the server. |
| `modifiedTime` | integer | Time when the service charge was modified on the server. |

***

# Order-level REST API endpoints

## 1. Use  the `isOrderFee` object flag to control where service charges appear

At the API level, service charges are handled as line items (of _service charge_ type). However, in your app interface, service charges should not display with the line items—they should be listed after the subtotal because taxes are not applied to service fees.  

You can control the placement of service charges in your app interface using the `isOrderFee` object flag.

- For regular (non-service charge) lineItems the `LineItem` object flag is set to `isOrderFee`: **false**.
- When using `orderFeeLineItem `, set the `LineItem` object flag to `isOrderFee`: **true**. 

Make sure the response for the service charges found indicates `isOrderFee`: **true**.  
For example:

```Text Example response to get order fee line item
{
"id": "S4XK3VG1RXK1C",
"orderRef": {
"id": "P6JVBY8V8KFEC"
},
"name": "test order fee 2",
"price": 0,
"note": "test note",
"printed": false,
"createdTime": 1709732377000,
"orderClientCreatedTime": 1709732166000,
"exchanged": false,
"refunded": false,
"isRevenue": false,
"percentage": 190000,
"orderFee": {
"id": "7M8463224GJ5R"
},
"isOrderFee": true

```

### Make service charges display in the correct location

1. For the regular order line items, **filter out **service charge line items using the `isOrderFee` : **false** object flag. 
2. For the post-subtotal item list, **include** service charges using the`isOrderFee` : **true** object flag.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2c76c4c-mscReceipts-compared.png",
        "",
        "illustration of receipts with service charges"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Illustration of correct and incorrect placement of service charges in an order receipt"
    }
  ]
}
[/block]


## 2. Get a list of service charges associated with an order

1. Send a **GET** request to the `v3/merchants/{mId}/orders/{orderId}/order_fee_line_items` endpoint.
2. Enter the merchant identifier (`mId`) and the order identifier (`orderId`) in the request.

```curl Request
curl --request GET  \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/order_fee_line_items' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```
```json Response
{
"elements": [
{
"id": "S4XK3VG1RXK1C",
"orderRef": {
"id": "P6JVBY8V8KFEC"
},
"name": "order fee",
"price": 10,
"note": "test note",
"printed": false,
"createdTime": 1709732377000,
"orderClientCreatedTime": 1709732166000,
"exchanged": false,
"refunded": false,
"isRevenue": false,
"percentage": 190000,
"orderFee": {
"id": "7M8463224GJ5R"
},
"isOrderFee": true
}
],
"href": "http://sandbox.dev.clover.com/v3/merchants/{mid}/orders/{orderId}/order_fee_line_items?limit=100"
}
```

#### Request parameters

[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Type",
    "h-2": "Description",
    "h-3": "Required/ Optional",
    "0-0": "`mId`",
    "0-1": "string",
    "0-2": "Merchant identifier.",
    "0-3": "Required",
    "1-0": "`orderId`",
    "1-1": "string",
    "1-2": "Order identifier.",
    "1-3": "Required",
    "2-0": "`Expand query`",
    "2-1": "string",
    "2-2": "Expandable fields:  \n  \n- employee  \n- order type  \n- payments",
    "2-3": "Optional"
  },
  "cols": 4,
  "rows": 3,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


#### Response  parameters

| Parameter                | Type    | Description                                                                        |
| :----------------------- | :------ | :--------------------------------------------------------------------------------- |
| `id`                     | string  | Merchant identifier.                                                               |
| `orderRefid`             | string  | Reference identifier of the order fee with which the service charge is associated. |
| `name`                   | string  | Name of the order fee.                                                             |
| `price`                  | integer | Order fee price.                                                                   |
| `note`                   | string  | Comments or information, if any.                                                   |
| `createdTime`            | integer | Time when the service charge was recorded on the server.                           |
| `orderClientCreatedTime` | integer | Order client-created time for user data of line item.                              |
| `percentage`             | integer | Service charge amount in percent.                                                  |
| `orderFeeid`             | string  | Order fee identifier.                                                              |

## 3. Add service charges associated with a merchant to an order

> 📘 NOTE
> 
> **No tax on order fees**—Since MSC order fees are treated as line items, and order fees are non-taxed items, you must mark each order fee line item as a **0% No Tax Applied** tax.
> 
> For more information, see [Tax report example 5: zero tax](https://docs.clover.com/docs/tax-reports-examples#example-5-items-with-zero-tax-or-merchants-are-tax-exempt).

To add one or more service charges associated with a merchant to an order:

1. Send a **POST** request to `/v3/merchants/{mId}/orders/{orderId}/order_fee_line_items`. 
2. Enter the merchant identifier (`mId`) and order identifier (`orderId`) in the request.

```curl Request
curl --request POST  \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/order_fee_line_items'/
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```
```json Response
{
"id": "S4XK3VG1RXK1C",
"orderRef": {
"id": "P6JVBY8V8KFEC"
},
"name": "test order fee 2",
"price": 0,
"note": "test note",
"printed": false,
"createdTime": 1709732377000,
"orderClientCreatedTime": 1709732166000,
"exchanged": false,
"refunded": false,
"isRevenue": false,
"percentage": 190000,
"orderFee": {
"id": "7M8463224GJ5R"
},
"isOrderFee": true
}
}
```

#### Request parameters

| Parameter | Description          | Required/ Optional |
| :-------- | :------------------- | :----------------- |
| `mId`     | Merchant identifier. | Required           |
| `orderId` | Order identifier.    | Required           |

#### Response parameters

| Parameter                | Type    | Description                                                                       |
| :----------------------- | :------ | :-------------------------------------------------------------------------------- |
| `id`                     | string  | Merchant identifier.                                                              |
| `orderRefid`             | string  | Reference identifier of the order fee with which the service charge is associated |
| `name`                   | string  | Name of the order fee.                                                            |
| `price`                  | integer | Order fee price.                                                                  |
| `note`                   | string  | Comments or information, if any.                                                  |
| `createdTime`            | integer | Time when the service charge was recorded on the server.                          |
| `orderClientCreatedTime` | integer | Order client-created time for user data of line item.                             |
| `percentage`             | integer | Service charge amount in percent.                                                 |
| `orderFeeid`             | string  | Order fee identifier.                                                             |

## 4. Remove service charges associated with a merchant from an order

To remove one or more service charges associated with a merchant from an order:

1. Send a **DELETE ** request to `/v3/merchants/{mId}/orders/{orderId}/order_fee_line_items/{orderFeeLineItemId}`. 
2. Enter the merchant identifier (`mId`), order identifier (`orderId`) and the order fee line item identifier (`orderFeeLineitemId`) in the request.

```curl Request
curl --request DELETE  \
--url 'https://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/order_fee_line_items/{orderFeeLineItemId}' \
--header 'content-type: application/json' \
--header 'Authorization: Bearer {access_token}'
```

#### Request parameters

| Parameter            | Type   | Description                     | Required/ Optional |
| :------------------- | :----- | :------------------------------ | :----------------- |
| `mId`                | string | Merchant identifier.            | Required           |
| `orderId`            | string | Order identifier.               | Required           |
| `orderFeeLineItemId` | string | Order fee line item identifier. | Required           |

#### Response parameters

| Message | Type   | Description                                     |
| :------ | :----- | :---------------------------------------------- |
| `200`   | string | Successful response. Service charge is deleted. |
