---
title: "Make a sample REST API call"
slug: "make-a-rest-api-call"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to make a sample Clover REST API call and retrieve your test merchant's name."
  image: []
  robots: "index"
createdAt: "Tue Aug 21 2018 18:54:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Aug 09 2024 08:55:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Learn how to make a sample Clover REST API call and retrieve your test merchant's name.”>"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover REST API lets you query relevant information about Clover merchants in your web app. Relevant information, such as merchant inventory, orders, and payments, is available using our REST API. An endpoint represents each type of merchant information.

Use the [Android emulator](doc:setting-up-an-android-emulator) or [Developer Kits](https://cloverdevkit.com/) in the sandbox environment for building and testing your apps with test merchants. For your Android app, you can [generate an API token and query web services](doc:query-web-services) using the Clover Android SDK.

Use the following procedure to make a sample API call using the [Clover API Reference](https://docs.clover.com/reference/api-reference-overview).

# Use the API Reference

## Prerequisites

To use the Clover platform API, you require the following:

- [Sandbox developer account](https://docs.clover.com/docs/create-a-sandbox-account)
- [Test merchant account](https://docs.clover.com/docs/use-test-merchants-dashboard)
- [Test API token](https://docs.clover.com/docs/generate-a-test-api-token) with permissions to make REST API requests and manage your test merchant's data.

## Make a sample REST API call

To make a sample REST API call using the Clover API reference:

1. From the Platform API left navigation, select **MERCHANTS > Get a single merchant**.
2. In the Authentication header > Bearer type field, enter your access token. The access token is the [test API token](https://docs.clover.com/docs/generate-a-test-api-token#generate-a-merchant-specific-test-api-token-in-sandbox) that you have generated in the sandbox Developer Dashboard.
3. In the Path Params section, enter your test <<glossary:merchantId>> in the `mId` field. Your test merchant ID is a 13-alphanumeric identifier that displays in the browser link (URL) of the Merchant Dashboard for your test merchant. See [Locate your test merchant ID](https://docs.clover.com/docs/merchant-id-and-api-token-for-development#locate-the-test-merchant-identifier-merchantid).
4. Click **Try It**. In the JSON output response, the `name` value is your test merchant’s name.

## Test Rest API calls with the sample inventory

1. Use the <a href= "https://clover.box.com/s/y08he8u7llov7shufskgyb5stlgcs6s8" target= "_blank">sample inventory file</a> to test more REST API calls for your test merchant. 
2. On the Merchant Dashboard, select the **Inventory** app, and then follow the instructions to upload the sample inventory file. See [Import inventory](https://docs.clover.com/docs/importing-inventory).

# Related topics

- [Use the Clover REST API](https://docs.clover.com/docs/making-rest-api-calls)
- [Generate a merchant-specific test API token](https://docs.clover.com/docs/generate-a-test-api-token)
- [Use test merchant identifier and API token](https://docs.clover.com/docs/merchant-id-and-api-token-for-development)
- [Redirect merchants to your app](https://docs.clover.com/docs/merchant-interaction)
