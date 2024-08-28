---
title: "Convert Clover timestamps to Unix time"
slug: "convert-timestamps-to-unix-time"
excerpt: ""
hidden: false
metadata: 
  description: "Clover uses common timestamp methods that in are milliseconds from the same epoch time as Unix time  (Jan 1, 1970)."
  image: []
  robots: "index"
createdAt: "Thu Jun 08 2023 15:36:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:23 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n   <!--Latin America-->\n    <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Clover uses common timestamp methods that in are milliseconds from the same epoch time as Unix time  (Jan 1, 1970). If your app requires Unix time, divide the Clover timestamp by 1000.
