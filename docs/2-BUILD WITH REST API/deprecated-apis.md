---
title: "Deprecated APIs"
slug: "deprecated-apis"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides a list of deprecated APIs. It is recommended that no new apps or new features use these APIs. While you can continue using a deprecated API in an existing app, note the retirement date and plan to migrate your code to the replacement API before that date."
  image: []
  robots: "index"
createdAt: "Wed Jul 14 2021 15:58:56 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


This section contains a list of deprecated APIs. It is recommended that no new apps or new features use these APIs. While you can continue using a deprecated API in an existing app, note the retirement date and plan to migrate your code to the replacement API before that date.

[block:parameters]
{
  "data": {
    "h-0": "Deprecated API",
    "h-1": "Retirement date",
    "h-2": "Replacement API",
    "0-0": "Developer Pay API",
    "0-1": "October 27, 2021",
    "0-2": "Ecommerce API  \n  \nSee [Migrating from Developer Pay to Ecommerce](doc:migrating-from-developer-pay-to-ecommerce) for more information.",
    "1-0": "[Sync Token API](https://docs.clover.com/reference/syncgetsynctoken)",
    "1-1": "January 31, 2022",
    "1-2": ""
  },
  "cols": 3,
  "rows": 2,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
