---
title: "Transfer developer account ownership"
slug: "transfer-developer-ownership"
excerpt: ""
hidden: false
metadata: 
  description: "Want to transfer your Clover developer account ownership? Learn how to do it in a few easy steps."
  image: []
  robots: "index"
createdAt: "Mon May 01 2023 06:46:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 12 2024 12:48:19 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Owners are generally the super users of the developer account and have access to everything from accepting release agreements to editing developer release groups. They receive all communications and notifications related to the respective account.

## Developer Ownership transfer process

Based on your role, you can initiate or request developer ownership transfer from the Developer Dashboard only in the production environment.

- If you are the current owner of the developer account, you can initiate and complete the ownership transfer process.
- If you are an active admin, you can request for ownership transfer.

See [Developer account roles](https://docs.clover.com/docs/developer-account-roles) for more information.

## Prerequisite

[Set up two-factor authentication (2FA)](https://docs.clover.com/docs/set-up-two-factor-authentication-2fa).

## Transfer developer ownership as a current owner

1. Log into the [Developer Dashboard](https://www.clover.com/developer-home/login).
2. From the left navigation menu, click **Developer Settings **> **Members**. The Members page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9dfa6f3-Memebers-Owners.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "800px",
      "border": true
    }
  ]
}
[/block]


3. Click the vertical ellipsis next to the member's name to transfer account ownership.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1171e6e-Memebers-Owners_menu.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "800px",
      "border": true
    }
  ]
}
[/block]


4. Click **Transfer Ownership**. The two-factor authentication (2FA) process starts.  
   If you have not completed the 2FA process, see [Set up two-factor authentication (2FA)](https://docs.clover.com/docs/set-up-two-factor-authentication-2fa).
5. Complete the 2FA process. The **Are you sure you want to transfer the ownership?** pop-up appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0fe1cba-Are_you_sure.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "350px",
      "border": true
    }
  ]
}
[/block]


6. Click **Yes, transfer ownership**. When account ownership is successfully transferred, you are logged out of the application, and your role changes to admin. You also receive a confirmation email.

## Request developer ownership transfer as admin

An admin can only submit the ownership transfer request once in 24 hours.

1. Log into the [Developer Dashboard](https://www.clover.com/developer-home/login).
2. From the left navigation menu, click **Developer Settings **> **Members**. The Members page appears.
3. Click the vertical ellipsis next to the member's name to transfer account ownership.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/58f2bd0-Request_ownership.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "800px",
      "border": true
    }
  ]
}
[/block]


4. Click **Request Ownership**. A message appears—_Ownership transfer request sent to the current owner._—and you receive:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3933579-Successful_message.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "800px",
      "border": true
    }
  ]
}
[/block]


- Confirmation email that you have initiated the ownership transfer request. The current owner also receives an email to complete the ownership transfer process.
- Confirmation email on the successful completion of the account ownership transfer.  
  **Note:** If you do not receive any update within 14 working days from the ownership request initiation, email: <a href="mailto:developer-relations@devrel.clover.com">developer-relations@devrel.clover.com</a>.
