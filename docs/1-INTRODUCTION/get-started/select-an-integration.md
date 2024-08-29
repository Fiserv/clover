---
title: "Select an integration and Clover developer tools"
slug: "select-an-integration"
excerpt: ""
hidden: false
metadata: 
  description: "Use a decision tree, step-by-step guide, and checklists to select how to integrate with Clover and identify the developer tools to use, including creating a sandbox developer account, building a test app, and setting up a production developer account."
  image: []
  robots: "index"
createdAt: "Tue Oct 04 2022 02:39:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 10 2024 22:21:02 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--DDS-6224 [GDE] Update the Select an integration text + Checklist for GDE-->\n<meta name=\"description\" content=\"Use a decision tree, step-by-step guide, and checklists to select how to integrate with Clover and identify the developer tools to use, including creating a sandbox developer account, building a test app, and setting up a production developer account.\">"
}
[/block]


# 1\. Use our decision tree to select an integration

The following decision tree can help you select how to integrate with Clover and identify the developer tools to use:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/28b7415-SelectAnIntegration.png",
        "SelectAnIntegration.png",
        3520
      ],
      "align": "center",
      "sizing": "auto"
    }
  ]
}
[/block]


# 2\. Build your app

Once you select your integration, you are ready to create your developer account and start building your app. Here are the high-level steps you need to follow based on your region and the associated [Clover environments](https://docs.clover.com/docs/clover-environments):

[block:html]{"html":"<!--global developer platform + NA region pill icon-->\n<div class=\"container-top\">\n  <!-- North America -->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">North America—US and Canada</div>\n    </div>\n  </div>\n</div> \n\n<!-- GDP-Env-blue-icon -->\n<div class=\"container-top\">\n  <div class=\"container-env\">\n    <div class=\"pill-env\">\n      <div class=\"label-env\">Global developer platform</div>\n    </div>\n  </div>\n</div>\n\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: 5px;\n}\n\n.container-reg, .container-env {\n  align-items: center;\n  min-width: 12%;\n  text-align: left;\n  overflow: auto;\n  display: block; \n}\n\n/*Pill format REG and ENV*/\n.pill-reg, .pill-env {\n  border: .5px solid;\n  margin-left: 5px;\n  overflow: auto;\n  display: inline-flex;\n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  padding: 3px 20px; \n  margin-bottom:1.5px; \n}\n\n.pill-reg {\n  background: #44BB44; /* Green background for REG */\n  border-color: #44BB44; /* Green border for REG */\n}\n\n.pill-env {\n  background: #2e8bc9; /* Blue background for ENV */\n  border-color: #2e8bc9; /* Blue border for ENV */\n}\n\n/*Text FORMAT inside both the ENV and REG pills*/\n.pill-reg .label-reg, .pill-env .label-env {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.80rem;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n}\n</style>"}[/block]

| Step | Description                                                                                                                  |
| :--- | :--------------------------------------------------------------------------------------------------------------------------- |
| 1\.  | Create a [global developer account](https://docs.clover.com/docs/gdp-create-global-developer-account).                       |
| 2\.  | [Create test app in sandbox](https://docs.clover.com/docs/creating-an-app).                                                  |
| 3\.  | [Submit developer account for approval](https://docs.clover.com/docs/developer-account-approval).                            |
| 4\.  | Complete the [app approval process](https://docs.clover.com/docs/developer-app-approval-archive#submit-an-app-for-approval). |

***

[block:html]{"html":"\n<div class=\"container-top\">\n    <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]{"html":"<!--Environment-->\n<div class=\"container-top\">\n  <!-- Sandbox -->\n  <div class=\"container-env\"> \n    <div class=\"pill-env\">\n      <div class=\"label-env\">Sandbox</div>\n    </div>\n  </div>\n  <!-- Production -->\n  <div class=\"container-env\"> \n    <div class=\"pill-env\">\n      <div class=\"label-env\">Production</div>\n    </div>\n  </div>\n</div>\n\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: 5px;\n}\n\n.container-env {\n  align-items: center;\n  min-width: 12%;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; /* Displays icons side by side */\n}\n\n/*Pill format ENV*/\n.pill-env {\n  border: .5px solid;\n  margin-left: 5px;\n  overflow: auto;\n  display: inline-flex;\n  justify-content: center; \n  align-items: center;\n  border-radius: 10px;\n  height: 1.8rem;\n  padding: 3px 20px; \n  margin-top: .5px;\n  margin-bottom: .5px; \n  background: #2e8bc9; /* Blue background for ENV */\n  border-color: #2e8bc9; /* Blue border for ENV */\n}\n\n/*Text FORMAT inside the ENV pill*/\n.pill-env .label-env {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.80rem;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n}\n</style>"}[/block]

| Step | Description                                                                                                                  |
| :--- | :--------------------------------------------------------------------------------------------------------------------------- |
| 1\.  | Create a [sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account).                                 |
| 2\.  | [Create test app in sandbox](https://docs.clover.com/docs/creating-an-app).                                                  |
| 3\.  | Create a [production developer account](https://docs.clover.com/docs/developer-accounts).                                    |
| 4\.  | [Submit developer account for approval](https://docs.clover.com/docs/developer-account-approval).                            |
| 5\.  | Complete the [app approval process](https://docs.clover.com/docs/developer-app-approval-archive#submit-an-app-for-approval). |

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3cd087e-PublishApp.png",
        "PublishApp.png",
        3520
      ],
      "align": "center",
      "sizing": "smart"
    }
  ]
}
[/block]


# 3\. Publish your app with a step-by-step guide

You now have an overview of creating an app using your preferred integration. Use the following checklists for step-by-step instructions to start building your app:

| Step | Checklist                                                                                                 |
| :--- | :-------------------------------------------------------------------------------------------------------- |
| 1\.  | [From sandbox to app launch checklist](https://docs.clover.com/docs/from-sandbox-to-app-launch-checklist) |
| 2\.  | [Post app launch checklist](https://docs.clover.com/docs/post-app-launch-checklist)                       |
