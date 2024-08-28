---
title: "Retrieve funding information (beta)"
slug: "funding"
excerpt: ""
hidden: false
metadata: 
  description: "Use the Funding API to retrieve information regarding a merchant’s Fiserv card processing, including the amount submitted, fees, adjustments, chargebacks, reversals, interchange charges, processing service charges, amount paid by other card processors, and the total amount transferred to their bank account."
  image: []
  robots: "index"
createdAt: "Wed Apr 06 2022 15:38:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 06 2024 03:06:56 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--DS-6053, edit note and call it beta bc no one in-house can enable that feature. \n<!-- We might need to hide the topic later. \n<!-- Fixed headings in this section to sentence case, too. -cd, 3.6.2024-->\n<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


The Funding API can be used to retrieve information regarding a merchant’s Fiserv card processing, including the amount submitted, fees, adjustments, chargebacks, reversals, interchange charges, processing service charges, amount paid by other card processors, and the total amount transferred to their bank account. 

The Funding API supports requests for a specific merchant, returning all available funding data, for a specific date, or a breakdown of volume by card type.

> 🚧 Beta
> 
> Currently, the Funding API is only available for field testing and is not generally available in Sandbox or Production environments. 
> 
> Please check [What's New](https://docs.clover.com/docs/whats-new) to be on the lookout for when this API is made available. Once it is available in Production, it will require the service to be enabled on your merchants' accounts before you, as a developer, can access Funding API data. In Clover’s Sandbox environment, you can prepare your application to handle the JSON responses as described in the [API Reference](https://docs.clover.com/reference/api-reference-overview).

## Funding API overview

There are three funding endpoints: 

1. `deposits` returns all available funded deposit information for a given merchant.
2. `dateFunded` returns the available deposit information for a specific date.
3. `card_type` returns a report of the amount funded by credit card type (VISA, MC, DISC, AMEX).

## API reference

- [Deposits](doc:funding-examples) 
- [DateFunded](doc:datefunded) 
- [Card_types](doc:card-type) 
- [Appendix](doc:funding-api-description)
