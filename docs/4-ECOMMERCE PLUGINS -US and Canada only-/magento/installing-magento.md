---
title: "Install, upgrade, and uninstall the Clover Payment extension"
slug: "installing-magento"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides the procedures to install, upgrade, and uninstall the payment extension using Composer."
  image: []
  robots: "index"
createdAt: "Fri Mar 25 2022 16:33:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Use the following procedures to install, upgrade, and uninstall the payment extension using Composer.

# Install the Clover Payment extension for Adobe Commerce

Install the [Adobe Commerce module](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/extensions.html) using Composer. 

1. Place an order for the module through the [Adobe Commerce Marketplace](https://marketplace.magento.com/).
2. Open a terminal and run the following command in your Adobe Commerce directory.  
   If you are using Composer for the first time, or if you see a Composer error, make sure that you have saved your [authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

```text CLI Command
$ composer require clover/module-payments
```

3. Run the following commands to set up the module.

```text Setup Commands
$ bin/magento setup:upgrade
$ bin/magento cache:flush
$ bin/magento cache:clean
```

4. If you run Adobe Commerce in the production environment, run the following commands to compile and deploy the module static files.

```text Compile and Deploy commands
$ bin/magento setup:di:compile
$ bin/magento setup:static-content:deploy
```

> 📘 Important
> 
> The Clover Payments Extension for Adobe Commerce release 1.0.2 is only available in the US and Canada. Ensure that the value of **General** > **Currency Setup **> **Display Currency** in Adobe Commerce matches the payment region.

# Upgrade the Adobe Commerce module

If you installed the Adobe Commerce module using Composer, run the following commands to upgrade the payments extension.

```text
$ composer remove clover/module-payments 
$ composer require clover/module-payments 
$ bin/magento setup:upgrade 
$ bin/magento setup:di:compile 
$ bin/magento setup:static-content:deploy 
$ bin/magento cache:clean
```

# Uninstall the Clover Payment extension for Adobe Commerce

If you installed the Adobe Commerce module using Composer, run the following commands to uninstall the payments extension.

```text
$ composer remove clover/module-payments 
$ bin/magento setup:upgrade 
$ bin/magento setup:di:compile 
$ bin/magento setup:static-content:deploy 
$ bin/magento cache:clean
```
