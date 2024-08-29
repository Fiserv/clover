---
title: "Set up two-factor authentication (2FA)"
slug: "set-up-two-factor-authentication-2fa"
excerpt: ""
hidden: false
metadata: 
  description: "This process helps to set up two-factor authentication for your account to add an extra layer of protection and decrease the risk of unauthorized access and system breaches."
  image: []
  robots: "index"
createdAt: "Fri May 05 2023 06:31:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 10 2024 22:21:16 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Two-factor authentication (2FA) adds an extra layer of protection and significantly decreases the risk of unauthorized access and system breaches. This requires you to provide a unique verification code – a one-time password (OTP) –  other than your email ID and password combination to log in to the Developer Dashboard.

You can access the OTP in either of the following ways:

- **SMS**—Receive verification codes on your mobile phone. You can enter a backup recovery code if your mobile phone is unavailable.
- **Authenticator app**—Receive verification codes using an authenticator app like Google Authenticator. You can download the authenticator app on your [Android](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2&hl=en&gl=US&pli=1) or [iOS](https://apps.apple.com/us/app/google-authenticator/id388497605) device. Clover recommends using an authenticator app to set up your 2FA.

> 📘 NOTE
> 
> Two-factor (2FA) authentication is mandatory for all users to access the Clover production Developer Dashboard.

1. Log in to your Clover developer account.

- North America: <https://www.clover.com/global-developer-home>
- Sandbox for Europe and Latin America (LATAM): <https://sandbox.dev.clover.com>
- Production for Europe: <https://www.eu.clover.com>
- Production for Latin America (LATAM): <https://www.la.clover.com>

2. From the profile drop-down, click **User Settings**. The User Settings page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c4f944d-user_setting.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "600% ",
      "border": true
    }
  ]
}
[/block]


3. Click **Turn on Two Factor Authentication**. The Pick a method to get your verification codes pop-up appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/90f25d5-SMS_AP.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "50% ",
      "border": true
    }
  ]
}
[/block]


4. Select one of the following options:

- **SMS**—The Enter your phone number page appears:  
  a. Select the country code and enter your mobile phone number. The Send Code button is available.  
  b. Click **Send Code**. A 6-digit OTP is sent to your mobile phone, and the Enter the verification code page appears.  
  c. Enter the verification code (OTP) on the page, and click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e98055a-SMS_OTP.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "50% ",
      "border": true
    }
  ]
}
[/block]


- **Authenticator app** —The Open your authenticator app page appears:  
  a. Use your phone camera to scan the QR code to download the authenticator app.  
  b. Open the authenticator app to view or copy the 6-digit OTP.  
  c. Enter the verification code (OTP) and click **Next**. You’ve successfully turned on the two-factor authentication pop-up displays on the screen.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cd372e3-Authenticator_2FA.png",
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


4. Click **Got it**. The User Settings page displays the Two-Factor Authentication section with your authentication details.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/50838b0-2FA_turnonoff.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "400px",
      "border": true
    }
  ]
}
[/block]


5. Click **Turn On ** or **Turn Off** to change the authentication method.  
   **Note:** You can use only one method at a time for authentication.
6. Click **Download** and save the backup recovery codes the first time you set up two-factor authentication. The recovery codes are downloaded in a .txt file.  
   **Note: **When you cannot access the OTP through SMS,  use one of these recovery codes for 2FA.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6572a80-small-txt.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "600px",
      "border": true
    }
  ]
}
[/block]
