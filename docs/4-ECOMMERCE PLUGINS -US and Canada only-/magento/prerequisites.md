---
title: "Prerequisites"
slug: "prerequisites"
excerpt: ""
hidden: false
metadata: 
  description: "Clover provides a functional sandbox environment for developers. Clover recommends that you test your Adobe Commerce (Magento 2) integration with the Clover plug-in by sending transactions to your sandbox account prior to sending transactions to your production Clover account."
  image: []
  robots: "index"
createdAt: "Fri Mar 25 2022 17:44:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


## Create your sandbox and production developer accounts

Clover provides a functional sandbox environment for developers. Clover recommends that you test your Adobe Commerce (Magento 2) integration with the Clover plug-in by sending transactions to your sandbox account prior to sending transactions to your production Clover account. For more information, see:

- [Setting up a sandbox account](doc:setup-clover-sandbox-account)
- [Production developer accounts](doc:developer-accounts)

## Install and use the Adobe Commerce Composer module

Clover uses Composer to install the Adobe Commerce plugin. Composer is a tool for dependency management in PHP. If you do not have Composer installed, follow the [Composer installation instructions](https://getcomposer.org/doc/00-intro.md). For information on Composer, see [Get Composer](https://getcomposer.org/).

1. Use your Adobe Commerce [authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).
2. Click **Yes** to save your username and password. Composer saves your credentials in`~/.composer/auth.json`.

## Troubleshoot Composer `Invalid Credentials` error

If the error `Invalid Credentials` appears when installing the Composer:

1. Edit the`~/.composer/auth.json` file directly.
2. Delete the file.
3. Rerun the Composer command.
