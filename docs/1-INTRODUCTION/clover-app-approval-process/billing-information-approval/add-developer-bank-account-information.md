---
title: "Add developer bank account information"
slug: "add-developer-bank-account-information"
excerpt: ""
hidden: false
metadata: 
  description: "As a Clover developer, you need to submit your bank account information to Clover. Read more on how to add US, Canada, or International bank account details in the Clover production Developer Dashboard."
  image: []
  robots: "index"
createdAt: "Thu Feb 01 2024 08:19:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 29 2024 23:40:18 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<!--https://confluence.corp.clover.com/display/DES/Developer+Bank+Account+Update+-Design+Documentation-->\n<!--DS-2196; Editorial review and image update for purple box-->\n<!--DS-5454-->\n<!--DS-5607; QC complete 2.29.2024-->\n\n<meta name=\" description\" content= \"As a Clover developer, you need to submit your bank account information to Clover. Read more on how to add US, Canada, or International bank account details in the Clover production Developer Dashboard.\" >\n"
}
[/block]


## Prerequisites

- Complete the developer identity verification process. For more information, see [Developer account for approval](https://docs.clover.com/docs/developer-account-approval).
- Create a developer account with an Admin or Owner role with permission to access bank details. For more information, see [Developer account roles](https://docs.clover.com/docs/developer-account-roles#create-a-custom-role).
- [Set up two-factor authentication (2FA)](https://docs.clover.com/docs/set-up-two-factor-authentication-2fa).

## Add developer bank account information

1. Log in to the production Developer Dashboard.  
   If you do not have a production Clover developer account, [create an account](https://docs.clover.com/docs/developer-accounts) in your region.
2. From the left navigation menu, click **Developer Settings** > **Info**. The Developer Info page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8e4deed-Add-Bank-Account.png",
        null,
        "Developer Settings > Info > Developer Info page"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Developer Settings > Info > Developer Info page"
    }
  ]
}
[/block]


3. In the Bank Details section, click **Add Bank Account**. The two-factor authentication (2FA) process starts:
   - If you need to complete the 2FA process, a pop-up to set up two-factor authentication appears. See  [Set up two-factor authentication (2FA)](https://docs.clover.com/docs/set-up-two-factor-authentication-2fa).
   - If you completed the 2FA process, the Enter the verification code pop-up appears.
4. Complete the authentication process. The Step 1: Account Type page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d33f7df-1-AccntType.png",
        "",
        "Choose your account type page"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Choose your account type page"
    }
  ]
}
[/block]


5. Select an account type: **United States or Canada** or **International bank account**, and then select bank identifiers based on the selected country to:

- [Add a US or Canada routing number](https://docs.clover.com/docs/add-developer-bank-account-information#add-a-us-or-canada-routing-number)
- [Add an International Bank Account Number (IBAN)](https://docs.clover.com/docs/add-developer-bank-account-information#add-an-international-bank-account-number-iban)
- [Add a SWIFT/Bank Identifier Code (BIC)](https://docs.clover.com/docs/add-developer-bank-account-information#add-a-swiftbank-identifier-code-bic)
- [Add a SORT Code - United Kingdom](https://docs.clover.com/docs/add-developer-bank-account-information#add-a-sort-code---united-kingdom)

> 📘 IMPORTANT
> 
> All bank details information you enter are self-validated and required so add or update the correct bank account information.

***

### Add a US or Canada routing number

After you log in to your production Developer account to [add developer bank account information](https://docs.clover.com/docs/add-developer-bank-account-information#add-developer-bank-account-information), complete the three steps to add bank account details:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/267aba8-1-AccntType-US.png",
        "",
        "Choose your account type: United States or Canada"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Choose your account type: United States or Canada"
    }
  ]
}
[/block]


**Step 1: Account Type**—On the Choose your account type page:

1. Select the option: **United States or Canada**.
2. Click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/73cfc1d-2-BankDetails-US.png",
        "",
        "Add your bank details: US or Canada routing number"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Add your bank details: US or Canada routing number"
    }
  ]
}
[/block]


**Step 2: Bank details**—On the Add your bank details page:

1. Enter bank details in the following fields—Country, Account name, Account type (Savings or Checkings), Routing number, and Account number.  
   **Length: ** Account number for:
   - United States (US) bank account is 4- to 12-digit. 
   - Canada or an International bank account is 4- to 100-digit.
2. Click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f5c04b0-3-Review-US.png",
        "",
        "Review and confirm: US and Canada routing number"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Review and confirm: US and Canada routing number"
    }
  ]
}
[/block]


**Step 3: Review and confirm**—On the Review and confirm page:

1. Review the bank account information.
2. If any changes are needed, click **Back** to go to a previous step.
3. If all information is correct, click **Confirm**. The Developer Account Information page displays a confirmation message with the approximate time by which the new bank account will be updated in your developer account records with Clover.

***

### Add an International Bank Account Number (IBAN)

After you log in to your production Developer account to [add developer bank account information](https://docs.clover.com/docs/add-developer-bank-account-information#add-developer-bank-account-information), complete the three steps to add bank account details:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c2a2ede-1-AccntType-Intl.png",
        "",
        "Choose your account type: International"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Choose your account type: International"
    }
  ]
}
[/block]


