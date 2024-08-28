---
title: "Manage developer account roles and permissions"
slug: "developer-account-roles"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to assign different roles to your developers and other team members in the Clover Developer Dashboard. Whether you need to control access, permissions, or billing, Clover lets you create and manage developer account roles."
  image: 
    - "https://files.readme.io/cfa5ce1-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Thu Nov 15 2018 21:55:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<!-- DS-4289-Steps tested on https://dev1.dev.clover.com/developer-home/create-account and added MFA set up step -->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n  <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


# Understand developer roles

The Developer Dashboard has four standard user roles—Owner, Admin, Business, and Technical—with default permissions. The owner can:

- Invite other users to create their developer member accounts and access the Developer Dashboard. See [Invite members](https://docs.clover.com/docs/ds-4290-manage-developer-account-roles#invite-members). Members can have three roles—Admin, Business, and Technical. 
- Create custom roles, such as pricing specialist, release engineer, or human resources, and assign specific permissions for controlling the custom roles. See [Create a custom role](https://docs.clover.com/docs/ds-4290-manage-developer-account-roles#create-a-custom-role).

The following table provides more information:

[block:parameters]
{
  "data": {
    "h-0": "Role",
    "h-1": "Description",
    "h-2": "Functions",
    "0-0": "Owner",
    "0-1": "User who creates and manages the developer account. Owner can be a single developer creating apps or the leader of a team of developers and other staff within an organization.",
    "0-2": "- Owner has complete control of the account, and only they can accept the [Clover developer agreement](https://www.clover.com/developer-agreement).  \n- Owner is assigned all permissions, and these cannot be edited or removed.  \n- Owner or Member > Admin can invite users to create their developer member accounts and access the Developer Dashboard.  \n- Owner can add and manage custom roles.  \n- Owner can initiate or request developer ownership transfer from the Developer Dashboard. See [Transfer developer account ownership](https://docs.clover.com/docs/transfer-developer-ownership).",
    "1-0": "Member",
    "1-1": "Users that the owner invites to create their developer member accounts and access the Developer Dashboard are called members. Members are assigned to three default roles—Admin, Business, and Technical. See [Invite members](https://docs.clover.com/docs/ds-4290-manage-developer-account-roles#invite-members).",
    "1-2": "- Members in the three roles are assigned specific permissions to perform limited actions.  \n- Member roles receive tasks delegated by the owner.  \n- Member roles cannot be deleted.",
    "2-0": "Member > Admin",
    "2-1": "Users with all owner role permissions except the permission to accept the Clover developer agreement.",
    "2-2": "",
    "3-0": "Member > Technical   ",
    "3-1": "Developers and engineers who write code, debug, and manage APKs.",
    "3-2": "",
    "4-0": "Member > Business   ",
    "4-1": "Members who work with merchants and pricing.",
    "4-2": "",
    "5-0": "Custom role             ",
    "5-1": "Users with specific roles, such as pricing specialist, release engineer, or human resources. See [Create a custom role](https://docs.clover.com/docs/ds-4290-manage-developer-account-roles#create-a-custom-role). The owner can:  \n- Add custom roles.  \n- Custom custom roles by assigning permissions.  \n- Delete a custom role.",
    "5-2": ""
  },
  "cols": 3,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


# Understand permissions for developer roles

Permissions are assigned to each developer role:

- Owner role is assigned all permissions.
- Member and custom roles are assigned specific permissions.

<!-- information source: https://confluence.corp.clover.com/display/DZ/Developer+Platform+User+Roles+and+Permissions -->

| Permission                       | Description                                                                     |
| :------------------------------- | :------------------------------------------------------------------------------ |
| Accept developer agreement       | View and edit account settings in Developer Settings - Account Info.            |
| Access bank details              | Access developer bank details.                                                  |
| Add new members and assign roles | Access the Members tab.                                                         |
| Manage merchants                 | Access Merchant Installs. Required to GET merchant installs data.               |
| Edit app pricing                 | Edit App Pricing and Distribution.                                              |
| Access charges                   | Display and hide the Billing tab.                                               |
| Merchant support                 | Access the Merchant Help Code and reply to or report Clover App Market reviews. |
| Delete, edit, submit app         | Edit App Settings.                                                              |
| Manage APKs                      | Edit App Releases and upload an APK.                                            |
| View release groups              | Display Release Groups to the user.                                             |
| Edit release groups              | Edit Release Groups.                                                            |

# Watch video: Developer account roles and permissions

[block:parameters]
{
  "data": {
    "h-0": "Let’s learn",
    "0-0": "In this video, learn:  \n- How to define developer account roles?  \n- What are the benefits of assigning permissions to developer account roles?  \n- What are the limitations of different developer account roles?"
  },
  "cols": 1,
  "rows": 1,
  "align": [
    "left"
  ]
}
[/block]


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FIri6tv_F_8A%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DIri6tv_F_8A&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FIri6tv_F_8A%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=Iri6tv_F_8A",
  "title": "Clover Developer Account Roles",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/Iri6tv_F_8A/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=Iri6tv_F_8A",
  "typeOfEmbed": "youtube"
}
[/block]


# Invite members

As a developer with an owner role, you can invite members to join your team. The invite is sent as an email with a link to access the member developer account. 

1. Log in to the Developer Dashboard with your owner account details.
2. From the left navigation menu, click **Developer Settings** > **Members**. The Members page appears.
3. Click **Invite Members**. The Invite Members To Your Developer Account pop-up appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6a8fcfd-Invite-Members.png",
        "",
        "Invite Members To Your Developer Account"
      ],
      "align": "center",
      "sizing": "65% ",
      "border": true,
      "caption": "Invite Members To Your Developer Account pop-up"
    }
  ]
}
[/block]


