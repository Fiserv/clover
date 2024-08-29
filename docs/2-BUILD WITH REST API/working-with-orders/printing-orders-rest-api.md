---
title: "Print orders with the REST API"
slug: "printing-orders-rest-api"
excerpt: ""
hidden: false
metadata: 
  description: "You can print orders on a merchant's default printer using the `print_event` endpoint, and also customize order and payment receipts."
  image: []
  robots: "index"
createdAt: "Tue Jun 22 2021 19:14:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


## Watch the printing orders demo

Watch Clover's demo on how to print orders. Here's what you'll learn:

- Print orders on a merchant's default printer using the `print_event` endpoint
- Customize order and payment receipts

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FKkMtZhcXxJY%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DKkMtZhcXxJY&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FKkMtZhcXxJY%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=KkMtZhcXxJY&feature=youtu.be",
  "title": "Print with Clover's REST API",
  "favicon": "https://www.youtube.com/s/desktop/e90e8d8a/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/KkMtZhcXxJY/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=KkMtZhcXxJY&feature=youtu.be"
}
[/block]


## Print API endpoints

The Print API consists of two endpoints providing access to the printer on a merchant's device. Online ordering or other restaurant-related apps can build features that depend on the ability to print order receipts. The following endpoints can used to interact with the printer functions:

- `POST /v3/merchants/{mId}/print_event` (requires the [Write orders](https://docs.clover.com/docs/permissions#write-orders) permission)
- `GET /v3/merchants/{mId}/print_event/{eventId}` (requires the [Read orders](https://docs.clover.com/docs/permissions#write-orders) permission)

Your app may also need to use the `GET /v3/merchants/{mId}/orders` endpoint to get information about existing orders.

## Printing an order to the default firing device

To print an order, your app sends a POST request to the `/v3/merchants/{mId}/print_event` endpoint with a request body including the order ID.

```curl
curl --request POST \
  --url https://sandbox.dev.clover.com/v3/merchants/{mId}/print_event \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  --data '{"orderRef": {"id": "Y8TNWGTYHVP7G"}}'
```

This request is routed to the firing device's order printer or, if they don't have an order printer, to the firing device's onboard printer.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/76d01c7-PrintEventDataFlow.png",
        "PrintEventDataFlow.png",
        2323
      ],
      "caption": "Data flow for order printing"
    }
  ]
}
[/block]


The response includes the event `id`, the order being printed, the printer handling the request, as well as event state and time data.

```json
{
  "id": "P5WWTQ44VRY74",
  "orderRef": {
    "id": "4CZ8EH4BEKRXW"
  },
  "deviceRef": {
    "id": "926766ca-5636-8598-e959-6e3c6fe047e1"
  },
  "state": "CREATED",
  "createdTime": 1626454194000,
  "modifiedTime": 1626454194000,
  "printTime": 1626454194000
}
```

If you want to confirm that a print job is finished, your app should be [subscribed to the order event webhooks](https://docs.clover.com/docs/webhooks#subscribing-to-events). When an order is printed, Clover sets the `printed` property to `true` for each order line item. These line item updates are then sent to your app's callback URL as webhook messages.

## Getting the status of a recent print job

The `GET/v3/merchants/{mId}/print_event/{eventId}` endpoint returns information about a specific print job. Print jobs are short lived, so this endpoint only returns a response for jobs that are in the `CREATED`, `PRINTING`, or `FAILED` state. 

```curl
curl --request GET \
  --url https://sandbox.dev.clover.com/v3/merchants/{mId}/print_event/WNSZ2D0WX884W \
  --header 'Accept: application/json'
```
```json
{
  "id": "WNSZ2D0WX884W",
  "orderRef": {
    "id": "HQ6Q9WMX944SP"
  },
  "deviceRef": {
    "id": "926766ca-5636-8598-e959-6e3c6fe047e1"
  },
  "state": "PRINTING",
  "createdTime": 1626896196000,
  "modifiedTime": 1626896196000,
  "printTime": 1626896197000
}
```

Once a job is printed, the job is discarded and cannot be replayed. If you call this endpoint with the `eventId` of a job that has been successfully printed, the response is a message indicating `The print event is missing`.

## More questions?

See FAQs page for frequently asked questions related to [Devices and Printers](https://docs.clover.com/docs/faqs#devices-and-printers). Additionally, visit our Developer Community to see if your question has already been answered. Your initial requests should always begin at this forum which is highly visible to the Clover team and our developer community.
