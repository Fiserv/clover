---
title: "Submit developer account for approval"
slug: "developer-account-approval"
excerpt: ""
hidden: false
metadata: 
  description: "Clover requires developer accounts to be vetted and approved to ensure the security of merchant and customer data. Read more about the account submissions and approval process on this page."
  image: 
    - "https://files.readme.io/4665f80-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Wed Jul 10 2019 17:23:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jul 17 2024 04:53:38 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--JIRA DS-4297; Rewritten and improved content and images; redirected to transfer ownership topic-->"
}
[/block]


Clover must verify and approve your production developer account before starting the process to approve your app. Your app is linked to your approved production developer account. 

## Before you begin

1. Choose your region:

- **North America**—To build an integration for the North America region, [create a global developer account](https://docs.clover.com/docs/gdp-create-global-developer-account). 
- **Europe and Latin America**—To create apps for the Europe and Latin America (LATAM) regions, [create a production developer account](https://docs.clover.com/docs/developer-accounts#create-production-developer-account).

2. Create and test your app on the sandbox. You can submit your developer account for approval on production even while building and testing your app on sandbox.

## Submit your production developer account for approval

1. Log in to the production Developer Dashboard. The Developer Dashboard appears.
2. From the left navigation menu, click **Developer Settings** > **Info**. The Developer Info page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8f660d5-DevAccnt-approval.png",
        "",
        "Developer Info page"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Developer Info page"
    }
  ]
}
[/block]


3. Click the edit icon in each section, enter developer information, and click **Save**.

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "**Account Details section**",
    "0-1": "Developer’s details.",
    "1-0": "Developer display name",
    "1-1": "Developer’s display name on the [Clover App Market](https://www.clover.com/appmarket).",
    "2-0": "Website (Optional)",
    "2-1": "Developer’s website address, if available.  \nFormat: <https://www.example.com>",
    "3-0": "I am doing business as",
    "3-1": "\\- For an individual submitting an app for approval, select **Individual**.  \n  \n- For a corporate developer or company submitting an app for approval, select **Business**. When you select **Business**, additional fields display to enter the:  \n  -- Company Legal Name  \n  -- Business EIN/Tax ID—Employer identification number (EIN) or tax identifier (Tax ID) from a government tax authority-issued document.",
    "4-0": "**Identity Verification section**",
    "4-1": "Required. Information to verify the developer’s identity and to contact, if needed, for additional details.  \n**Important:**  \n  \n- **International developers**—If the developer’s address is outside the intended market, an unexpired passport is required. See the [FAQs on Developer account approval](https://docs.clover.com/docs/faqs#developer-account-approval). Developers in Canada and the United Kingdom (UK) can provide a current driver’s license instead of a passport.  \n- **OFAC check**—Clover must run an Office of Foreign Assets Control (OFAC) check on every developer as part of the approval process. After your account is approved, Clover repeats the OFAC check monthly.",
    "5-0": "First Name",
    "5-1": "Developer’s first name.",
    "6-0": "Last Name",
    "6-1": "Developer’s last name.",
    "7-0": "Date or Birth",
    "7-1": "Developer’s date of birth.  \n**Format: **YYYY-MM-DD",
    "8-0": "Home Address",
    "8-1": "Developer’s home address, including street, city, 2-character state code, country, and postal or ZIP code as mentioned on a utility bill, bank statement, or other legal document matching the address of the developer account.  \n**Note: **A postal box or P.O. box number is valid for an organization but not for its individual representative.",
    "9-0": "Contact Details",
    "9-1": "Developer’s phone number and email address.",
    "10-0": "**Contact Info section**",
    "10-1": "Information for emergency, technical, and public relations (PR) related communication.",
    "11-0": "Emergency contact",
    "11-1": "Developer’s emergency contact email address that is accessible to the developer at all times. Clover can use this email address to communicate urgent information about the approval request, such as if the submitted app generates frequent errors.",
    "12-0": "Tech Contact",
    "12-1": "Read-only. Displays the email address used when creating the developer account. Clover can use this email address to communicate technical issues and updates on Clover SDKs, APIs, features, and the platform.",
    "13-0": "PR Contact (Optional)",
    "13-1": "Contact person details, including name, phone number, and email address, to coordinate public relations (PR) efforts with Clover, if needed."
  },
  "cols": 2,
  "rows": 14,
  "align": [
    "left",
    "left"
  ]
}
[/block]


4. Click the **Developer Agreement** link to review the [Clover App Market Developer Terms](https://www.clover.com/developer-agreement).
5. Click **Verify Your Account**. You agree to the Clover App Market Developer Terms by submitting your details.

## Upload additional information securely

If the [Clover App Market](https://www.clover.com/appmarket) business team needs to contact you for more information, they also share a secure Clover Box folder URL (link) with you. Upload all required documentation to the specified Clover Box folder. Do not share any required identity documentation by email.

After your account is approved, the status of your developer account on the Developer Settings page is updated to **Account Verified**. You receive an email confirming the developer account approval.

## Update approved account information

### Update name and email address

If you need to change approved account information, such as the developer's name or email address, send an email to Clover at <a href="mailto:developer-relations@devrel.clover.com">developer-relations@devrel.clover.com</a> with the following information:

- Developer account name and identifier. To view the Developer ID, from the left navigation, click **Developer Settings **> **Developer Info**.
- Request type and reason for the request, for example, developer name or email address change.

### Transfer account ownership

If you need to transfer the ownership of a business account to another user, see [Transfer developer account ownership](https://docs.clover.com/docs/transfer-developer-ownership). For example, if an approved developer leaves the company, the owner or admin must transfer the developer account ownership to another person to assume responsibility for the account.
