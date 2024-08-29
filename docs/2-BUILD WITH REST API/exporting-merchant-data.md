---
title: "Export merchant data"
slug: "exporting-merchant-data"
excerpt: ""
hidden: false
createdAt: "Wed May 20 2020 01:03:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n   <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


The Export API allows you to obtain bulk payment and order data from merchants who have installed your app. This service is not real-time, so your chance of running into API limit restrictions is lower. Consider using this service for data collection if you need merchant orders and payment histories.

> 📘 NOTE
> 
> If you have not used this endpoint before, email [developer-relations@devrel.clover.com](mailto:developer-relations@devrel.clover.com) during your app review to inquire about permissions.

# Prerequisites

Install and set up the following before using the Export API:

- Python 3.7.3 (backward compatible with 2.7)
- pip Python package manager
- Clover sandbox [developer account](doc:developer-accounts)

# Usage considerations

Consider the following points before using the Export API:

- Availability time: 
  - United States (US) UTC: MON-FRI 10:00-15:00, SAT 10:00-15:00, SUN 10:00-15:00
  - Europe UTC: MON-FRI 01:00-05:00, SAT 02:00-05:00, SUN 02:00-06:00
- Sandbox is not limited to specific times.
- Returns 1000 objects per file. If your response contains more than 1000 objects, returns an array of files to capture.
- Deletes exported files after 24 hours.
- Maximum time range is 30 days. If your data spans are longer, break the request into multiple requests.
- Server handles a few exports concurrently. Wait for each export to finish before you start another one. The server returns 503 errors whenever the threshold is reached.

# Use the endpoint

## Step 1: Create the request

Make a POST call to `/v3/merchants/{merchant_Id}/exports` with the appropriate payload:

- `export_type` (PAYMENTS or ORDERS)
- `start_time` (In UTC)
- `end_time` (in UTC)

```text Python
{
      "type": export_type,
      "startTime": start_time,
      "endTime": end_time
  }
```

The exports object response includes the export id for you to use in the next step.

## Step 2: Check the status and percent complete periodically

Using the export id from the previous step, make a GET call to `/v3/merchants/{merchant_Id}/exports/{export_Id}`

The following status may appear:

- `PENDING`—In the queue to be processed.
- `IN_PROGRESS`—Being processed
- `DONE`—Process complete

```text Python
{
  "status": "PENDING",
  "modifiedTime": modified_time,
  "merchantRef": {
    "id": "merchant_id"
  },
  "percentComplete": 0,
  "startTime": start_time,
  "createdTime": created_time,
  "endTime": end_time,
  "type": "ORDERS",
  "id": "export_id"
}
```

## Step 3: Download the exported files

After the request completes, your export object includes URLs (links) to the exported files for you to download.

```text Export object
{
  "id": "export_id",
  "type": "ORDERS",
  "status": "DONE",
  "percentComplete": 100,
  "availableUntil": available_until_time,
  "startTime": start_time,
  "endTime": end_time,
  "createdTime": created_time,
  "modifiedTime": modified_time,
  "exportUrls": {
    "elements": [
      {
        "url": URL,
        "export": {
          "id": "export_id"
        }
      }
    ]
  },
  "merchantRef": {
    "id": "merchant_id"
  }
}
```
