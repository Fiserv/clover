---
title: "Set up the SDK"
slug: "setting-up-the-sdk"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides instructions for setting up a Clover Ecommerce SDK with your app."
  image: 
    - "https://files.readme.io/29be1d0-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue May 05 2020 16:51:05 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 08:48:08 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# Install the SDK

Use a package manager to download and install the SDK you want to use.

```shell Python
pip install ecommClover
```
```shell Node
yarn add clover-ecomm-sdk
```

# Configure the SDK

To use the SDK, you'll need to configure it using the following values:

- Your test merchant's `access_token` retrieved from the OAuth flow. See [Authenticate with OAuth—Canada and US](https://docs.clover.com/docs/use-oauth).
- Your test merchant's public key obtained using the [`pakms/apikey`] \(<https://docs.clover.com/reference/getapikey>) endpoint)  
  The `access_token` is needed to initialize the SDK.

```python
clover.access_token = "Bkk321..."
```
```javascript Node
const clover = require('clover-ecomm-sdk')('Bkk312...');
```

The merchant's public key is required to tokenize the customer's card data. 

```python
clover.api_key = "fhjk1..."
```
```javascript Node
const API_KEY = 'fhjk1...';
```

# Set environment variables in Node

If your app is using the Node SDK,  create a `.env` file in your project root directory.

```javascript .env file
ACCESS_TOKEN={access_token}
API_KEY={api_key}
ENVIRONMENT=sandbox
```

> 📘 NOTE
> 
> For your app in production environments, set the `ENVIRONMENT` as `production`.
