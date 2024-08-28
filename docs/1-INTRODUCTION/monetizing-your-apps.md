---
title: "Monetize your apps"
slug: "monetizing-your-apps"
excerpt: ""
hidden: false
metadata: 
  description: "The Clover platform provides many options for pricing and distributing your app. Read more about pricing and billing and how you can select an effective pricing strategy before you build and publish your app."
  image: []
  robots: "index"
createdAt: "Tue Oct 15 2019 19:02:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 12 2024 11:49:17 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<!--JIRA DS-3939 [Doc Improvements] [Editorial] Intro - Monetize your apps; Nov 2023-->\n\n<meta property=\"og:description\" content=\"The Clover platform provides many options for pricing and distributing your app. Read more about pricing and billing and how you can select an effective pricing strategy before you build and publish your app.\">\n"
}
[/block]


The Clover billing system lets you charge for paid apps in specific regions. After a <<glossary:billable merchant>> subscribes to an app through the [Clover App Market](https://www.clover.com/appmarket), Clover tracks the merchant's app usage and does the following:

- Manages the billing, collects merchant payments, and disburses your developer's share for the merchant's app usage.
- Tracks the free trial period and generates a statement of the charges from the following month until the merchant uninstalls the app and terminates all subscriptions. Billing starts at the end of the free trial period.
- Processes the previous month's refund adjustments at the beginning of the month and credits the amount to the merchant before the payment period.

## Understand app fees

All app fees, merchant app usage payments, and merchant-customer payment processing must be implemented within the Fiserv or Clover platforms. You receive 70% of the amount that Clover collects from the merchant for an installed app.

- For more information on the terms, see Part 1, section 9.2 of the [Clover App Market Developer Terms](https://www.clover.com/developer-agreement).
- For more information on app fees for merchants, see [Clover Help](https://www.clover.com/en-us/help/understand-statements-rates-and-deposits).

## Plan your pricing strategy

You can build robust apps if you plan your pricing strategy. It is important to take time to decide how you want to price your app for Clover merchants. This helps to avoid making changes after your app is published and merchants have installed it.

<!--Lucidchart diagram source: https://lucid.app/lucidchart/49708fcf-07e6-43f7-898f-a5827d952b39/edit?viewport_loc=49%2C-67%2C2560%2C1272%2Cm-5o7ONTd-nK&invitationId=inv_2ef99c92-6553-445a-b8b8-4c7c7157e642 -->

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5c3af98-DS-4957-Monetize-your-app-Plan-Strategy.png",
        "DS-491 - Billing Stages.png",
        1380
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Stages of billing: pricing strategy, build app, set up billing, publish approved app, and manage refunds"
    }
  ]
}
[/block]


Follow these guidelines to deliver your apps:

1. Identify the most suitable pricing strategy for your app. See [Understand the pricing options](https://docs.clover.com/docs/monetizing-your-apps#understand-the-pricing-options).
2. Configure pricing for your apps. See [Set up pricing tiers](https://docs.clover.com/docs/configuring-billing).
3. Publish your app and track the payment status. See [Handle app billing](https://docs.clover.com/docs/billing-for-apps).
4. Handle lapsed merchants in the app. See [View billing status](https://docs.clover.com/docs/billing-status).
5. Initiate refunds for your merchants. See [Process refunds](https://docs.clover.com/docs/billing#process-refunds).

## Understand the pricing options

To plan the pricing strategy of your app, you need to know about the available pricing options:

- Subscription
- Metered billing
- Subscription and metered billing

### 1. Subscription tier

<!--Info source: https://confluence.corp.clover.com/display/AMO/App+Market+Billing#AppMarketBilling-BillingStages -->

Every app must have a subscription, even if it is a free subscription. You can:

- Set the app subscription for a monthly price that is charged on the first of every month. 
- Set up multiple subscription tiers. A merchant can select a tier before installing your app.
- Offer a 30-day free trial for your app.

**Advance charge: ** Clover creates an advance charge at the beginning of the month and handles subscription upgrades and downloads as follows:

- New app install—Creates a prorated charge for the remainder of the current month.
- App uninstall—Creates a prorated refund for the unused part of the month's advance charge.
- App subscription level changes:
  - Subscription upgrade—Creates a prorated charge for the remainder of the current month at the new subscription level.
  - Subscription upgrade or downgrade, or a trial period ends—Adjusts the prorated amounts daily on your account.
  - Subscription upgrade and then downgrade on the same day—Doesn't charge.
  - Subscription upgrade and then uninstall an app on the same day—Refunds the unused part of the advance charge and doesn't charge for the upgrade. See [Refunds for subscription upgrades and downgrades](https://docs.clover.com/docs/billing#refunds-for-subscription-upgrades-and-downgrades).

**Calculation:** <code>Charge amount = Number of days remaining in current month \* Subscription price / number of days in current month</code>

**Example: **A merchant installs a gift card app on June 1. The app charges $10 a month for up to five gift cards. Clover exports an advance charge of $10 in June. If there is a trial period, Clover exports an advance of $10 for July, which is accounted for in the July statement.

### 2. Metered billing

<!--Info source: https://confluence.corp.clover.com/pages/viewpage.action?pageId=118889739 -->

You can:

- Set up metered billing for a per-usage event or action. You need to send the event trigger to Clover so it is recorded in the Clover billing system. You are responsible for recording metered events correctly.
- Offer a 30-day free trial for your app.

**Monthly charge:** Clover charges the merchant for each action they take on the app throughout the month. Clover generates a statement on the first of the following month for the total number of actions in the previous month. Metered charges are not partially refundable.

**Example: **Your gift card app charges $2 for each gift card purchased. A merchant installs the app in June and purchases four gift cards. The merchant's bill on July 1 displays a charge of $8. 

### 3. Subscription and metered billing

You can use a combination of the subscription and metered billing if your business requires it. 

**Monthly charge: **The merchant receives two charges in their monthly statement:

1. Single subscription charge for the new month and
2. Separate charge for the metered event from the previous month. 

**Example: **Your gift card app has the following structure:

- $10/month subscription charge for up to five gift cards
- $2 for every gift card after that

If the merchant used eight gift cards during May, they are charged the following amounts on June 1:

- $10 subscription charge for June 1–July 1
- $6 (three additional gift cards \* $2 = $6) metered charge for May

Clover collects this charge from the merchant's account and pays your share by the middle of the following month. 

## Set up your pricing strategy

To set up your pricing strategy for an app on the Developer Dashboard, see [Set up pricing tiers](https://docs.clover.com/docs/configuring-billing). You can add or change pricing for your apps at a later time. 

However, any merchants who previously downloaded the app continue under the old subscription price until they reinstall the app. Since the [Clover Terms and Conditions of Use](https://www.clover.com/terms) don't require merchants to upgrade to new pricing tiers, merchants can continue using the tier price from when they first installed the app.

## Know about the billing cycle

Billing starts after Greenwich Mean Time (GMT) midnight on the first day of the month. At the beginning of the month, Clover generates a statement for a merchant with the following:

- Subscription charges for the current month.
- Metered event charges for the previous month.

After the merchant's account is debited in the middle of the month, Clover disburses the payment to you in the third week of the following month.

**Example: **In the third week of September, Clover disburses payments for merchants billed on August 1.
