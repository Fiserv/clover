---
title: "Locate the merchant identifier (merchantId)"
slug: "locating-merchant-id"
excerpt: ""
hidden: false
metadata: 
  description: "Clover assigns a universally unique identifier (UUID) known as the merchantId to every merchant business. You can search for and view merchantId in both the sandbox and production environments."
  image: []
  robots: "index"
createdAt: "Wed May 04 2022 20:58:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue May 14 2024 06:19:42 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Clover assigns a universally unique identifier (UUID) known as the merchantId to every merchant business. You can search for and view merchantId in both the sandbox and production environments.”>"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Clover assigns a universally unique identifier (**UUID**) known as the <<glossary:merchantId>> to every merchant business. You can search for and view merchantId in both the sandbox and production environments.

To locate the merchantId:

1. Log in to the <<glossary:Developer Dashboard>>.
2. From the Developer Account drop-down list, select a merchant name under Businesses. The Merchant Dashboard for the selected merchant appears.
3. From the left navigation menu, click **Account & Setup**. The Account & Setup page appears.
4. In the About Your Business section, click **Merchants**. 

[block:image]{"images":[{"image":["https://files.readme.io/5bd62fa-Merchants.png","Merchants.png",1608],"align":"center","sizing":"80","border":true}]}[/block]

The User Settings page displays the merchantId for the selected merchant. The merchantId is the 13-alphanumeric identifier below the merchant name in the Merchant column.

[block:image]{"images":[{"image":["https://files.readme.io/dd91296-MID.png","MID.png",3266],"align":"center","sizing":"100","border":true}]}[/block]

5. To view another merchantId, enter search criteria in the Search merchants by name, ID, city field, and click **Search**. The merchant information displays in the search results grid.
