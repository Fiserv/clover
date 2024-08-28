---
title: "Use test merchant identifier and API token"
slug: "merchant-id-and-api-token-for-development"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to locate your test merchant identifier (merchantId) and create a test API token on the Developer Dashboard—important for testing interactions with Clover REST API and Android development."
  image: []
  robots: "index"
createdAt: "Mon Jun 25 2018 21:23:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Aug 07 2024 10:23:51 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Learn how to locate your test merchant identifier (merchantId) and create a test API token on the Developer Dashboard—important for testing interactions with Clover REST API and Android development.”>"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Test API tokens generated from the sandbox Merchant Dashboard are intended for development and testing only. The merchant identifier `merchantId` and the test API token are required for you to test interactions with Clover REST API and for Android development. Production apps must use API tokens generated using the relevant [OAuth flow](https://docs.clover.com/docs/oauth-flows-in-clover) or the [Clover Android SDK](https://docs.clover.com/docs/setting-android-sdk-versions). In production environments, test API tokens have additional restrictions with [rate limits](https://docs.clover.com/docs/api-usage-rate-limits).

The following procedures are for app development and testing in the sandbox environment.

# Locate the test merchant identifier (merchantId)

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

***

# Generate a merchant-specific test API token in sandbox

With your test API token, you can make a REST API call and access Clover merchant data. You can create as many merchant-specific test API tokens as required.

## Prerequisites

- [Create a sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account).
- [Create test merchant account](https://docs.clover.com/docs/use-test-merchants-dashboard).

## Steps

1. Log in to the <<glossary:Developer Dashboard>>.
2. From the Developer Account drop-down list, select a merchant name under Businesses. The test Merchant Dashboard appears.
3. From the left navigation menu, click **Account & Setup.** The Account & Setup page appears.
4. In the Business Operations section, click **API Tokens**.

[block:image]{"images":[{"image":["https://files.readme.io/b9c0eb8-AccntSetup-CreateToken.png","Accnt-Setup.png",2650],"align":"center","sizing":"100% ","border":true,"caption":"Test Merchant Dashboard: Account & Setup page"}]}[/block]

The API Tokens page appears.

[block:image]{"images":[{"image":["https://files.readme.io/b133269-CreateNewToken.png","Create-New-Tken.png",3456],"align":"center","sizing":"100% ","border":true,"caption":"Test Merchant Dashboard: API Tokens"}]}[/block]

5. Click **Create New Token**. The Create new token pop-up displays app permissions that map to platform API endpoints. See [API Reference](https://docs.clover.com/reference/api-reference-overview) > Platform API section.

[block:image]{"images":[{"image":["https://files.readme.io/cfdf764-Create-New-Token-Popup.png","Create-New-Token-Popup.png",1296],"align":"center","sizing":"50","border":true,"caption":"Create new token pop-up"}]}[/block]

6. Enter a token name.
7. Select checkboxes to set permissions based on the test merchant information you want to manage. API tokens are scoped to grant specific permissions to make sure that apps only have access to the resources they need. 
8. Click **Create Token**. The new token displays in the Tokens section. Use this token as the Bearer token to make calls to the Clover Platform API endpoints.
9. Expand the Permissions section to view or edit the permissions associated with the API token.
