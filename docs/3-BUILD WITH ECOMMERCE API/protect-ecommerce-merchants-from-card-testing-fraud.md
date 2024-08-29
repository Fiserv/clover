---
title: "Protect Ecommerce merchants from card testing fraud"
slug: "protect-ecommerce-merchants-from-card-testing-fraud"
excerpt: ""
hidden: false
metadata: 
  description: "Learn about card testing methods and how to recognize and prevent card testing on e-commerce websites."
  image: []
  keywords: "card testing, e-commerce websites, Ecommerce API, Clover fraud tools, Hosted Checkout, iframe"
  robots: "index"
createdAt: "Thu Feb 22 2024 04:16:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 10 2024 22:22:36 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": " <meta name=\" description\" content= \"Learn about card testing methods and how to recognize and prevent card testing on e-commerce websites.\" >\n<!--DS-5406-NewTopic-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

## What is card testing?

Card testing, also known as carding, account testing, and card checking, is a fraudulent activity where a fraudster uses stolen partial or full card credentials to make a small payment, such as a $1 purchase on an e-commerce website. The purchase is intended to verify if the card is active, check the card expiration date, and validate or guess the card verification value (CVV).

If the small purchase is successful, the fraudster starts making larger purchases. Bots or scripts are used to rapidly submit hundreds of thousands of card-not-present (CNP) transaction authorization requests on an e-commerce website. This continues until the fraud is detected and the card blocked, but not before a loss of transaction fees, inventory, and even reputation.

If the card testing attempt fails, the fraudster learns that the e-commerce website uses fraud detection measures. The fraudster gathers information about the card from the decline message, such as a transaction decline due to an address mismatch.

It is important to understand [card testing methods](https://docs.clover.com/docs/protect-ecommerce-merchants-from-card-testing-fraud#understand-card-testing-methods), the [impact of card testing](https://docs.clover.com/docs/protect-ecommerce-merchants-from-card-testing-fraud#understand-the-impact-of-card-testing), and to [detect](https://docs.clover.com/docs/protect-ecommerce-merchants-from-card-testing-fraud#detect-card-testing-using-common-indicators) and [prevent card testing](https://docs.clover.com/docs/protect-ecommerce-merchants-from-card-testing-fraud#prevent-card-testing) fraudulent activity on hosted payment pages and e-commerce websites.

***

## Understand card testing methods

Card testers or fraudsters use various methods to test stolen card data for validity and then carry out both manual and automated fraud attacks that range in risk and efficiency:

- **Payment sessions**—Merchants can generate customer-facing or public sessions as a payment link for multiple customers, for example, a promotional period payment link or a donation button. The same payment link can be used multiple times until it is deleted from the system. These public payment links are at high risk of being used for card testing.
- **Ecommerce APIs**—Private payment sessions are authenticated using an API token associated with a specific merchant. A payment service provider uses the API token to verify merchant identity and authorize the payment request. Private sessions are more secure because no payment request is authorized without the API token. However, [Ecommerce APIs](https://docs.clover.com/reference/createcharge) are open to the public and can be a target for card testing. Merchants must keep their authorization tokens secret from unauthorized users and never share the tokens over public networks.

***

## Detect card testing using common indicators

A combination of factors can indicate a card testing fraudulent activity that demands attention:

| Card testing factors         | Description                                                                                                                                                                                                                                                                  |
| :--------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Small and frequent purchases | Frequent transactions for small amounts, ranging from a few cents to less than $5, are used to check a card's validity. A successful payment indicates that the card is active, but this transaction displays on the card statement and can alert the legitimate cardholder. |
| Repeated declines            | Multiple failed attempts on different cards with slight variations can indicate testing for valid card details.                                                                                                                                                              |
| Rapid transaction attempts   | Unusually high number of card transactions within a short timeframe.                                                                                                                                                                                                         |
| Sequential card number       | Multiple attempts using similar card numbers in sequence, for example, 1234 5678 9012 3456, 1234 5678 9012 3457, and so on.                                                                                                                                                  |
| Pattern-based attempts       | Similar expiration dates or CVV numbers are used successively across various transactions.                                                                                                                                                                                   |
| Geographical anomalies       | Transactions from locations inconsistent with the cardholder's usual spending patterns or known addresses.                                                                                                                                                                   |
| IP address anomalies         | Multiple attempts originating from different IP addresses or locations in a short period.                                                                                                                                                                                    |

***

## Prevent card testing

A combination of risk assessment, enhanced fraud prevention tools, and multi-layer checks such as Address Verification System (AVS) and card verification value (CVV) matching, monitoring IP addresses, and using velocity checks are required to combat card testing. Here are some of the methods that Clover provides:

### 1. Use Clover-hosted checkout and payment integrations

Clover-hosted checkout and Clover iframe are two ways to integrate Clover payment services with an e-commerce website. Both methods use the Clover Ecommerce APIs and SDKs to process the payment securely and reduce the merchant's Payment Card Industry (PCI) compliance scope.

- Clover-hosted checkout securely redirects customers to a Clover-hosted payment page, where they can enter their card details and complete the transaction.
- Clover iframe is a customizable way to embed a Clover-hosted form or elements into an e-commerce payment page.

### 2. Use reCAPTCHA with iframe and hosted checkout

reCAPTCHA is available for fraud prevention in all iframe and hosted checkout implementations. Using Clover iframe or REST API, you can integrate and manage the reCAPTCHA settings on e-commerce integrations. See [Clover Ecommerce vs. Bots: reCAPTCHA Your Website](https://medium.com/clover-platform-blog/clover-ecommerce-vs-bots-recaptcha-your-website-e6d6c21aa1c8) to learn more about implementing CAPTCHA as a security feature in your Ecommerce integration.

#### **reCAPTCHA setting for iframe on the Developer Dashboard**

1. Log in to the Developer Dashboard.
2. From the left navigation, click \<**app name**> **App Settings** > **Ecommerce Settings**. The Edit Ecommerce settings page appears.
3. Select the **Hosted iFrame** option, and then select the **Use reCAPTCHA for all transactions made through iFrame embedded page.** checkbox.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6003df9-reCAPTCHA-DevDashboard.png",
        "",
        "Developer Dashboard: reCAPTCHA setting for Hosted iframe page"
      ],
      "align": "center",
      "sizing": "80% ",
      "border": true,
      "caption": "Developer Dashboard: reCAPTCHA setting for Hosted iframe page"
    }
  ]
}
[/block]


