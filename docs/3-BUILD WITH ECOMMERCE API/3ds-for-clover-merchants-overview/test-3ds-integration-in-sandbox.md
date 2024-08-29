---
title: "Test 3DS integration"
slug: "test-3ds-integration-in-sandbox"
excerpt: ""
hidden: true
metadata: 
  description: "Learn how to test 3DS in sandbox and production."
  image: []
  robots: "index"
createdAt: "Mon Apr 15 2024 05:13:47 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue May 28 2024 05:56:19 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\" description\" content= \"Learn how to test 3DS in sandbox and production.\" >\n<!--This topic will be embeded to 3DS commercialization topic as as subtopic (DS-4968)-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

You can use test cards specially designed for testing 3-D Secure (3DS) integration and specific scenarios in the sandbox.

### Sandbox

The sandbox environment provides elements of the 3DS infrastructure, and you can use specific test cards for specific responses.

The following test cards are available for 3DS integration testing:

[block:parameters]
{
  "data": {
    "h-0": "Card issuer",
    "h-1": "Card number",
    "h-2": "Expected response",
    "0-0": "American Express<sup>®</sup>",
    "0-1": "3566007770017510",
    "0-2": "Successful response without authentication challenge",
    "1-0": "American Express",
    "1-1": "373953192351004",
    "1-2": "Successful response following successful authentication",
    "2-0": "Discover<sup>®</sup>",
    "2-1": "6011000991300009",
    "2-2": "Successful response without authentication challenge",
    "3-0": "Discover",
    "3-1": "6011000990099818",
    "3-2": "Successful response following successful authentication",
    "4-0": "Discover",
    "4-1": "6011000990139424",
    "4-2": "Successful response following authentication challenge",
    "5-0": "Discover",
    "5-1": "6011000990099818",
    "5-2": "Successful response following authentication challenge",
    "6-0": "Mastercard<sup>®</sup>",
    "6-1": "5424180279791732",
    "6-2": "Successful response without authentication challenge",
    "7-0": "Mastercard",
    "7-1": "5102610000000051",
    "7-2": "Authentication attempted",
    "8-0": "Mastercard",
    "8-1": "5431111111111111",
    "8-2": "Successful response following authentication challenge",
    "9-0": "Mastercard",
    "9-1": "5123455806308521",
    "9-2": "Successful response without authentication challenge",
    "10-0": "Mastercard",
    "10-1": "5123459046058920",
    "10-2": "Authentication failed",
    "11-0": "Visa<sup>®</sup>",
    "11-1": "4012000033330020",
    "11-2": "Successful response without authentication challenge",
    "12-0": "Visa",
    "12-1": "4005519200000004",
    "12-2": "Successful response following authentication challenge",
    "13-0": "Visa",
    "13-1": "4264281511112228",
    "13-2": "Authentication failed",
    "14-0": "Visa",
    "14-1": "4012002000992200",
    "14-2": "Successful response following authentication challenge",
    "15-0": "Visa",
    "15-1": "4500000000200045",
    "15-2": "Successful response following authentication challenge",
    "16-0": "Visa",
    "16-1": "4999999999999103",
    "16-2": "Successful response following authentication challenge",
    "17-0": "Visa",
    "17-1": "4111111111111111",
    "17-2": "Authentication attempted",
    "18-0": "Visa",
    "18-1": "4242424242424242",
    "18-2": "Successful response without authentication challenge",
    "19-0": "Visa",
    "19-1": "4001230000000129",
    "19-2": "Successful response without authentication challenge",
    "20-0": "Visa",
    "20-1": "4811326490014875",
    "20-2": "Successful response following authentication challenge",
    "21-0": "Visa",
    "21-1": "4043130007524792",
    "21-2": "Successful response following authentication challenge"
  },
  "cols": 3,
  "rows": 22,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


### Production

3DS testing in the production environment requires active cards, a suitable merchant account, and an available acquirer for the transactions.

Depending on the card issuer, your card may be required to pass authentication challenges in the production environment.

> 📘 TIP
> 
> Clover recommends testing your active cards with a few transactions and a lesser amount to reduce fraud in the production environment.
