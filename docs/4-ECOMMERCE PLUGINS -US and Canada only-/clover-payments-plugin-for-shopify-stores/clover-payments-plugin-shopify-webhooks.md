---
title: "Compliance webhooks for Clover payments plugin"
slug: "clover-payments-plugin-shopify-webhooks"
excerpt: ""
hidden: true
metadata: 
  description: "Learn about Shopify mandatory compliance webhooks and the actions that Clover needs to take when a merchant requests for customer data or deletion of customer data, or uninstalls the Clover payments plugin for a Shopify Online Shop."
  image: []
  robots: "index"
createdAt: "Wed May 29 2024 05:35:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jul 17 2024 03:23:05 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content="Learn about Shopify mandatory compliance webhooks and the actions that Clover needs to take when a merchant requests for customer data or deletion of customer data, or uninstalls the Clover payments plugin for a Shopify Online Shop." >

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]{"html":"<!--Add a top nav for all related topics-->\n<div><!--div set-->\n <div class=\"top-container\">\n    <div class=\"topnav\">\n      <a href=\"https://docs.clover.com/docs/clover-payments-plugin-for-shopify-stores\">Clover Payments plugin for Shopify Online Shop</a>\n      <a href=\"https://docs.clover.com/docs/integrate-clover-payments-with-shopify\">Integrate Clover Payments with Shopify Online Shop</a>\n      <a href=\"https://docs.clover.com/docs/clover-payments-plugin-shopify-webhooks\">Compliance webhooks</a>\n   \n    </div><!--end topnav-->\n  </div><!--end top-container-->\n</div>\n\n<!--css-->\n<style>\n/* Add a background color to the top navigation */\n.topnav {\n  font-family: 'Graphik-Regular', sans-serif;\n  background-color: #5D5D5D;\n  overflow: hidden;\n}\n\n/* Style the links inside the navigation bar */\n.topnav a {\n  font-family: 'Graphik-Regular', sans-serif;\n  float: left;\n  color: #f2f2f2;\n  text-align: center;\n  padding: 10px 12px;\n  text-decoration: none;\n  font-size: 12px;\n}\n\n/* Change the color of links on hover */\n.topnav a:hover {\n  background-color: #D8D8D8;\n  color: black;\n}\n\n/* Add a color to the active/current link */\n.topnav a.active {\n  background-color: #5D5D5D;\n  color: white;\n}\n</style>"}[/block]

# Data privacy rules and regulations

Privacy laws, such as the General Data Protection Regulation (GDPR), impose requirements on entities that handle personal data. These regulations apply to parties that collect, store, or process personal information about individuals and are required when working with merchants in Europe. Shopify requires mandatory compliance <<glossary:webhooks>> or callback methods that help manage the personal data collected by an app.

# Types of compliance webhooks

The Clover Payments plugin needs to support the three types of webhooks from Shopify:

