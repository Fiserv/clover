---
title: "Use Clover developer environments"
slug: "clover-environments"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to work with the Clover environments and how to test and get apps approved for the Clover App Market."
  image: 
    - "https://files.readme.io/3ce21fe-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue Aug 21 2018 18:51:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 10 2024 22:19:39 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<!--JIRA DS-5749; Replaced: https://www.clover.com and replace it with https://www.clover.com/global-developer-home to access the global developer platform only for the North America region.-->\n<!--JIRA DS-5917; Segregated content by region and platform-->"
}
[/block]


The Clover open platform provides tools for developers to design, configure, test, and manage app integrations for Clover merchants. You can use different environments based on specific regions:

[block:parameters]
{
  "data": {
    "h-0": "Region",
    "h-1": "Platform",
    "h-2": "Description",
    "0-0": "North America—United States and Canada",
    "0-1": "Global developer platform",
    "0-2": "\\- Use to develop and launch apps and integrations only in the North America region.  \n- Create a single developer account and access both the sandbox and production environments on the [Global Developer Dashboard](https://www.clover.com/global-developer-home).  \nSee [Get started with the global developer platform](https://docs.clover.com/docs/global-developer-platform-get-started).",
    "1-0": "Europe and Latin America—Argentina",
    "1-1": "Developer platform",
    "1-2": "\\- Use to develop and launch apps and integrations in the Europe and Latin America regions.  \n- Create two separate developer accounts on the sandbox and the region-based production environments to access the following:  \n    > Sandbox Developer Dashboard for initial setup and testing. See [Get started with sandbox environment](https://docs.clover.com/docs/get-started-with-sandbox-environment).  \n    > Production Developer Dashboard to submit integrations for approval and then manage and track app performance. See [Get started with production environment](https://docs.clover.com/docs/clover-app-approval-process)."
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


***

# Global developer platform

[block:html]{"html":"<div class=\"container-top\">\n  <!--North America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">North America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover global developer platform offers a consolidated developer experience with access to the [Global Developer Dashboard](https://www.clover.com/global-developer-home).

To create apps and integrations for the North America region:

1. [Create a global developer account](https://docs.clover.com/docs/gdp-create-global-developer-account). 
2. Build and test your apps in the sandbox first. 
   1. Install your apps on [test merchants](https://docs.clover.com/docs/gdp-manage-test-merchants-accounts) accounts. When you sign up on the global developer platform to create a developer account, Clover creates a default test merchant account for both sandbox and production environments.
   2. Create additional test merchant accounts with different settings to simulate the effects of regions, time zones, currencies, or permissions.
   3. Test your apps that interact with the Clover payment functions. The sandbox environment is connected to a test payment gateway that checks the validity of test cards and provides realistic responses to payment requests. This lets you build apps that can handle all possible responses when completing a transaction.
3. Turn off the Sandbox toggle icon to:
   1. Access the production environment.
   2. Complete the developer account verification and approval process.
   3. Re-create your app in the production environment.
   4. Test and submit your app for approval. The Clover team reviews and approves each developer account you create in the production environment. After your app is approved and published, merchants can download and install your app from the [Clover App Market](https://www.clover.com/appmarket). 
   5. Monitor the status of your app approval and communicate with the Clover team from the production Developer Dashboard. For more information, see [Understand the app approval process](https://docs.clover.com/docs/developer-app-approval-archive).

> 📘 NOTE
> 
> If you have an existing developer platform account in North America, note the following when signing up on the global developer platform:
> 
> - You cannot use an email address that you previously used to create your sandbox or production accounts.
> - You cannot invite members to your global developer platform account with email addresses that were previously associated with a sandbox or product account.

***

# Developer platform

[block:html]{"html":"\n<div class=\"container-top\">\n    <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

## Sandbox environment

You can use the sandbox environment as a testbed to experiment with the Clover platform capabilities.

1. [Create a sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account).
2. Use the [sandbox Developer Dashboard](https://sandbox.dev.clover.com/developer-home/) to:
   1. Build and test your apps.
   2. Install your apps on [test merchants](https://docs.clover.com/docs/use-test-merchants-dashboard) accounts before you create a production developer account and submit your app for approval.
   3. Create additional test merchants for each region with different settings to simulate the effects of regions, time zones, currencies, or permissions.
   4. Test your apps that interact with the Clover payment functions. The sandbox environment is connected to a test payment gateway that checks the validity of test cards and provides realistic responses to payment requests. This lets you build apps that can handle all possible responses when completing a transaction.

## Production environment

You must have an approved production developer account before Clover can approve your apps. 

1. Create a separate [production developer account](https://docs.clover.com/docs/developer-accounts#create-a-production-developer-account) for each country or region where you want to create apps:

- Europe: [https://www.eu.clover.com](https://www.eu.clover.com/developer-home/create-account)
- Latin America: [https://www.la.clover.com](https://www.la.clover.com/developer-home/create-account)  
  **Note: **You can use the same email address to sign up as a developer in multiple regions.

2. Complete the developer account verification and approval process.
3. Re-create your app in the production environment.
4. Submit your app for approval after you test your app. The Clover team reviews and approves each developer account you create in a production environment. After your app is approved and published, merchants can download and install your app from the [Clover App Market](https://www.clover.com/appmarket).
5. Monitor the status of your app approval and communicate with the Clover team from the production Developer Dashboard. For more information, see [Understand the app approval process](https://docs.clover.com/docs/developer-app-approval-archive).