4. Click **Save**.

#### **reCAPTCHA setting for a hosted checkout page on the Merchant Dashboard**

1. Log in to the Merchant Dashboard.
2. From the left navigation menu, click **Account & Setup**. The Account & Setup page appears.
3. In the **Ecommerce** section, click **Hosted Checkout**. The Hosted Checkout page appears.
4. In the ReCAPTCHA section, select the **Use reCAPTCHA for all transactions made through hosted checkout page **checkbox.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/afc6082-HostedCheckout-reCAPTCHA.png",
        "",
        "Merchant Dashboard: reCAPTCHA setting for a hosted checkout page"
      ],
      "align": "center",
      "sizing": "90% ",
      "border": true,
      "caption": "Merchant Dashboard: reCAPTCHA setting for a hosted checkout page"
    }
  ]
}
[/block]


5. Click **Back to Account & Setup**.

#### **reCAPTCHA setting for iframe on the Merchant Dashboard**

1. Log in to the Merchant Dashboard.
2. From the left navigation menu, click **Account & Setup**. The Account & Setup page appears.
3. In the **Ecommerce** section, click **Ecommerce API Tokens**. The Ecommerce API Tokens page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d4a0120-APIToken-reCAPTCHA.png",
        "",
        "Merchant Dashboard: reCAPTCHA setting for iframe embedded page"
      ],
      "align": "center",
      "sizing": "90% ",
      "border": true,
      "caption": "Merchant Dashboard: reCAPTCHA setting for iframe embedded page"
    }
  ]
}
[/block]


4. In the reCAPTCHA Settings section, select the **Use reCAPTCHA for all transactions made through iFrame embedded page** checkbox.
5. Click **Back to Account & Setup**.

### 3. Use fraud prevention tools

Clover provides options to select and set fraud rules through the Merchant Dashboard.

1. Log in to the Merchant Dashboard.
2. From the left navigation menu, click **Account & Setup**. The Account & Setup page appears.
3. In the **Ecommerce** section, click **Fraud Tools**. The Fraud Prevention Tools page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/88d0d7d-FraudTools.png",
        "",
        "Fraud prevention tools setup for Ecommerce API"
      ],
      "align": "center",
      "sizing": "50% ",
      "border": true,
      "caption": "Fraud prevention tools setup for Ecommerce API"
    }
  ]
}
[/block]


