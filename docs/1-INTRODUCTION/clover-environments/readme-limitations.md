---
title: "Limitations by environment"
slug: "readme-limitations"
excerpt: ""
hidden: false
metadata: 
  description: "Clover sandbox environment is for building and testing apps; the production environment is to  build an app for real-time use. This topic provides the limitations for each environment."
  image: []
  robots: "index"
createdAt: "Fri Jul 08 2022 17:07:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 12 2024 12:44:44 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<!--JIRA DS-5749; Replaced: https://www.clover.com and replace it with https://www.clover.com/global-developer-home to access the global developer platform only for the North America region.-->"
}
[/block]


# Sandbox developer environment

If you are in the building and testing phase of your app, [sandbox](https://docs.clover.com/docs/create-a-sandbox-account) is the right place for you. The Clover [sandbox environment](https://sandbox.dev.clover.com/developers) is a testbed where you can experiment with the platform's capabilities. 

[block:parameters]
{
  "data": {
    "h-0": "✅",
    "h-1": "❎",
    "0-0": "You **can**:  \n  \n- Create test merchant accounts to manage merchant data and install and test your solutions for these test merchant accounts without your app approvals.  \n- Create test merchants in other regions where you want to make your app available.  \n- Associate Dev Kits with your sandbox developer account.",
    "0-1": "You **cannot**:  \n  \n- Publish your apps in the sandbox environment. Create your production account and follow proper procedures to [publish](https://docs.clover.com/docs/clover-app-approval-process) and have your apps approved by [Clover App Market](https://www.clover.com/appmarket).  \n- Use release groups in the sandbox. You can only create release groups for approved apps."
  },
  "cols": 2,
  "rows": 1,
  "align": [
    "left",
    "left"
  ]
}
[/block]


# Production developer environment

If you have tried out our APIs and are ready to build an app for real-time use, create your region-specific [production developer](https://docs.clover.com/docs/developer-accounts) account in [North America](https://www.clover.com/global-developer-home), [Europe](https://www.eu.clover.com/developer-home/create-account), or [Latin America](https://www.la.clover.com/developer-home/create-account).

[block:parameters]
{
  "data": {
    "h-0": "✅",
    "h-1": "❎",
    "0-0": "- Your app is linked to a production developer account. This account must be verified and approved by Clover before app approval can begin.  \n- You can submit your [developer account for approval](https://docs.clover.com/docs/developer-account-approval) on production even while you are building and testing your app on the sandbox.  \n  **Note: **To minimize app approval delays, be sure all information is complete and accurate.",
    "0-1": "- Dev Kits are not available for the production environment. You can only associate Dev Kits with your sandbox developer account.  \n- Production demo merchants do not provide as accurate results as the sandbox [RapidConnect](https://www.rapidconnect.com/rcpub/pubapp/RapidConnectPub/) gateway for test payments."
  },
  "cols": 2,
  "rows": 1,
  "align": [
    "left",
    "left"
  ]
}
[/block]
