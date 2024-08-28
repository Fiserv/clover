---
title: "Work with inventory"
slug: "working-with-inventory"
excerpt: ""
hidden: false
metadata: 
  description: "Use the REST API to build solutions that address specific inventory needs in different merchant verticals."
  image: []
  robots: "index"
createdAt: "Tue Feb 02 2021 18:42:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to\nthe partner docs. -->"
}
[/block]


Clover merchants manage merchandise inventory, restaurant menu items, and services using Clover devices and the merchant dashboard. Each item in the merchant’s inventory is represented by an `items` object. Clover merchants create and manage inventory items with the Clover Inventory app. Merchants can also bulk import their inventory into their sandbox merchant location.

# Sample inventory

Download the <a href="https://clover.box.com/s/y08he8u7llov7shufskgyb5stlgcs6s8" target="_blank">sample inventory file</a> that we have created to help you get started with your test merchant.

Use the REST API to build solutions that address specific inventory needs in different merchant verticals.

In this topic, we walk through standard inventory operations.

- [Import inventory](https://docs.clover.com/docs/importing-inventory)
- [Manage items and item groups](doc:managing-items-item-groups) 
- [Manage item availability](https://docs.clover.com/docs/managing-item-availability)
- [Manage categories](doc:managing-categories) 
- [Manage modifier groups and modifiers](doc:managing-modifier-groups-modifiers)
- [Manage tags](doc:managing-tags)
