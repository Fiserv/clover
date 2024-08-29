---
title: "Update developer bank account information"
slug: "update-developer-bank-account-information"
excerpt: ""
hidden: false
metadata: 
  description: "As a Clover developer, you need to submit your bank account information to Clover. Read more on how to update US, Canada, or International bank account details in the Clover production Developer Dashboard."
  image: []
  robots: "index"
createdAt: "Thu Feb 01 2024 08:21:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 10 2024 22:22:23 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<!--https://confluence.corp.clover.com/display/DES/Developer+Bank+Account+Update+-Design+Documentation-->\n<!--DS-2196; Editorial review and image update for purple box-->\n<!--DS-5454-->\n<!--DS-5607; QC complete 2.29.2024-->\n\n<meta name=\" description\" content= \"As a Clover developer, you need to submit your bank account information to Clover. Read more on how to update US, Canada, or International bank account details in the Clover production Developer Dashboard.\n\" >\n"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

## Prerequisites

Verified developer account with at least one bank account added. See [Add developer bank account information](https://docs.clover.com/docs/add-developer-bank-account-information).

## Update developer bank account information

1. Log in to the production Developer Dashboard.
2. From the left navigation menu, click **Developer Settings** > **Info**. The Developer Info page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f6205b1-Edit-Bank-Details.png",
        "",
        "Developer Info page > Edit Banking Details"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Developer Info page > Edit Banking Details"
    }
  ]
}
[/block]


3. In the Bank Details section, click the edit icon. The two-factor authentication (2FA) process starts:
   - If you need to complete the 2FA process, a pop-up to set up two-factor authentication appears. See [Set up two-factor authentication (2FA) process](https://docs.clover.com/docs/set-up-two-factor-authentication-2fa).
   - If you completed the 2FA process, the Enter the verification code pop-up appears.
4. Complete the two-factor authentication process. The Banking Details page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d8dbc18-ChangeBankAcct.png",
        "",
        "Banking Details page"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Banking Details page: Change bank account"
    }
  ]
}
[/block]


5. In the Actions column, click **Change bank account**. The Choose your account type page appears.
6. Complete the three steps to update the bank account details:

**Step 1: Account type**

1. Select an option and click **Next**:

- United States or Canada
- International

2. If you select** International**, then you need to select a bank identifier type:

- International Bank Account Number (IBAN)
- SWIFT/Bank Identifier Code (BIC)
- Sort code: United Kingdom

3. Click **Next**.

**Step 2: Bank details**

1. Review and update bank details based on the option you selected in Step 1: Account type. All fields are self-validated and required. Be careful to update the correct bank account information.

- **United States and Canada routing number**—Country, Account name, Account type (Savings or Checkings), Routing number, and Account number.
- **International Bank Account Number (IBAN)**—Account name, IBAN, and the Bank identifier code.
- **SWIFT/Bank Identifier Code (BIC)**—Account name, Account number, and SWIFT/Bank identifier code.
- **Sort code: United Kingdom**—Account name, Account number, and Sort code.

2. Click **Next**.

**Step 3: Review and confirm**

1. Review the updated account information.
2. If any changes are needed, click **Back** to go to a previous step.
3. If all information is correct, click **Confirm**. The Developer Account Information page displays a confirmation message with the approximate time by which the new bank account will be updated in your developer account records with Clover.

## Support information

Clover sends an email informing you that your Clover Developer Dashboard bank information is updated. For any questions related to the bank account update, you can send an email to [developer-relations@devrel.clover.com](mailto:developer-relations@devrel.clover.com).

## Related topics

- [Manage developer bank account information](https://docs.clover.com/docs/billing-information-approval)
- [Add developer bank account information](https://docs.clover.com/docs/add-developer-bank-account-information)
