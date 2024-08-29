---
title: "Manage developer accounts"
slug: "managing-developer-accounts"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to invite members to join a developer account team and access both the Developer and Merchant Dashboard."
  image: []
  robots: "index"
createdAt: "Wed Jun 23 2021 15:45:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 12 2024 12:47:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Each Clover developer account is created and managed by an account owner. The owner can be:

- An individual developer who is creating apps.
- The leader of a team of developers and other staff within an organization. 

The owner can invite members to access the production Developer Dashboard and assign roles and permissions. See [Manage developer account roles and permissions](https://docs.clover.com/docs/developer-account-roles).

## Understand developer and test merchant accounts

Developer accounts and merchant accounts are separate accounts. The developer account with the owner or admin role can invite additional users to create their developer member accounts to access the Developer Dashboard.

- If a member needs access to the [test merchant account](https://docs.clover.com/docs/working-with-test-merchants), the owner can add them as an employee of the test merchant.
- If a member needs accounts for both the Developer Dashboard and Merchant Dashboard, they must use the same email address to create each account. The same email address lets the member access both dashboards and use the test merchant account to install and test apps. See [Add a developer account member to a test merchant account](https://docs.clover.com/docs/ds-4300-manage-developer-accounts#add-a-developer-account-member-to-a-test-merchant-account).

For example, an invited member creates a developer account and a test merchant account with the email address `member1@example.com`. In this case, only the `owner@example.com` and `member1@example.com` accounts can view both the Developer Dashboard and Merchant Dashboard.

<!--Diagram source: https://lucid.app/lucidchart/4cc1cfcf-3b4e-4eea-a8b2-e473565c1961/edit?viewport_loc=-45%2C328%2C1783%2C992%2Cm-5o7ONTd-nK&invitationId=inv_d6b5be68-5b16-4e73-9763-9c8b3d78158c -->

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ff9be16-DS-4300-Manage-dev-and-test-merchant-account-roles.png",
        "DS-300_Managing Developer Acccounts.png",
        1169
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Developer account owner and test merchant account roles"
    }
  ]
}
[/block]


## Add a developer account member to a test merchant account

If you want to invite members only to create a developer account, see [Invite members](https://docs.clover.com/docs/developer-account-roles#invite-members). The following procedure provides steps to add a developer member account as an employee in a test merchant account.

1. Log in to the production Developer Dashboard with your owner account details.
2. From the left navigation menu, click **Developer Settings** > **Members**. The Members page appears.
3. Click **Invite Members**. The Invite Members To Your Developer Account pop-up appears.
4. Enter the user’s email address to invite as a member. If needed, enter a list of email addresses separated by commas.
5. From the Role drop-down list, select a member role—Admin, Business, or Technical.
6. Click **Invite**. The invited member receives an email with instructions to access their developer account.  
   Information for all invited members and members who accept the invite to join the owner’s developer account displays on the Members page. The information contains the email address, role, and status details.
7. From the Dashboard drop-down menu, under Businesses, click \<**Merchant Name**>. The Merchant Dashboard appears.
8. From the left navigation menu, click **Employees**. The Employees page appears.
9. Click **Add Employee**. The Add Employee page appears.
10. Enter developer member information to add as an employee for the test merchant.
11. Click **Save**. The employee information displays on the Employees page.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c2631c5-Emp-Roles.png",
        "",
        "Employees page"
      ],
      "align": "center",
      "sizing": "90% ",
      "border": true,
      "caption": "Employees page"
    }
  ]
}
[/block]
