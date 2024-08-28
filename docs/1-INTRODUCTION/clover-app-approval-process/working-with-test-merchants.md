---
title: "Manage test merchants"
slug: "working-with-test-merchants"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to setup the test merchant information and create additional test merchants in the Merchant Dashboard. Use test merchant accounts to fully test your app and ensure a great merchant experience."
  image: 
    - "https://files.readme.io/15795ac-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue Aug 21 2018 20:17:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 12 2024 12:48:38 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Test merchant accounts allow you to simulate merchant interactions with your application. This includes installing your app, [assigning permissions](https://docs.clover.com/docs/permissions), and then testing all the features of your app. When you sign up to [create your production developer account](https://docs.clover.com/docs/developer-accounts) in North America, Europe, or Latin America, you can create a test merchant after entering your developer account information. Test merchants on [production environment](https://docs.clover.com/docs/clover-environments#production-environment) are not billed.

# Create your first test merchant

When you login to the [production environment](https://docs.clover.com/docs/clover-environments#production-environment) based on your merchant's location, you can create your first test merchant. You can edit this information later and create additional test merchants in the Merchant Dashboard.

1. Complete steps to create a [production developer account](https://docs.clover.com/docs/developer-accounts).
2. On the Create your Test Merchant page, enter test merchant information:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b6384e6-US-CreateMerchAccnt.png",
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


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Merchant Name",
    "0-1": "Name of the merchant as displayed on the Merchant Dashboard.",
    "1-0": "Country",
    "1-1": "Country where the merchant is located.",
    "2-0": "Zip/Postal Code",
    "2-1": "Postal or ZIP code for the merchant location.",
    "3-0": "Address Line",
    "3-1": "Street and building information for the merchant location.",
    "4-0": "City",
    "4-1": "City of the merchant location.",
    "5-0": "State/Province",
    "5-1": "State or province of the merchant. If the selected country does not have states or provinces, enter `n/a`.",
    "6-0": "Phone Number",
    "6-1": "Phone number for the merchant.",
    "7-0": "Currency",
    "7-1": "Currency accepted by the merchant.  \n**Important:** If you are creating a test merchant for any region other than the United States (US), be sure to select the correct currency for testing your app. Some regions, such as Canada, allow processing in more than one currency, and this setting cannot be changed once the test merchant is created.",
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


3. Click **Create Account**. The production Developer Dashboard appears.

From here, you can:

- [Create additional test merchants in different regions](https://docs.clover.com/docs/working-with-test-merchants#create-additional-test-merchants).
- [Create an app](https://docs.clover.com/docs/creating-an-app).

# Create additional test merchants

You can:

- Create additional test merchants for each region where you want to make your app.
- Add test merchants with different settings to simulate the effects of regions, time zones, currencies, or permissions.
- Process test transactions using the correct payment gateway for a region. A specific payment gateway is configured based on the address you enter for your test merchant. For example, if you are a developer who wants to create an app for use in Canada, create your test merchant using a Canadian address.

To create additional test merchants:

1. Log in to the production Developer Dashboard.
2. From the Dashboard drop-down menu, under Developer Account, click **Create test location**. The Create your Test Merchant page appears.
3. Complete the information in the fields. For field descriptions, see [Create your first merchant](https://docs.clover.com/docs/working-with-test-merchants#create-your-first-test-merchant).
4. Click **Create Account**. The Merchant Dashboard for the test merchant appears.
5. On the Merchant Dashboard, you can complete the steps to set up your merchant account, such as:

- Update business details
- Add employees
- Set up taxes
- Build an inventory

For more information, see [Clover Help](https://www.clover.com/en-US/help/get-started-with-clover).

# Update merchant information

You cannot change the merchant's business information using the Setup app on a Clover device. To change your test merchant's business information:

1. Log in to the production Developer Dashboard.
2. From the Dashboard drop-down menu, under Businesses, click \<**Merchant Name**>. The Merchant Dashboard appears.
3. From the left navigation menu, click **Setup**. The Business Information page appears.
4. Enter information in the fields, such as business name and address, currency, timezone, privacy policy, and business hours, and upload the business logo.
5. Click **Save**.

# Install your app to a test merchant

   After you build and test your apps, you can [install your app to your test merchant](https://docs.clover.com/docs/installing-your-app-to-your-test-merchant).  
   For more information, see:

- [Set app permissions](https://docs.clover.com/docs/permissions)
- [Redirect merchant to apps](https://docs.clover.com/docs/merchant-interaction)
