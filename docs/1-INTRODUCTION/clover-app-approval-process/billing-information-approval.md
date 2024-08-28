---
title: "Manage developer bank account information"
slug: "billing-information-approval"
excerpt: ""
hidden: false
metadata: 
  description: "If you have paid apps on the Clover App Market, you need to submit your bank account information to Clover. Read more on how to add and update your bank account in the Clover production Developer Dashboard."
  image: []
  robots: "index"
createdAt: "Wed Jul 10 2019 17:31:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 12 2024 12:46:30 GMT+0000 (Coordinated Universal Time)"
---
<meta name=" description" content= "If you have paid apps on the Clover App Market, you need to submit your bank account information to Clover. Read more on how to add and update your bank account in the Clover production Developer Dashboard." >

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<!--https://confluence.corp.clover.com/display/DES/Developer+Bank+Account+Update+-Design+Documentation-->\n<!--DS-2196-->\n<!--DS-5454-->\n<!--DS-5607 Completed QC 02.29.2024-->\n"
}
[/block]


You need to add bank account details to your verified Clover developer account to receive disbursements from Clover. You can add or update account bank details on the Developer Settings page on your production Developer Dashboard.

## Before you begin

Note the following:

- Clover supports only direct bank deposits and one bank account per developer account. It does not support any cash or check deposits. Make sure your bank account is always up-to-date on your Developer Dashboard.
- Clover recommends maintaining the current bank account linked to your developer account as open and active to avoid payment failure due to billing cycle nuances.
- Clover lets you directly update the bank account details in the Developer Dashboard. You do not need to send an email to the Developer Relations team for bank account updates.

## How Clover uses developer  bank account information

Clover uses the bank account information to:

- Pay your share from payments collected from merchants or businesses using your apps.
- Accept app fees in compliance with the Clover App Market Developer terms:
  - [US and Canada Clover App Market Developer Terms](https://www.clover.com/developer-agreement)
  - [Europe Clover App Market Developer Terms](https://eu.clover.com/developer-agreement)

## Terminology

[block:parameters]
{
  "data": {
    "h-0": "Term",
    "h-1": "Description",
    "0-0": "BIC",
    "0-1": "Bank Identifier Code. BIC is a unique code that is assigned to each bank or financial institution that participates in the SWIFT network. The code is used to identify banks and financial institutions globally and is required for international wire transfers.  \n**Format: **8- or 11-character code to indicate the business party identifier that consists of the:  \n  \n- Business party prefix (4 alphanumeric characters),  \n- Country code defined in the ISO 3166-1 (2 upper case alphabets), and  \n- Business party suffix (2 or 5 alphanumeric characters)  \n  **Example: **HBUKGB4B  \n  See [BIC used for international money transfers](https://www.bankrouting.ca/bic-codes).",
    "1-0": "IBAN",
    "1-1": "International Bank Account Number. IBAN is a unique identifier that is assigned to bank accounts across countries that participate in the IBAN system. It is used to facilitate international money transfers.  \n**Format: **First 2 digits indicate the country code.  \nSee [List of countries using the IBAN standard](https://bank-code.net/iban/country-list).",
    "2-0": "Routing number",
    "2-1": "United States (US) routing number is also known as an ABA (American Bankers Association) number or ACH (Automated Clearing House) number. It uniquely identifies a specific financial institution and its branch location and is used for various transactions, including direct deposits, recurring payments, and wire transfers.  \n**Format: **9-digit  \nSee [Routing Number & Bank Account Lookup](https://www.routingnumber.com/).  \n  \nCanada routing number is used for electronic fund transfers (EFT), such as direct deposits, pre-authorized debits (PAD), bill payments, and bank-to-bank transfers.  \n**Format: **9-digit, starting with 0 (zero)  \nSee [Canada Bank Routing Number](https://www.bankrouting.ca/routing-number-lookup).",
    "3-0": "Sort code",
    "3-1": "Domestic bank codes to route money transfers between financial institutions in the United Kingdom. The sort code identifies a bank and branch and is available on bank statements and checks.  \n**Format:** 6-digit  \nSee [Sort codes for banks in the United Kingdom](https://bank-code.net/uk-sort-code).",
    "4-0": "SWIFT",
    "4-1": "Society for Worldwide Interbank Financial Telecommunication. SWIFT is a global network that facilitates secure financial transactions between banks and financial institutions. SWIFT assigns a unique code to each bank, known as the Bank Identifier Code (BIC) or SWIFT code. The code is used to identify banks and financial institutions globally and is required for international wire transfers.  \n**Format: **8- or 11-character code to indicate the business party identifier that consists of the:  \n  \n- Business party prefix (4 alphanumeric characters),  \n- Country code defined in the ISO 3166-1 (2 upper case alphabets), and  \n- Business party suffix (2 or 5 alphanumeric characters)  \n  **Example: **HBUKGB4B  \n  See [What is a SWIFT/BIC code?](https://bank-code.net/)"
  },
  "cols": 2,
  "rows": 5,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Manage developer bank account information

- [Add developer bank account information](https://docs.clover.com/docs/add-developer-bank-account-information)
- [Update developer bank account information](https://docs.clover.com/docs/update-developer-bank-account-information)
