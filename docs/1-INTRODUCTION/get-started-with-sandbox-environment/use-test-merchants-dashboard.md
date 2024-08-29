---
title: "Work with test merchants in sandbox"
slug: "use-test-merchants-dashboard"
excerpt: ""
hidden: false
metadata: 
  description: "You can create test merchants in the sandbox environment. Use the Test Merchants page in the Developer Dashboard to view and update test merchant account settings and go to the Merchant Dashboard."
  image: []
  robots: "index"
createdAt: "Mon Sep 04 2023 10:51:20 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 05 2024 07:49:34 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="You can create test merchants in the sandbox environment. Use the Test Merchants page in the Developer Dashboard to view and update test merchant account settings and go to the Merchant Dashboard." >

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Test merchant accounts let you simulate merchant interactions with your application. This includes installing your app, assigning permissions, and then testing all the features of your app. When you sign up to create your sandbox developer account, you can create a test merchant after entering your developer and account information.

On the Test Merchants page in the Developer Dashboard, you can:

- Create and access multiple test merchant accounts.
- Manage your login credentials to access test merchants' information.
- View and manage your test merchant business information. You can click the Settings icon next to the merchant name. See [Manage test merchants](https://docs.clover.com/docs/working-with-test-merchants) for more information.

# Create your first test merchant

On the [Global Developer Dashboard](https://docs.clover.com/docs/global-developer-platform-get-started), a Default Test Merchant account is created when you create your global developer account. However, on the sandbox Developer Dashboard, when you [create a sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account), you need to create your first test merchant.

# Create additional test merchants

You can create additional test merchants for each country in a region where you want to publish your app. You can add test merchants with different settings to simulate the effects of different regions, time zones, currencies, or permissions schemes.

A specific payment gateway is configured based on the address you enter for your test merchant. For example, if you want to create an app for use in Canada, create your test merchant using a Canadian address. The test merchant you create processes test transactions using the correct gateway for that region.

1. Log in to the <<glossary:Developer Dashboard>>.
2. Do one of the following:

- From the Dashboard drop-down menu, under Developer Account, click **Create test location**.
- From the left navigation menu, in the bottom panel, click **Test Merchants**.  
  The Test Merchants page displays the list of test merchants.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/541b6b1-TMC.png",
        "",
        "Test Merchants page - Create test location"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Test Merchants page - Create test location"
    }
  ]
}
[/block]


3. Click **Add Test Merchant**. The Create your Test Merchant page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/32bb4fd-Create_test_merchant_page.png",
        "",
        "Create your Test Merchant page"
      ],
      "align": "center",
      "sizing": "80% ",
      "border": true,
      "caption": "Create your Test Merchant page"
    }
  ]
}
[/block]


4. Add information in the following fields:
5. Click **Create Account**. The merchant you added displays in the test merchants list.

| Field                    | Description                                                                                               |
| :----------------------- | :-------------------------------------------------------------------------------------------------------- |
| Merchant Name            | Name of the merchant that displays on the Test Merchants page and Dev Kits associated with the account.   |
| Country                  | Country where the merchant is located.                                                                    |
| Zip/Postal Code          | Postal code for the merchant location.                                                                    |
| Address Line             | Street and building information for the merchant location.                                                |
| City                     | City of the merchant location.                                                                            |
| State/Province           | State or province of the merchant. If the selected country does not have states or provinces, enter n/a.  |
| Phone Number             | Phone number for the merchant.                                                                            |
| Currency                 | Currency accepted by the merchant.                                                                        |
| Timezone                 | Timezone for the merchant.                                                                                |
| Employee Passcode Length | Passcode of 4- or 6-digits that employees of the merchant business must use to log on to the test device. |

# Update test merchant settings

You can update settings only for test merchants in the United States (US) region.

