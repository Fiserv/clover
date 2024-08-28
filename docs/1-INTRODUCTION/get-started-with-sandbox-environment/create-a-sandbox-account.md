---
title: "Create a sandbox developer account"
slug: "create-a-sandbox-account"
excerpt: ""
hidden: false
metadata: 
  description: "The Clover platform provides tools for developers to design, configure, test, and manage app integrations for Clover merchants. Learn how to create a sandbox developer account for each country or region where you want to create apps."
  image: []
  keywords: "clover platform, sandbox environment"
  robots: "index"
createdAt: "Fri May 13 2022 21:20:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jun 14 2024 08:28:35 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to\n\"Setting up a sandbox account\". -->\n<!--Updated DS-2888 on Sept 4, 2023-->\n\n<!-- In Sept 2023, for DS-4248 this page which originally contained the same content was edited to remove duplicate content and redundancy and make the topic useful without the need to remove it: https://docs.clover.com/docs/setup-clover-sandbox-account-—>\n\n<!--Note from Aneesha on Sept 4, 2023-Source for the text about dynamic URLs is https://docs.google.com/document/d/1xVO-mKaK1zxuyQ3QQv9iTXPletmYsOa86T2L_vo7yHw/edit.\nI could not find the exact JIRA for the documentation update but the content is valid: Developer impact\nAfter the maintenance, the URLs for all sandbox services will have a dynamic IP address. Any developers using static IP addresses for connecting to sandbox services must support the URLs instead. -->\n\n<!--DS-5917-->\n<!--DS-6576-->\n\n <meta name=\" description\" content= \"The Clover platform provides tools for developers to design, configure, test, and manage app integrations for Clover merchants. Learn how to create a sandbox developer account for each country or region where you want to build and test apps.\" > "
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover platform provides tools for you to design and build apps for Clover merchants. Use the Clover sandbox environment as a testbed to build and test your apps for [test merchant accounts](https://docs.clover.com/docs/use-test-merchants-dashboard).

# Before you begin

Choose your region:

- **North America**—To build an integration for the North America region, [create a global developer account](https://docs.clover.com/docs/gdp-create-global-developer-account). On the Global Developer Dashboard, a Default Test Merchant account is created when you create your global developer account. You can [create additional test merchants](https://docs.clover.com/docs/use-test-merchants-dashboard#create-additional-test-merchants) if needed.
- **Europe and Latin America**—To create apps for the Europe and Latin America (LATAM) regions, continue to [create a sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account#create-a-sandbox-developer-account).

# Recommendation for developers

Note the following before you begin creating a sandbox developer account:

- If you process credit cards, Clover recommends you secure your account with [two-factor authentication](https://docs.clover.com/docs/set-up-two-factor-authentication-2fa) to protect merchants and their data.
- If you create, edit, or delete apps in the sandbox environment, your published apps in the [Clover App Market](https://www.clover.com/appmarket) are unaffected. Thus, merchants who have installed apps from the Clover App Market are not impacted by app changes in the sandbox.
- If you use a static IP address, you need to support the links (URLs) for all sandbox services that have dynamic IP addresses.

***

> 📘 NOTE
> 
> The following procedures are for Europe and Latin America (LATAM) regions. For the North America region, you need to [Create a global developer account](https://docs.clover.com/docs/gdp-create-global-developer-account).

# Create a sandbox developer account

[block:html]{"html":"\n<div class=\"container-top\">\n    <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

1. Go to [Clover sandbox environment](https://sandbox.dev.clover.com/developer-home/create-account). The Create your Developer account page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1f5e896-CreateSandboxAccount.png",
        "CreateDevAccnt.png",
        1230
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Create your Developer account to access the sandbox Developer Dashboard"
    }
  ]
}
[/block]


2. Enter your email address, and click **Create Account**. A message appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c4f4d87-VerifyEmail.png",
        "VerifyEmail.png",
        1222
      ],
      "align": "center",
      "sizing": "70% ",
      "border": true,
      "caption": "Verify your email address"
    }
  ]
}
[/block]


3. Go to your email account, and in the confirmation email from Clover, click **Set a password**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/59bee62-Access-Clover.png",
        "Access-Clover.png",
        2350
      ],
      "align": "center",
      "sizing": "90% ",
      "border": true,
      "caption": "Welcome to Clover email"
    }
  ]
}
[/block]


The Set your Password pop-up appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1434ed2-SetPassword.png",
        "SetPassword.png",
        1208
      ],
      "align": "center",
      "sizing": "60% ",
      "border": true,
      "caption": "Set your password"
    }
  ]
}
[/block]


4. Create a strong password, and click **Continue**. The Welcome to Clover! pop-up appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/275e021-Step1-Dev-Name.png",
        "Step1-2-Dev-Name.png",
        2246
      ],
      "align": "center",
      "sizing": "60% ",
      "border": true,
      "caption": "Welcome to Clover"
    }
  ]
}
[/block]


