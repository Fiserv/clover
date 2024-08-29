---
title: "Initiate OAuth flow from the Clover App Market app selection"
slug: "merchant-dashboard-left-navigation-oauth-flow"
excerpt: ""
hidden: false
metadata: 
  title: "Start OAuth through left nav app link"
  description: "Learn how to start the OAuth flow through the left nav app link."
  image: []
  robots: "index"
createdAt: "Fri Aug 25 2023 18:25:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 05 2024 12:55:05 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Learn how to start the OAuth flow in the Global Developer Dashboard through the left nav app link." >

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# Legacy left navigation menu flow

Before Clover implemented v2 OAuth, when a merchant installed an app from the Merchant Dashboard > **More Tools** > Clover App Market page or the [Clover App Market](https://www.clover.com/appmarket), Clover redirected the merchant through a partial OAuth flow. This process bypassed the first endpoint in the OAuth process—`/oauth/authorize`—and took some of the OAuth flow control away from you and your app.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4874e6b-Auth_Code_Flows_-_Left_Nav_Pane_Legacy_Flow.png",
        "",
        "Legacy flow from Merchant Dashboard left navigation menu"
      ],
      "align": "center",
      "caption": "Legacy flow from Merchant Dashboard left navigation menu"
    }
  ]
}
[/block]


# Apps initiate the OAuth flow

The Clover v2 OAuth flow starts when the merchant selects your app from the [Clover App Market](https://www.clover.com/appmarket) or the Merchant Dashboard > **More Tools** > Clover App Market page. Clover redirects the merchant to your app with a merchant ID. From there, your app must call the v2 authorize endpoint to initiate OAuth. Your app has full control of the entire OAuth flow and facilitates the use of v2 OAuth.

If a merchant loads the app from your website instead of installing (connecting) it from the Clover App Market, your app needs to redirect the merchant to the Clover App Market page to install the app from there.

Clover **requires new apps** to use the v2 OAuth flow. However, for both new and existing apps, you can roll out the v2 OAuth flow as you deem fit—for example, all at once or by using feature flags or gradual rollouts.

> 🚧 IMPORTANT
> 
> By **August 1, 2024** it is mandatory for all new and existing apps to use the Clover v2 OAuth flow.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9b4017a-Auth_Code_Flows_-_Left_Nav_Pane_OAuth_Flow.png",
        "",
        "Left navigation menu v2 OAuth flow starting with the app"
      ],
      "align": "center",
      "caption": "Left navigation menu v2 OAuth flow starting with the app\\*"
    }
  ]
}
[/block]


\*You can learn more about PKCE in [OAuth terminology](https://docs.clover.com/docs/oauth-intro#oauth-terminology). 

# Set the Alternate Launch Path

The Alternate Launch Path sends the merchant directly to your app and initiates the OAuth flow. Enter your app’s Alternate Launch Path on the [Global Developer Dashboard](https://www.clover.com/global-developer-home), Edit REST Configuration web app settings.

The flow is:

- The merchant clicks **Connect** on your app in the Clover App Market.
- The Clover App Market redirects the merchant to the location specified in the Alternate Launch Path field.
- The app calls `/oauth/v2/authorize` to initiate OAuth. 

The Alternate Launch Path URL domain depends on the site URL. See [Add web app settings](https://docs.clover.com/docs/app-settings#add-web-app-settings) and [Set app link (URL) and CORS domain](https://docs.clover.com/docs/using-cors) for more information.