**Step 1: Account Type**—On the Choose your account type page:

1. Select the option: **International bank account**.
2. Click **Next**. The Select the bank identifier page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8367947-1-AccntType-IBAN.png",
        "",
        "Select the bank identifier type: IBAN"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Select the bank identifier type: IBAN"
    }
  ]
}
[/block]


3. Select the option: **International Bank Account Number (IBAN)**.
4. Click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8233137-2-BankDetails-IBAN.png",
        "",
        "Add your bank details: IBAN"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Add your bank details: IBAN"
    }
  ]
}
[/block]


**Step 2: Bank details**—On the Add your bank details page:

1. Enter bank details in the following fields—Account name, IBAN, and the Bank identifier code.
2. Click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ab061e0-3-Review-IBAN.png",
        "",
        "Review and confirm: IBAN"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Review and confirm: IBAN"
    }
  ]
}
[/block]


**Step 3: Review and confirm**—On the Review and confirm page:

1. Review the bank account information.
2. If any changes are needed, click **Back** to go to a previous step.
3. If all information is correct, click **Confirm**. The Developer Account Information page displays a confirmation message with the approximate time by which the new bank account will be updated in your developer account records with Clover.

***

### Add a SWIFT/Bank Identifier Code (BIC)

After you log in to your production Developer account to [add developer bank account information](https://docs.clover.com/docs/add-developer-bank-account-information#add-developer-bank-account-information), complete the three steps to add bank account details:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c2a2ede-1-AccntType-Intl.png",
        "",
        "Choose your account type: International"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Choose your account type: International"
    }
  ]
}
[/block]


**Step 1: Account Type**—On the Choose your account type page:

1. Select the option: **International bank account**.
2. Click **Next**. The Select the bank identifier page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a1db76b-1-AccntType-SWIFT.png",
        "",
        "Select the bank identifier type: SWIFT/BIC"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Select the bank identifier type: SWIFT/BIC"
    }
  ]
}
[/block]


3. Select the option: **SWIFT/Bank Identifier Code (BIC)**.
4. Click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/62a8bde-2-BankDetails-SWIFT.png",
        "",
        "Add your bank details: SWIFT/BIC"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Add your bank details: SWIFT/BIC"
    }
  ]
}
[/block]


**Step 2: Bank details**—On the Add your bank details page:

1. Enter bank details in the following fields—Account name,  Account number, and SWIFT or Bank identifier code.
2. Click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/450ef57-3-Review-SWIFT.png",
        "",
        "Review and confirm: SWIFT/BIC"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Review and confirm: SWIFT/BIC"
    }
  ]
}
[/block]


**Step 3: Review and confirm**—On the Review and confirm page:

1. Review the bank account information.
2. If any changes are needed, click **Back** to go to a previous step.
3. If all information is correct, click **Confirm**. The Developer Account Information page displays a confirmation message with the approximate time by which the new bank account will be updated in your developer account records with Clover.

***

### Add a SORT Code - United Kingdom

After you log in to your production Developer account to [add developer bank account information](https://docs.clover.com/docs/add-developer-bank-account-information#add-developer-bank-account-information), complete the three steps to add bank account details:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c2a2ede-1-AccntType-Intl.png",
        "",
        "Choose your account type: International"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Choose your account type: International"
    }
  ]
}
[/block]


**Step 1: Account Type**—On the Choose your account type page:

1. Select the option: **International bank account**.
2. Click **Next**. The Select the bank identifier page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4efa741-1-AccntType-SortCode.png",
        "",
        "Select the bank identifier type: Sort code - UK"
      ],
      "align": "center",
      "border": true,
      "caption": "Select the bank identifier type: Sort code - United Kingdom"
    }
  ]
}
[/block]


3. Select the option: **Sort Code - United Kingdom**.
4. Click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3125802-2-BankDetails-SortCode.png",
        "",
        "Add your bank details: Sort code - UK"
      ],
      "align": "center",
      "sizing": "98% ",
      "border": true,
      "caption": "Add your bank details: Sort code - UK"
    }
  ]
}
[/block]


**Step 2: Bank details**—On the Add your bank details page:

1. Enter bank details in the following fields—Account name,  Account number, and Sort code.
2. Click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bbe4c4d-3-Review-SortCode.png",
        "",
        "Review and confirm: Sort code - UK"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Review and confirm: Sort code - UK"
    }
  ]
}
[/block]


**Step 3: Review and confirm**—On the Review and confirm page:

1. Review the bank account information.
2. If any changes are needed, click **Back** to go to a previous step.
3. If all information is correct, click **Confirm**. The Developer Account Information page displays a confirmation message with the approximate time by which the new bank account will be updated in your developer account records with Clover.

After you add the bank account, you can set up a monthly subscription and metered pricing tiers for your paid app. For more information, see [Set up pricing tiers](https://docs.clover.com/docs/configuring-billing).

## Related topics

- [Manage developer bank account information](https://docs.clover.com/docs/billing-information-approval)
- [Update developer bank account information](https://docs.clover.com/docs/update-developer-bank-account-information)