5. In the Full Name field, enter identification information for your sandbox developer account, and click **Continue**. The Name your Developer Account page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/916eafa-Step2-Dev-Public-Name.png",
        "Step1-2-Dev-Name.png",
        2246
      ],
      "align": "center",
      "sizing": "60% ",
      "border": true,
      "caption": "Name your Developer Account"
    }
  ]
}
[/block]


6. In the Public Developer Name field, enter either your developer name or company name to display in the  [Clover App Market](https://www.clover.com/appmarket), and click **Continue.** The Create your Test Merchant page appears.
7. Enter information to create a test merchant. See [Create your first test merchant](https://docs.clover.com/docs/create-a-sandbox-account#create-your-first-test-merchant).
8. Click **Create Account **to complete the steps to create your sandbox developer account and first test merchant.

# Create your first test merchant

When you sign up to create your sandbox developer account, you can create a test merchant after entering your developer and account information. Test merchants allow you to simulate merchant interactions with your application, such as installing your app, granting permissions, and then testing all the features of your app. Test merchants are non-billable.

1. Complete the steps to [create a sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account#create-a-sandbox-developer-account).
2. On the Create your Test Merchant page, enter test merchant information: 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2149164-Step3-CreateMerchAccnt.png",
        "CreateMerchAccnt.png",
        1636
      ],
      "align": "center",
      "sizing": "70% ",
      "border": true,
      "caption": "Create your Test Merchant"
    }
  ]
}
[/block]


You can edit this information later and also [create additional test merchants](https://docs.clover.com/docs/use-test-merchants-dashboard#create-additional-test-merchants) on the [Test Merchants Dashboard](https://docs.clover.com/docs/use-test-merchants-dashboard). 

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Merchant Name",
    "0-1": "Name of the merchant that displays in your [Developer Dashboard](https://sandbox.dev.clover.com/developer-home/dashboard) and on [Clover Dev Kits ](https://docs.clover.com/docs/clover-dev-kits)associated with the account.",
    "1-0": "Country",
    "1-1": "Country where the merchant operates.",
    "2-0": "Zip/Postal/Pin Code",
    "2-1": "Valid postal or ZIP code for the merchant.",
    "3-0": "Street Address",
    "3-1": "Street and building information for the merchant.",
    "4-0": "City",
    "4-1": "City of the merchant business.",
    "5-0": "State/Province",
    "5-1": "State or province of the merchant business. If the selected country does not have states or provinces, enter `n/a`.",
    "6-0": "Currency",
    "6-1": "Currency accepted by the merchant.  \n**Important: **If you are creating a test merchant for any region besides the US, be sure to select the correct currency for testing your app. Some regions, such as Canada, allow processing in more than one currency, and this setting cannot be changed once the test merchant is created.",
    "7-0": "Phone Number",
    "7-1": "Phone number for the merchant.",
    "8-0": "Timezone",
    "8-1": "Timezone for the merchant.",
    "9-0": "Employee Passcode Length",
    "9-1": "Passcode of 4- or 6-digits that employees of the merchant business must use to log on to the test device."
  },
  "cols": 2,
  "rows": 10,
  "align": [
    "left",
    "left"
  ]
}
[/block]


3. Click **Create Account**. The Developer Dashboard for your account is available in the sandbox environment. You can now [create an app](https://docs.clover.com/docs/creating-an-app).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8c645b9-CreateFirstApp.png",
        "CreateFirstApp.png",
        3432
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Sandbox Developer Dashboard"
    }
  ]
}
[/block]


# Use sample inventory to get started with your test merchant

We've created a [sample inventory file ](https://clover.box.com/s/y08he8u7llov7shufskgyb5stlgcs6s8)to help you get started with your test merchant.

1. Download the [sample inventory](https://clover.app.box.com/s/y08he8u7llov7shufskgyb5stlgcs6s8) and save it to your computer.
2. Log in to your sandbox [Developer Dashboard](https://sandbox.dev.clover.com/developer-home/dashboard).
3. From the Developer Account drop-down list, select a merchant name under Businesses. The Merchant Dashboard for the selected merchant appears.
4. From the left navigation menu, click **Inventory**. The Items page appears.
5. Click** Import Your Inventory Spreadsheet**. The Import Inventory page appears.
6. Import the sample inventory spreadsheet. You can either:

- Browse to your inventory spreadsheet and drag and drop it into the Import Inventory page.  
  —or—
- Click **Choose File** to browse and select the inventory spreadsheet.  
  The To be added to inventory page displays the name of the imported sample inventory spreadsheet and the count of items in each of the tabs in the imported spreadsheet.

7. Validate the information on the page and click **Continue**. A Success pop-up appears.
8. Click **Back to my inventory**. The Items page displays the inventory items.

For more details, see [Work with inventory](doc:working-with-inventory).

# Receive Clover platform status updates

1. Sign up on [Clover Status page](https://status.clover.com/) to stay informed about maintenance windows.
2. Use this information to plan your work, such as not connecting to Clover resources when they may be less responsive than usual or down for maintenance.
