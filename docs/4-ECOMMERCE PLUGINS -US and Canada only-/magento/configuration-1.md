---
title: "Set up an Ecommerce API token"
slug: "configuration-1"
excerpt: ""
hidden: false
metadata: 
  description: "You can create public and private keys or API token in either the Clover sandbox or production environment."
  image: []
  robots: "index"
createdAt: "Mon Apr 04 2022 22:31:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jun 18 2024 10:26:19 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content=“API tokens secure the communication between an app integration and your merchant account. You can use an API token to integrate online payments with your e-commerce website. Learn how to create a public and private token for your iframe integration.">

[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023\n<!--March 27, 2024: replaced long custom html with \"regionicon-us-can\" reusable content. \nI still do not see how DS-4047 was actually resolved. \nThere are still multiple topics that appear redundant.-cd\n-->\n<!--18 June 2024-DS-6593; removed reference to Enable online card payments checkbox.-->\n"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

You can create public and private keys or API tokens in either the production or sandbox environment. API tokens secure the communication between an app integration and your merchant account. You can use an API token to integrate online payments with your e-commerce website. You can create only one Ecommerce API token per merchant account, but you can use the same token for multiple solutions. <!--source: Clover Online Help -->

To create public and private keys (API tokens):

1. Log in to your <<glossary:Developer Dashboard>>.
2. From the Developer Account drop-down list, select a merchant name under Businesses. The Merchant Dashboard for the selected merchant appears.
3. From the left navigation menu, click **Account & Setup**. The Account & Setup page appears.
4. In the Ecommerce section, click **Ecommerce API Tokens**. 

[block:image]{"images":[{"image":["https://files.readme.io/8d2a911-Ecommerce-API-Tokens-MerchDashboard.png","Ecomm-API.png",2164],"align":"center","sizing":"100% ","border":true,"caption":"Merchant Dashboard > Account & Setup > Ecommerce > Ecommerce API Tokens"}]}[/block]

The Ecommerce API Tokens page displays any existing API tokens and to create a new token you have to delete the existing token. If you have not created any API tokens, the Tokens section on the page is blank.

[block:image]{"images":[{"image":["https://files.readme.io/ebf39b9-CreateNewToken-EcommAPI.png","CreateToken-Blank.png",1294],"align":"center","sizing":"100% ","border":true,"caption":"Ecommerce API Tokens > Create new token"}]}[/block]

5. Click **Create New Token**. The Create new token pop-up appears.

[block:image]{"images":[{"image":["https://files.readme.io/bd742ae-CreateNewToken-EcommerceAPI.png","CreateToken.png",812],"align":"center","sizing":"40% ","border":true,"caption":"Create new token pop-up"}]}[/block]

6. Verify or select the Integration type as **Hosted iFrame + API/SDK**. This is a closer integration with your website that allows for more customization and lets you define the checkout fields, all styled using your cascading style sheets (CSS). For more information, see [Clover iframe integrations](https://docs.clover.com/docs/clover-iframe-integrations).
7. Click **Create Token**. The API tokens page displays the public and private keys (tokens) you need to use when entering the Clover Payment configuration. 

[block:image]{"images":[{"image":["https://files.readme.io/f43bd73-iFrame-APIToken.png","Token.png",2512],"align":"center","sizing":"100% ","border":true,"caption":"Ecommerce API Tokens for iframe integration type"}]}[/block]

8. Copy the public and private tokens and paste them into the Adobe Commerce Configuration page. See [Configure the Clover Payment Extension](https://docs.clover.com/docs/configuration).
