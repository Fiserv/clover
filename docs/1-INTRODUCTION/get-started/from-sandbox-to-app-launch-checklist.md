---
title: "From sandbox to app launch checklist"
slug: "from-sandbox-to-app-launch-checklist"
excerpt: ""
hidden: false
metadata: 
  description: "Use the step-by-step guide referencing the sandbox and production environments, building and testing apps, and getting your apps approved."
  image: []
  robots: "index"
createdAt: "Fri Sep 30 2022 08:34:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jul 15 2024 06:13:50 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Use the step-by-step guide referencing the sandbox and production environments, building and testing apps, and getting your apps approved.">

[block:html]
{
  "html": "<!--DDS-6224 [GDE] Update the Select an integration text + Checklist for GDE-->\n<div class=\"topnav\">\n  <a href=\"https://docs.clover.com/docs/select-an-integration\">Select an integration</a>\n  <a href=\"https://docs.clover.com/docs/from-sandbox-to-app-launch-checklist#in-the-sandbox-environment\">Sandbox</a>\n  <a href=\"https://docs.clover.com/docs/from-sandbox-to-app-launch-checklist#in-the-production-environment\">Production</a>\n  <a href=\"https://docs.clover.com/docs/post-app-launch-checklist\">Post app launch checklist</a>\n</div>\n\n<!--css-->\n<style>\n/* Add a background color to the top navigation */\n.topnav {\n  font-family: 'Graphik-Regular', sans-serif;\n  background-color: #228800;\n  overflow: hidden;\n  display: flex;\n  justify-content: flex-end;\n}\n\n/* Style the links inside the navigation bar */\n.topnav a {\n  font-family: 'Graphik-Regular', sans-serif;\n  color: #f2f2f2;\n  text-align: center;\n  padding: 10px 12px;\n  text-decoration: none;\n  font-size: 14px;\n}\n\n/* Change the color of links on hover */\n.topnav a:hover {\n  background-color: #D8D8D8;\n  color: black;\n}\n\n/* Add a color to the active/current link */\n.topnav a.active {\n  background-color: #228800;\n  color: white;\n}  \n</style>"
}
[/block]


The following is a step-by-step guide referencing the sandbox and production environments, building and testing apps, and getting your apps approved.

# In the sandbox environment

<!--the <span>https\://</span> tag in html links for is **intentional**; it is to prevent the links from being clickable..............-->

