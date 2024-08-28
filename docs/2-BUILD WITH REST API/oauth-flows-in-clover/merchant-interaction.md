---
title: "Redirect merchants to your app"
slug: "merchant-interaction"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to redirect merchants to your Clover app and provide a customized onboarding and setup experience."
  image: 
    - "https://files.readme.io/feefa53-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Mon Jun 25 2018 21:23:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jun 05 2024 10:20:59 GMT+0000 (Coordinated Universal Time)"
---
<meta name= "description" content= "Learn how to redirect merchants to your Clover app and provide a customized onboarding and setup experience.">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

You can build Clover web apps using the [Clover REST API](doc:making-rest-api-calls). The Clover integration for web applications uses the OAuth 2.0 protocol to secure API tokens for merchants. When setting up a web app, you must enter the app link or site URL, which merchants are redirected to after they install and launch an app from the Merchant Dashboard. This link is set in the sandbox Developer Dashboard for testing and in the production Developer Dashboard to launch an approved app and publish it in the Clover App Market.

# 1. Set app link (URL) redirects for test merchants

Clover redirects test merchants to the app link or <<glossary:site URL>> that you set on the sandbox Developer Dashboard. For information, see how to [set up the app link (URL) and CORs domain](https://docs.clover.com/docs/using-cors).

This URL is used when merchants:

- Install and launch your web app from the <a href= "https://www.clover.com/appmarket" target= "_blank">Clover App Market</a>.
- Launch your web app from the sandbox or test Merchant Dashboard.

As part of the site URL redirect, Clover appends certain URL parameters, including `merchantId` of the business and `employee_id` of the current user. To view all query parameters included in these redirects, see how to [receive an authorization code](https://docs.clover.com/docs/using-oauth-20#step-2-receive-an-authorization-code). 

# 2. Authenticate merchants and users

If users browse directly to your web app, rather than launch it from the Merchant Dashboard, you need to redirect them to Clover for authentication using [OAuth flows in Clover](https://docs.clover.com/docs/oauth-flows-in-clover).

In the OAuth response, you can view the following information:

- The `employee_id` of the current user associated with the merchant. A business can have multiple devices and employees. The owner of the business, along with managers and employees, have an `employee_id` associated with their account. 
- The `merchantId` of the business. The `merchantId` is a universally unique identifier (UUID) that Clover assigns to a merchant business, and it is used when making [REST API calls](doc:making-rest-api-calls).

You can use the merchant identifier (`merchantId`) and employee identifier (`employee_id` or `empId`) to determine if the merchant has used your app before and provide a user-friendly app install and setup experience.

## Locate the merchant identifier (merchantId)

Clover assigns a universally unique identifier (**UUID**) known as the <<glossary:merchantId>> to every merchant business. You can search for and view merchantId in both the sandbox and production environments. This merchantId is needed when you make [Clover REST API](https://docs.clover.com/docs/making-rest-api-calls) calls.

To locate the merchantId:

1. Log in to the <<glossary:Developer Dashboard>>.
2. From the Developer Account drop-down list, select a merchant name under Businesses. The Merchant Dashboard for the selected merchant appears.
3. From the left navigation menu, click **Account & Setup**. The Account & Setup page appears.
4. In the About Your Business section, click **Merchants**. 

[block:image]{"images":[{"image":["https://files.readme.io/5bd62fa-Merchants.png","Merchants.png",1608],"align":"center","sizing":"70% ","border":true,"caption":"Merchant Dashboard—Account & Setup"}]}[/block]

The User Settings page displays the merchantId for the selected merchant. The merchantId is the 13-alphanumeric identifier below the merchant name in the Merchant column.

[block:image]{"images":[{"image":["https://files.readme.io/dd91296-MID.png","MID.png",3266],"align":"center","sizing":"100% ","border":true,"caption":"Merchant Dashboard—User Settings"}]}[/block]

5. To view another merchantId, enter search criteria in the Search merchants by name, ID, city field, and click **Search**. The merchant information displays in the search results grid.

## Locate the employee ID

1. Log in to the <<glossary:Developer Dashboard>>.
2. From the Developer Account drop-down list, select a merchant name under Businesses. The Merchant Dashboard for the selected merchant appears.
3. From the left navigation menu, click **Account & Setup**. The Account & Setup page appears.
4. In the Employee Access section, click **Employees**. The Employees page appears. Employee ID is the 13-alphanumeric identifier below the employee name in the Employee column.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ba3c9b3-EiD.png",
        "EiD.png",
        2322
      ],
      "align": "center",
      "sizing": "95% ",
      "border": true,
      "caption": "Merchant Dashboard—Employees"
    }
  ]
}
[/block]


5. To view another employee ID, enter search criteria in the Search employees field, and click **Search**. The employee information displays in the search results grid.

# 3. Install your test app

To install your app on a test merchant account:

1. Log in to the <<glossary:Developer Dashboard>>.
2. From the left navigation menu, click **Your Apps** > _App name_ > **Market Listing.** The App name - Market Listing page appears.
3. Click **Preview in App Market**. The Merchant Dashboard for your test merchant account displays the App Market preview of your app.
4. Click **Connect**. When you accept the installation, the app is installed for your test merchant account on the Merchant Dashboard.