4. Do one of the following:
   - Click **Edit** to set up any of the fraud prevention tools.
   - Click **Show Rules** to view the existing rule setup.

The fraud prevention tools include:

- **AVS, postal code, and full billing address**—The Address Verification System (AVS) checks the postal code and billing street address to determine whether the information matches the billing address on file with the card issuer. Clover fraud system includes a rule to block any payments that fail postal code verification.
- **CVC and CVV**—Customers can provide a card verification value (CVV) or card verification code (CVC) during the online checkout process. The card issuer checks the CVV for validity against what is on file and sends back an authorization or decline to the merchant. For more information on AVS and CVC checks, see Confirm customer information with fraud tools.
- **Transaction controls**—You can add custom rules for a merchant. For example, add rules for Transaction Limits and set conditions to limit the number of transactions per card per day to 20 or set transactions per IP address. You can also set velocity limits, that is, limit the number of failed checkout attempts on an e-commerce payment page.
- **Fraud filters**—You can create allowed or safe and blocked lists for IP addresses, non-tokenized credit card numbers, bank identification numbers (BINs), email addresses or domains, billing addresses, country, and other relevant information.

### 4. User authentication

User access verification and controlling user sessions on e-commerce websites are also effective ways of preventing card testing.

- **3DS**—The 3-D Secure (3DS) authentication protocol is a paid service for merchants. It provides an additional layer of verification for credit and debit card-not-present (CNP) transactions initiated by the customer. Clover uses EMV® 3DS to authenticate customers and safeguard against CNP fraud, reduce chargebacks, and shift chargeback liability from the merchant to the issuer. See [Use Clover 3-D Secure for e-commerce transactions](https://docs.clover.com/docs/use-3ds).
- **Timed logouts and user account management**—Some best practices are to set a time limit on how long a user can remain logged on an e-commerce website. Users can be required to create an account on the e-commerce website to make a payment and limit the number of user accounts that can be added within a specific timeframe.

### 5. Set up continuous monitoring

Clover provides continuous transaction monitoring through the Merchant Dashboard and Webhook notifications. You can:

- **Monitor transaction processing patterns**—Review batch totals and transaction history daily for irregular payment activity. Identify multiple smaller transactions and those that result in declines, multiple transactions with different cards using the same customer information, or excessive usage and bandwidth consumption from a single user.
- **Monitor IP addresses**—Check multiple failed card payment data in the blocklist database or look out for multiple logins for a single card account from many IP addresses.
- **Monitor fraud attempts**—For example, HTTP status 402 errors are from CVV decline errors or SCL, API failure rate, and HTTP status 429 errors are from a developer app that is reaching the rate limits.

Multi-level prevention is better than countering the impact of a card testing attempt, such as fee adjustments and the reversal of approved authorizations to prevent disputes.

***

## Understand the impact of card testing

Card testing has far-reaching financial and reputational impacts on small and medium-sized businesses (SMBs) that use customer-facing e-commerce checkout websites. These include:

| Consequence of card testing                    | Description                                                                                                                                                                                                                                                                                                                        |
| :--------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Increase in per-transaction authorization fees | Card networks may impose higher processing fees for each failed payment attempt. This is to cover the additional scrutiny and resources when merchants receive thousands of payment requests due to card testing attempts.                                                                                                         |
| Increase in chargebacks and losses             | When customers detect fraudulent card activity and file a dispute, it often results in chargebacks on those transactions. This incurs financial and inventory losses. Card networks may label the merchant as high-risk and initiate stricter scrutiny, increased fees, and limited access to certain payment processing services. |
| Low transaction approval rate                  | As card issuers and networks identify suspicious patterns, they are more cautious in approving transactions from the affected merchant. Consequently, legitimate transactions may come under scrutiny, causing inconvenience to both the merchant and the customers.                                                               |
| Decrease in system performance                 | The influx of fraudulent transactions, bot activities, or repeated failed attempts can overload the payment system, causing disruptions, slowdowns, or even temporary outages.                                                                                                                                                     |
| Loss of reputation                             | Card testing can severely damage the reputation of SMBs. Due to multiple failed transactions and potentially fraudulent activities, customers may lose trust in the ability of the business to secure their payment information.                                                                                                   |

Be aware, alert, and report suspicious activity immediately by sending an email to [developer-relations@devrel.clover.com](mailto:developer-relations@devrel.clover.com).