[block:parameters]
{
  "data": {
    "h-0": "Step",
    "h-1": "Task",
    "h-2": "Description",
    "0-0": "1\\. ",
    "0-1": "Choose the region to build your app or integration.",
    "0-2": "\\- **North America:** [Create a global developer account](https://docs.clover.com/docs/gdp-create-global-developer-account)  and access both the sandbox and production environments on the Global Developer Dashboard.  \n—or—  \n  \n- **Europe or Latin America:** [Create your sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account#create-a-sandbox-developer-account) to access the Developer Dashboard.",
    "1-0": "2\\.",
    "1-1": "Use your sandbox developer account.",
    "1-2": "Create, test, and manage your apps in the sandbox environment. Clover provides base URLs for different services:  \n  \n- Platform API: <https://sandbox.dev.clover.com>  \n- Tokenization service API: <span>https\\://</span>token-sandbox.dev.clover.com  \n- Ecommerce service API: <span>https\\://</span>scl-sandbox.dev.clover.com",
    "2-0": "3\\.",
    "2-1": "For payment integrations, [Create Remote App ID (RAID)](https://docs.clover.com/docs/create-your-remote-app-id) in the sandbox environment.",
    "2-2": "When your integration connects to a Clover device, your application must pass a Remote App ID (remoteApplicationID or RAID) generated for your Clover app. RAID is separate from your Clover App ID, and both IDs are needed to launch your integration with Clover.",
    "3-0": "4\\.",
    "3-1": "[Create your test merchant](https://docs.clover.com/docs/use-test-merchants-dashboard) in the sandbox environment.",
    "3-2": "See the following developer guides for information on building your application:  \n  \n- [Clover Android SDK](https://github.com/clover/clover-android-sdk) to build Android apps that run on Clover devices.  \n- [Clover REST API](https://docs.clover.com/reference/api-reference-overview) to build web apps.  \n- [Clover Android Payments API](https://docs.clover.com/docs/using-clover-android-payments-api) to build a native point-of-sale (POS) application directly on a Clover device and to process payments from your Android app on a variety of Clover device configurations.  \n- [REST Pay Display API](https://docs.clover.com/docs/rest-pay-overview) to build a semi-integrated application on a Clover device connected to your POS.  \n- [Ecommerce API](https://docs.clover.com/reference/charges) and [iframe](https://docs.clover.com/docs/using-the-clover-hosted-iframe) to build a standalone or companion payment integration with Ecommerce services tailored to the needs of merchants.",
    "4-0": "5\\.",
    "4-1": "Build and test your app in the sandbox environment.",
    "4-2": "Your sandbox account is connected to a test payment gateway, which checks the validity of test cards and provides realistic responses to payment requests. You can build apps that interact with Clover's payment functions and allow you to test all possible responses when completing a transaction.  \n  \nTo learn more, see [Create an app](https://docs.clover.com/docs/creating-an-app) and [Manage app settings](https://docs.clover.com/docs/app-settings).",
    "5-0": "6\\.",
    "5-1": "[Get an OAuth token.](https://docs.clover.com/docs/oauth-flows-in-clover)",
    "5-2": "Clover OAuth 2.0 framework requires you to retrieve an access and refresh token pair before accessing merchant information, such as inventory, orders, and payments. You need to authorize merchants to access your app from the Clover App market when it is in the production environment. When an authorized merchant is redirected to your app with an authorization code, the Clover server uses the code to confirm that your request for merchant data is authorized by the merchant.",
    "6-0": "7\\.",
    "6-1": "[Generate an API test token](https://docs.clover.com/docs/generate-a-test-api-token#generate-a-test-api-token) on the test Merchant Dashboard.",
    "6-2": "**Note:** An API test token is needed only for testing purposes in the sandbox environment and is not for use in the production  \nenvironment.  \n  \nYour app uses the confirmed authorization code, client ID, and client secret to request the Clover server for an API token. With the API token, your app can make REST API calls and access merchant data"
  },
  "cols": 3,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


# In the production environment

You can submit your developer account for approval in the production environment even while you are building and testing your app in the sandbox environment.

[block:parameters]
{
  "data": {
    "h-0": "Step",
    "h-1": "Task",
    "h-2": "Description",
    "0-0": "1\\.",
    "0-1": "Use your [production developer account](https://docs.clover.com/docs/developer-accounts)",
    "0-2": "When you are ready to start building an app for real users, you need an approved production developer account for each country or region in which you want to create apps, depending on your merchant's location:  \n  \n- [North America](https://www.clover.com/global-developer-home): Global Developer Dashboard  \n- [Europe](https://www.eu.clover.com/developer-home/create-account): Developer Dashboard  \n- [Latin America](https://www.la.clover.com/developer-home/create-account): Developer Dashboard  \n  The Clover team reviews and approves each developer account you create in the production environment.",
    "1-0": "2\\.",
    "1-1": "[Submit your production developer account for approval](https://docs.clover.com/docs/developer-account-approval).",
    "1-2": "Your app is linked to a production developer account. Before app approval can begin, you must get this account verified and approved by Clover.  \nClick the **Dashboard** > **Developer Settings** tab to complete the steps.",
    "2-0": "3\\.",
    "2-1": "Recreate your app in the production environment.",
    "2-2": "Complete all the required information, including the points of integration with Clover.",
    "3-0": "4\\.",
    "3-1": "Select a region where you want to publish your APIs in the production environment.",
    "3-2": "In the production environment, Clover provides base links (URLs) for different services in [supported markets](https://docs.clover.com/docs/multiple-markets). If you are using Clover RESTful APIs, select a region as follows:  \n  \n- Platform API (US and Canada): <span>https\\://</span>api.clover.com  \n- Platform API (Europe): <span>https\\://</span>api.eu.clover.com  \n- Platform API (LATAM): <span>https\\://</span>api.la.clover.com  \n- Tokenization service API: <span>https\\://</span>token.clover.com  \n- Ecommerce service API: <span>https\\://</span>scl.clover.com",
    "4-0": "5\\.",
    "4-1": "Generate an OAuth and API token for apps on the Clover App Market in production environments.",
    "4-2": "Use the same steps to get the OAuth code and the API token as in the sandbox environment. Simply replace <https://sandbox.dev.clover.com/> with the correct regional base URL in your requests:  \n  \n- US and Canada: <https://www.clover.com/>  \n- Europe: <https://eu.clover.com/>",
    "5-0": "6\\.",
    "5-1": "[Test your app](https://docs.clover.com/docs/testing-payment-flows) and record payment flow videos for your app submission.",
    "5-2": "If required, create a [release group ](https://docs.clover.com/docs/beta-releases-staged-rollouts)to test your app on a small group of merchants.  \n  \n- Verify your application can successfully pass the required tests.  \n- Record a video of each payment flow.",
    "6-0": "7\\.",
    "6-1": "Set up billing information.",
    "6-2": "If you plan to create paid apps, you can update your bank details on the Developer Settings page on your production developer account. For more information, see:  \n  \n- [Manage developer bank account information](https://docs.clover.com/docs/billing-information-approval)  \n- [Clover developer agreement](https://www.clover.com/developer-agreement)  \n- [Handle app billing](https://docs.clover.com/docs/billing-for-apps)",
    "7-0": "8\\.",
    "7-1": "[Submit an app for approval](https://docs.clover.com/docs/developer-app-approval-archive#submit-an-app-for-approval) using your production developer account.",
    "7-2": "Get your app approved through the following review stages:  \n  \n- [Functional review](https://docs.clover.com/docs/clover-functional-review-playbook)—Clover installs your app and reviews it for functional operability.  \n- [Legal & privacy](https://docs.clover.com/docs/legal-templates#app-terms-guidelines--privacy-policy-guidelines)—Clover reviews if the app meets its terms of service and privacy policy.  \n- [Market listing](https://docs.clover.com/docs/managing-app-details)—Clover reviews information about your app for Clover merchants to view when published on the [Clover App Market](https://www.clover.com/appmarket).",
    "8-0": "9\\.",
    "8-1": "Launch your app.",
    "8-2": "- For on-Clover device and online integrations, publish your approved app in the [Clover App Market](https://www.clover.com/appmarket).  \n- For payment integrations, use CoPilot to board merchants and deploy your custom integration. See [CoPilot](https://integrate.clover.com/developers/guides/partner#using-copilot).",
    "9-0": "10\\.",
    "9-1": "Request and receive support as needed.",
    "9-2": "Maintenance phase starts once your app is approved and in production for use with Clover merchants."
  },
  "cols": 3,
  "rows": 10,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


# What's next

[Post app launch checklist](https://docs.clover.com/docs/post-app-launch-checklist)
