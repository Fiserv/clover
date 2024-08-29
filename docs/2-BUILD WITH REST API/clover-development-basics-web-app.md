---
title: "Clover REST API basics"
slug: "clover-development-basics-web-app"
excerpt: ""
hidden: false
metadata: 
  description: "Review the basic concepts and quick references that can help you build apps with the Clover REST API."
  image: []
  robots: "index"
createdAt: "Fri Sep 07 2018 02:52:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 08:11:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--DS-6275: Added links to the two separate OAuth flows and the two separate regions: NA & Europe/LATAM-->"
}
[/block]


# Create web apps with the Clover REST API

Clover web apps offer a seamless experience and enable merchants to connect services through a central hub. You can build a browser-based integration that uses our REST API along with OAuth to create a secure connection to your website. You can redirect a merchant from the Clover Merchant Dashboard to your website URL (link). 

You can create an alternate integration path for scenarios where a native, on-device experience may not be appropriate. Clover developers have used our OAuth protocol for reporting, analytics, Ecommerce integrations, and more.

# Before you begin

Here's how you go about building Clover REST APIs:

1. Choose your region:
   - **North America—United States and Canada: **Create a single developer account and access both the sandbox and production environments on the [Global Developer Dashboard](https://www.clover.com/global-developer-home/home). See [Get started with the global developer platform](https://docs.clover.com/docs/global-developer-platform-get-started).
   - **Europe and Latin America: **Create separate developer accounts on the [sandbox environment](https://docs.clover.com/docs/get-started-with-sandbox-environment) and the region-based [production environments](https://docs.clover.com/docs/clover-app-approval-process).
2. Import the [sample inventory](https://clover.box.com/s/y08he8u7llov7shufskgyb5stlgcs6s8) to get started with your test merchant. See [Import inventory](https://docs.clover.com/docs/importing-inventory).
3. Use the appropriate [OAuth flow](https://docs.clover.com/docs/oauth-flows-in-clover).
4. Use the following resources for guidance on how to build your app with Clover REST API:
   - [Use Clover REST API](https://docs.clover.com/docs/making-rest-api-calls).
   - Check out our [video tutorials about Clover Rest APIs](https://www.youtube.com/playlist?list=PL5qwTAUobAx4MWUhvfYxIlxocOndHrtuo)
   - Use [webhooks](doc:webhooks) to receive and handle notifications about changes in merchant data.
   - Manage [orders](doc:working-with-orders) and learn to calculate taxes with these [examples](doc:tax-reports-examples).
   - Learn about [API usage & rate limits](doc:api-usage-rate-limits).
   - Build solutions for accepting payments with [Ecommerce API](doc:ecommerce-accepting-payments).
   - Use the [Payment Card Industry security guidance for app developers](https://docs.clover.com/docs/pci-security-guidance-for-app-developers).

# Web app development guidelines

The following web development guidelines can help you create good apps that give a great experience to Clover merchants.

## 1\. Be aware of web security principles

**Do's**

Clover recommends you familiarize yourself with basic web security principles. The Open Web Application Security Project (OWASP) offers several resources that will help you get started:

- [OWASP homepage](https://www.owasp.org/index.php/Main_Page)
- [OWASP Top Ten](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)
- [OWASP/Developer Guide](https://github.com/OWASP/DevGuide)
- [OWASP Cheat Sheet Series](https://www.owasp.org/index.php/OWASP_Cheat_Sheet_Series)

**Don'ts**

- Don't check app tokens into your source code online.
- Don't prompt users to enter sensitive cardholder data, such as card numbers and expiration dates, except as part of Clover payments SDK (this means that third-party Clover Apps are not payment apps as the term is defined in the <a href= "https://www.pcisecuritystandards.org/minisite/en/docs/PA-DSS_v3.pdf" rel= "noopener noreferrer" target="_blank">PCI PA DSS</a>).

## 2\. Secure merchant data

The Clover REST API lets you access a database. Hence, you need to follow the security standards for database access.

- Use server-to-server requests as much as possible when your web application accesses the Clover API.
- Securely store any data that your own services cache.

## 3\. Limit client access

Customer and employee-facing apps must prevent unauthorized users from accessing privileged data, including the Clover credentials your app uses.

- Use secure logins and session tracking if needed.
- Use server logic to prevent unauthorized access to data by injection attacks.
- Consider any data passed to the client in any format as vulnerable.

## 4\. Ease of Clover integration

- Make it easy for merchants to log in. The URL (link) for your web app should launch the login flow, not browse to the general homepage for your business.
- Include your Web URL prior to submission and test it with an example OAuth request.