1. Log into the [Developer Dashboard](https://sandbox.dev.clover.com/developer-home/dashboard).

2. From the left navigation menu, in the bottom panel, click **Test Merchants**. The Test Merchants page displays the list of test merchants.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e868cf2-TMC_launcher.png",
        "",
        "Test Merchants - Settings icon"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Test Merchants - Settings icon"
    }
  ]
}
[/block]


3. From the Actions column, click the **Settings** icon next to a merchant name. The Settings pop-up appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/661b9a2-setting.png",
        "",
        "Test Merchants - Settings pop-up"
      ],
      "align": "center",
      "sizing": "60% ",
      "border": true,
      "caption": "Test Merchants - Settings pop-up"
    }
  ]
}
[/block]


   **Note: ** If the Settings page fails to load, add a new test merchant for the US region to use this feature. 

4. Update the following information:

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Card Entitlements",
    "0-1": "Select checkboxes for the card types your merchant can use to process payments.  \n**Note: **You need to select at least one card type to proceed.",
    "1-0": "Credit Card Surcharging",
    "1-1": "Use the toggle icon to turn on the feature and enter the fee in percentage (%) that the merchant can charge a customer for payment using a credit card. A merchant decides the surcharge percentage based on state rules. They can view the credit surcharge fee applied to transactions in the Virtual Terminal and on Clover devices and receipts. For more information, see:  \n  \n- [Use test cards for surcharging](https://docs.clover.com/docs/use-test-merchants-dashboard#use-test-cards-for-surcharging)  \n- [Clover Credit Card Surcharging policy](https://docs.clover.com/docs/clover-policies#clover-credit-card-surcharging-policy)",
    "2-0": "Smart Tipping",
    "2-1": "Use the toggle icon to turn on or off the Smart Tipping feature that displays on the Merchant Dashboard. If Smart Tipping is available, merchants can add a flat tip amount to the total sales value through their merchant settings.",
    "3-0": "Service Plans",
    "3-1": "Select a merchant service plan from the drop-down list. See [Test an app with different merchant service plans](https://docs.clover.com/docs/test-an-app-with-different-merchant-service-plans).  \n**Default: **Standard Merchant Plans for the test merchants in the United States (US) region."
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


4. Click **Save**. The Test Merchants page displays a confirmation message.

# Use test cards for surcharging

Use the following cards to test the surcharging feature:

[block:parameters]
{
  "data": {
    "h-0": "Card type",
    "h-1": "Card issuer",
    "h-2": "Card number",
    "h-3": "CVV",
    "h-4": "Expiry date",
    "0-0": "Credit",
    "0-1": "Mastercard<sup>®</sup>",
    "0-2": "5405 9800 0000 8303",
    "0-3": "201",
    "0-4": "12/23",
    "1-0": "Credit",
    "1-1": "Visa<sup>®</sup>",
    "1-2": "4005 5192 0000 0004 201",
    "1-3": "201",
    "1-4": "12/23"
  },
  "cols": 5,
  "rows": 2,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


# Update test merchant business information

You can update the merchant's business information only on the Developer Dashboard and not through the Setup app on a Clover device. To change your test merchant's business information:

1. Log into the [Developer Dashboard](https://sandbox.dev.clover.com/developer-home/dashboard).
2. From the left navigation menu, in the bottom panel, click **Test Merchants**. The Test Merchants page displays the list of test merchants.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/afba9aa-TMC-LaunchIcon.png",
        "",
        "Test Merchants - Launch Dashboard icon"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Test Merchants - Launch Dashboard icon"
    }
  ]
}
[/block]


3. From the Actions column, click the **Launch Dashboard** icon next to a merchant name. The Merchant Dashboard appears.
4. From the left navigation menu, click **Account & Setup**. The Account & Setup page appears.
5. In the About Your Business section, click **Business Information**. The Business Information page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b6cffef-Business_info.png",
        "",
        "Merchant Dashboard - Account & Setup > Business Information page"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Merchant Dashboard - Account & Setup > Business Information page"
    }
  ]
}
[/block]


6. Update the relevant information.
7. Click **Save**.