4. Enter the email address of the user you want to invite as a member. If needed, enter a list of email addresses separated by commas.
5. From the Role drop-down list, select a member role—**Admin**, **Business**, or **Technical**.
6. Click **Invite**. The invited member receives an email with instructions to access their developer account.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6bc9709-Invite_Inbox.png",
        "",
        "Email invitation to join as member"
      ],
      "align": "center",
      "sizing": "70% ",
      "border": true,
      "caption": "Email invitation to join as a member"
    }
  ]
}
[/block]


Information for all invited members and members who accept the invite to join the owner’s developer account displays on the Members page with email address, role, and status details.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/551d6ca-Members-Display.png",
        "",
        "Members page with submenu to perform actions on roles"
      ],
      "align": "center",
      "border": true,
      "caption": "Members page with submenu to perform actions on roles"
    }
  ]
}
[/block]


7. Click the ellipsis icon next to a member’s name to:

- Resend the invite.
- Deactivate a member account.
- Edit the role assigned to the member.

For any member or custom role, you can manage assigned default permissions. See [Manage default permissions](https://docs.clover.com/docs/developer-account-roles#manage-default-permissions).

# Create a custom role

The owner can create custom roles for members to perform custom tasks and assign relevant permissions, such as in the beta tester team, production testers team, customer support team, and so on.

1. Log in to the Developer Dashboard with your owner account details.
2. From the left navigation menu, click **Developer Settings** > **Roles**. The Roles page appears.
3. Click **Add Role**. The Add New Role window appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/50cdead-Add-Role.png",
        "",
        "Add New Role pop-up"
      ],
      "align": "center",
      "sizing": "35% ",
      "border": true,
      "caption": "Add New Role pop-up"
    }
  ]
}
[/block]


4. Enter the custom role name.
5. From the Default Permission drop-down list, select permission to assign to the custom role. For example, for a Customer Support custom role, you can select default permissions for the Business role.
6. Click **Save**. The custom role displays on the Roles page.
7. From the Actions column for a custom role, click an icon to edit the name of the role or delete the custom role.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6e09b05-Edit-Custom-Role.png",
        "",
        "Roles page with edit and delete icons for custom roles"
      ],
      "align": "center",
      "sizing": "80% ",
      "border": true,
      "caption": "Roles page with edit and delete icons for custom roles"
    }
  ]
}
[/block]


For any member or custom role, you can manage assigned default permissions. See [Manage default permissions](https://docs.clover.com/docs/developer-account-roles#manage-default-permissions).

# Manage default permissions

To review the default permissions assigned to each role:

1. Log in to the Developer Dashboard with your owner account details.
2. From the left navigation menu, click  **Developer Settings** > **Permissions**. The Permissions page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d7e33c9-Permissions.png",
        "",
        "Permissions for developer account roles"
      ],
      "align": "center",
      "sizing": "100% ",
      "border": true,
      "caption": "Permissions for developer account roles"
    }
  ]
}
[/block]


3. Review the list of permissions assigned to each member and custom role.
4. For any role, select or clear checkboxes to assign or remove permissions as needed. Your changes are saved automatically.