[block:parameters]
{
  "data": {
    "h-0": "Merchant request",
    "h-1": "Shopify webhook",
    "h-2": "Description",
    "h-3": "Clover action",
    "0-0": "Request to access stored customer data.",
    "0-1": "customers/data_request",
    "0-2": "Customers for a merchant with a Shopify Online Shop can request to view customer data stored on Clover. The merchant must have an authorized or owner role to generate this request from the Shopify Dashboard.",
    "0-3": "1. Send `200` response to Shopify.  \n2. Send an acknowledgment email to the merchant with a link to the [Fiserv form](https://docs.clover.com/docs/clover-payments-plugin-shopify-webhooks#fiserv-form-field-descriptions) requesting customer information.  \n3. Send an email to the merchant to confirm or reject the request based on information in the Fiserv form.",
    "1-0": "Request to delete customer data with Clover.",
    "1-1": "customers/redact",
    "1-2": "Merchants with a Shopify Online Shop can request that customer data be deleted from the Shopify platform. The merchant must have an authorized or owner role to generate this request from the Shopify Dashboard.  \n**Note: **If the customer is associated with multiple merchantIds, only the customer for <<glossary:merchantId>> associated with the Shopify Online Shop is deleted.",
    "1-3": "1. Send `200` response to Shopify.  \n2. Send an acknowledgment email to the merchant with a link to the [Fiserv form](https://docs.clover.com/docs/clover-payments-plugin-shopify-webhooks#fiserv-form-field-descriptions) requesting customer information.  \n3. Send an email to the merchant to confirm or reject the request based on information in the Fiserv form.",
    "2-0": "Request to delete Shopify Online Shop data from the Clover payment method.",
    "2-1": "shop/redact",
    "2-2": "Merchants with a Shopify Online Shop can request to:  \n  \n- deactivate the payment method or uninstall the app  \n- change the payment provider",
    "2-3": "1. Send `200` response to Shopify.  \n2. Terminate the OAuth flow between the Clover Merchant and the Shopify Online Shop.  \n3. Send an email to the merchant to confirm or reject the request."
  },
  "cols": 4,
  "rows": 3,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


***

# Clover - Shopify webhook process

1. Merchant requests one of the following on the Shopify Online Shop Dashboard—customer data, customer data deletion request, or store deactivation request.
2. Shopify invokes the related webhook—customers/data request, customers/redact, or shop/redact. For more information, see [Mandatory compliance webhooks](https://shopify.dev/docs/apps/build/privacy-law-compliance#mandatory-compliance-webhooks).
3. Clover sends `200` response to acknowledge the request in the webhook from Shopify.
4. Clover sends an email to the Clover merchant owner with the link to a [Fiserv form](https://docs.clover.com/docs/clover-payments-plugin-shopify-webhooks#fiserv-form-field-description) that the merchant needs to complete.
5. Clover reviews the information in the form and decides on the next action.
6. Clover sends an email to the listed merchant owner's account to confirm or reject the customer's request.
7. Clover maintains the records of the requests and required emails.

# Fiserv form field descriptions

The merchant can click the link to the Fiserv form in the email from Clover and complete the form as follows:

[block:parameters]
{
  "data": {
    "h-0": "Fiserv form",
    "h-1": "",
    "0-0": "**Field**",
    "0-1": "**Description**",
    "1-0": "Please select your country",
    "1-1": "Enter the country where the merchant is located, and then enter the State.",
    "2-0": "Please select your relationship to Fiserv",
    "2-1": "Select the option: Consumer/Cardholder",
    "3-0": "Please select your request type",
    "3-1": "Select one of the options:  \n  \n- Access my data—to request customer data  \n- Delete my data—to request deletion of customer data",
    "4-0": "Please select the Fiserv product to which your request relates to",
    "4-1": "Select **Clover**.",
    "5-0": "Please provide your mobile number",
    "5-1": "Enter the merchant's mobile number. ",
    "6-0": "Order ID/Payment ID or Clover app user ID",
    "6-1": "Enter the <<glossary:merchantId>>.",
    "7-0": "First name",
    "7-1": "Enter the customer's first name.",
    "8-0": "Last name",
    "8-1": "Enter the customer's last name.",
    "9-0": "Email",
    "9-1": "Enter the customer's email address.",
    "10-0": "Please re-type email address",
    "10-1": "Re-enter the customer's email address.",
    "11-0": "If known, please select the business your request is related to",
    "11-1": "Select **Clover**.",
    "12-0": "Please provide a brief description of your request",
    "12-1": "Enter information such as justification for requesting customer data or deletion of customer data.",
    "13-0": "reCAPTCHA",
    "13-1": "Select the **I am not a robot** checkbox.",
    "14-0": "Submit",
    "14-1": "Click **Submit** to send the completed form to Clover."
  },
  "cols": 2,
  "rows": 15,
  "align": [
    "left",
    "left"
  ]
}
[/block]


<!--

 

Hide until we publish the webhooks topic:

# Related topics

- [Ecommerce (US and Canada only) - Clover Payments plugin](https://docs.clover.com/docs/clover-payments-plugin-for-shopify-stores)
- [Integrate Clover Payments with Shopify Online Shop](https://docs.clover.com/docs/integrate-clover-payments-with-shopify)

\-->
