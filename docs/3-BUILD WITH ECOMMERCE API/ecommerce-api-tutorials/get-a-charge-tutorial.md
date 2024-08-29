---
title: "Get charges endpoints"
slug: "get-a-charge-tutorial"
excerpt: ""
hidden: false
metadata: 
  description: "A charge is a cash, credit card or other payment source that indicates a successfully processed transaction. Charges are captured when a create a charge endpoint is issued. The get a charge endpoints allow you to either retrieve a single charge or several charges."
  image: []
  robots: "index"
createdAt: "Mon Jul 18 2022 21:50:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


The get a charge endpoints allow you to either retrieve a single charge (that is, [Get a charge](ref:getchargescharge)) or retrieve several charges (that is, [Get charges](ref:getcharges)). A charge is a cash, credit card or other payment source that indicates a successfully processed transaction. Charges are captured when a [Create a charge](ref:createcharge) endpoint is issued.  

## Endpoints

Clover includes two types of get charges endpoints:

- [Get a charge](doc:get-a-charge) 
- [Get charges](doc:get-charges)
