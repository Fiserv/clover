---
title: "Get started with sandbox environment"
slug: "get-started-with-sandbox-environment"
excerpt: ""
hidden: false
metadata: 
  description: "The Clover platform provides tools for developers to design, configure, test, and manage app integrations for Clover merchants. Learn about the sandbox environment for each country or region where you want to build and test apps."
  image: []
  keywords: "sandbox, Clover platform, sandbox environment"
  robots: "index"
createdAt: "Fri May 13 2022 21:09:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 22 2024 05:10:16 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<!--DS-2888 - updated September 4, 2023 -->\n<!--DS-5917 - updated Feb 20, 2024 -->\n<meta name=\" description\" content= \"The Clover platform provides tools for developers to design, configure, test, and manage app integrations for Clover merchants. Learn about the sandbox environment for each country or region where you want to build and test apps.\" > \n"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover platform provides tools for developers to design, configure, test, and manage app integrations for Clover merchants. See how to [Use Clover developer environments](https://docs.clover.com/docs/clover-environments).

# Before you begin

Note the following before you begin using the Clover sandbox and production environments on the region-based developer platforms:

- Approved developer apps that Clover merchants download and install from the [Clover App Market](https://www.clover.com/appmarket) are not impacted when you create, edit, or delete apps in the sandbox environment.
- Production test merchant accounts are connected to a payment gateway that neither checks for card validity nor verifies that the payment request is correct or complete. You must complete all testing in the sandbox environment before submitting the app for approval.

For more information, see:

- [Limitations by environment](https://docs.clover.com/docs/readme-limitations)
- [Region-specific features and limitations](https://docs.clover.com/docs/region-specific-features)

# Step 1: Create a developer account

Create a developer account based on region:

- **North America**—[Create a global developer account](https://docs.clover.com/docs/gdp-create-global-developer-account) and get access to both the sandbox and the production environment with a single developer account.
- **Europe and Latin America**—[Create a sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account).

***

> 📘 NOTE
> 
> The following steps and links are for Europe and Latin America (LATAM) regions. For the North America region, you need to use the [Create a global developer account](https://docs.clover.com/docs/gdp-create-global-developer-account) procedure.

# Step 2: Create, install, and test your apps

The [Clover sandbox environment](https://sandbox.dev.clover.com/developer-home) is a testbed where you can:

1. Experiment with the [Clover platform](https://docs.clover.com/docs/clover-architecture) capabilities.
2. [Create test merchant accounts](https://docs.clover.com/docs/create-a-sandbox-account#create-your-first-test-merchant) to manage merchant information.
3. [Create additional test merchants](https://docs.clover.com/docs/use-test-merchants-dashboard#create-additional-test-merchants) with different settings to simulate the effects of regions, time zones, currencies, or permissions.
4. [Create an app](https://docs.clover.com/docs/creating-an-app) for test merchant accounts.
5. [Manage and test your apps](https://docs.clover.com/docs/app-info-mgmt) that interact with the Clover payment functions. The sandbox environment is connected to a test payment gateway that checks the validity of test cards and provides realistic responses to payment requests. This lets you build apps that can handle all possible responses when completing a transaction.

# Step 3: Use the production environment

After you have tested your app, you need to use your approved [production developer account](https://docs.clover.com/docs/developer-accounts) and submit your app for approval. You can monitor the status of your app approval and communicate with Clover team from the production Developer Dashboard.
