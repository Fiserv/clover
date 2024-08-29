---
title: "3D Secure (3DS) for e-commerce transactions"
slug: "3ds-for-clover-merchants-overview"
excerpt: ""
hidden: true
metadata: 
  description: "Secure e-commerce transactions with 3D Secure (3DS). Verify cardholder identity, reduce fraud, and comply with PSD2 SCA regulations."
  image: []
  robots: "index"
createdAt: "Mon May 27 2024 06:27:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jun 12 2024 09:10:57 GMT+0000 (Coordinated Universal Time)"
---
<meta name="description" content=“Secure e-commerce transactions with 3D Secure (3DS). Verify cardholder identity, reduce fraud, and comply with PSD2 SCA regulations.">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# 3DS overview

3D Secure (3DS) is a protocol that provides an additional security layer for online credit and debit card-not-present (CNP) transactions. Clover uses the <<glossary:EMVCo>> 3DS to authenticate customers and safeguard against CNP fraud.

In a general <<glossary:3DS>> flow, customers need to verify their identity with the card issuer during CNP payments for e-commerce transactions. The card issuer may require the customer to enter a password linked to a card or a one-time passcode (OTP) received on their mobile device or even complete payment with a <<glossary:frictionless flow>>. The method of 3DS authentication depends on the card issuer.

## 3DS as offered by card issuers

All major card issuers offer 3D Secure by a different brand name. Merchants and cardholders can recognize the offering as follows:

[block:parameters]
{
  "data": {
    "h-0": "Card issuer",
    "h-1": "3DS",
    "0-0": "American Express<sup>®</sup>",
    "0-1": "SafeKey®",
    "1-0": "Discover<sup>®</sup>",
    "1-1": "ProtectBuy®",
    "2-0": "Mastercard<sup>®</sup>",
    "2-1": "SecureCode",
    "3-0": "Visa<sup>®</sup>",
    "3-1": "Visa Secure"
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Regional compliance

3DS helps to secure electronic payments as per the <<glossary:PSD2>> <<glossary:Strong Customer Authentication>> (SCA) regulatory requirement in the European region. 3DS authentication is optional in all other regions, but Clover recommends enabling this value-added service to reduce fraud. Ecommerce or card-not-present (CNP) payment is currently available for Clover merchants in the United States.

***

# 3DS enablement for Clover merchants

Clover supports[ 3D Secure 2.0 (3DS2)](https://3dsecure2.com/), which enhances online transaction security by providing issuers with extensive data for improved risk assessment and enabling user authentication through a <<glossary:challenge flow>> for high-risk transactions.

## 3DS enablement request

A Clover merchant can request 3D Secure (3DS) enablement only through their relationship manager. The relationship manager can guide the merchant based on eligibility for 3DS enablement.

## 3DS pricing for Clover merchants

Each transaction request from a 3DS-enabled merchant that is authenticated using 3DS secure services is charged at **4 cents**. The merchant receives a monthly invoice for 3DS services through Clover Billing.

## 3DS workflow for Clover merchants

After 3DS enablement for a Clover merchant based on eligibility checks, 3DS services from Clover are available as two distinct workflows:

1. Enable 3DS on the Merchant Dashboard—If the merchant uses Clover-hosted checkout and other Clover payment products such as payment links, invoices, or payment plugins, then the 3DS authentication service is automatically enabled after the merchant enables 3DS on the Merchant Dashboard as part of fraud tools. See [Enable 3DS on the Merchant Dashboard](https://docs.clover.com/docs/enable-3ds-on-the-merchant-dashboard).
2. Set up 3DS authentication service—If the merchant uses on-device or self-hosted checkout, they need to complete the following to use the 3DS authentication service:

- [Configure 3D Secure SDK for merchant self-hosted checkout](https://docs.clover.com/docs/3ds-secure-configure-sdk)
- [Add the 3DS authentication method to the Create a charge endpoint](https://docs.clover.com/docs/add-3-d-secure-authentication-to-create-a-charge)

***

# 3DS terminology

[block:parameters]
{
  "data": {
    "h-0": "Term",
    "h-1": "Description",
    "0-0": "Card-not-present fraud",
    "0-1": "Card-not-present (CNP) fraud occurs when the customer manually enters credit card information without physically presenting the card to the merchant during a transaction. This type of fraud usually occurs in online or e-commerce transactions, where the cardholder's information, for example, their three-digit security code, is used without the cardholder's knowledge or consent.",
    "1-0": "Chargeback",
    "1-1": "Chargeback is a process that lets customers dispute a transaction made using their credit or debit card and request a refund from their card issuer. In chargeback, the card issuer reverses the transaction, that is, withdraws the funds that were previously deposited into the merchant's bank account and returns them to the customer's account. Merchants need to manage chargebacks effectively to prevent administrative and financial costs and maintain customer satisfaction.  \n**Note: **3DS shifts the liability of any chargebacks due to fraud or disputes from the merchant to the issuer.",
    "2-0": "Clover 3DS",
    "2-1": "When Clover sends 3DS data in an Ecommerce API charge request, and the 3DS authentication is done by a Fiserv 3DS authentication services provider, the `source` of the 3DS authentication in the charge request is CLOVER. See [Add 3-D Secure authentication when creating a charge](https://docs.clover.com/docs/add-3-d-secure-authentication-to-create-a-charge).",
    "3-0": "Non_Clover 3DS",
    "3-1": "When Clover sends 3DS data in an Ecommerce API charge request, and the 3DS authentication is sent to an external authentication services provider, the `source` of the 3DS authentication in the charge request is NON_CLOVER.",
    "4-0": "Challenge flow",
    "4-1": "For card-not-present (CNP) payments, challenge flow indicates that the financial institution (FI) or issuer requires more evidence to verify the legitimacy of the transaction. In the challenge flow, the customer must provide extra information to authenticate the payment, such as a password or a one-time code that the card issuer sends to their mobile device.",
    "5-0": "Frictionless flow",
    "5-1": "For card-not-present (CNP) payments, frictionless flow refers to a seamless process where the financial institution (FI) or issuer can verify the legitimacy of a transaction without requiring additional input from the cardholder. This behind-the-scenes verification lets customers complete their purchases without any noticeable interruptions or authentication steps.",
    "6-0": "Liability shift",
    "6-1": "Liability shift indicates the transfer of responsibility for chargeback losses from the merchant to the financial institution (FI). As issuers are responsible for authenticating transactions, 3DS enables the transfer of liability for any chargebacks resulting from fraud or disputes from the merchant to the issuer. However, if a transaction is not authenticated, the liability stays with the merchant. This shift in liability is beneficial for merchants as it helps reduce the costs associated with chargebacks.  \n**Important:** Liability shift protection applies only to chargebacks related to fraud and does not cover non-fraudulent customer claims. For more information, see [3DS results and liability shift](https://docs.clover.com/docs/3ds-for-clover-merchants-overview#3ds-results-and-liability-shift)."
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]


***

# 3DS payments transaction flow

3DS payments transaction flow includes the following steps:

1. The cardholder makes a purchase and enters card details for payment.
2. The merchant's 3D secure service provider sends the transaction data and an authentication request to the card issuer.
3. The card issuer's 3D secure service provider determines the level of risk inherent in the particular transaction:

- If the transaction is high-risk, a challenge authentication flow is initiated.
- If the transaction is low risk, no additional customer action is needed, and a frictionless authentication flow is initiated.

4. The card issuer sends the authentication result to the merchant.
5. The merchant then submits the transaction for authorization, including the authentication result.

# 3DS results and liability shift

The 3D Secure (3DS) liability shift is a rule that protects merchants from fraudulent transactions. When the 3DS liability shift applies, the liability for fraudulent chargebacks shifts from the business to the card issuer, such as a financial institution (FI) or bank.

When a Clover merchant with 3DS services enabled initiates a transaction, the cardholder's issuing FI or bank authenticates the cardholder. If the authentication is successful, the liability shifts from the merchant to the issuer. The merchant proceeds with authorizing the payment, and the card issuer becomes liable for any fraudulent-type disputes that the customer may file. The merchant then proceeds to authorize the payment, and any fraudulent disputes that may arise from the customer become the responsibility of the card issuer. This implies that in cases of disputes or chargebacks related to fraud, such as a customer denying their involvement or authorization of the transaction, the merchant is generally not held accountable.

> 📘 IMPORTANT
> 
> - Liability shift protection does not cover all 3DS authenticated transactions. The responsibility of issuing a liability shift lies with the card issuer and network.
> - Liability shift protection applies only to chargebacks related to fraud and does not cover non-fraudulent customer claims.

Even with liability shift for 3DS authenticated transactions, the merchant should always take additional steps to check the identity of the customer and reduce the risks of fraud by applying risk rules, such as velocity checks, IP restrictions, safelists, CVV/CV2 matching, and the address verification service (AVS). For more information, see how to [use fraud prevention tools](https://docs.clover.com/docs/protect-ecommerce-merchants-from-card-testing-fraud#3-use-fraud-prevention-tools).

***

# Related topics

- [Enable 3DS on the Merchant Dashboard](https://docs.clover.com/docs/enable-3ds-on-the-merchant-dashboard)
- [Configure 3D Secure SDK for merchant self-hosted checkout](https://docs.clover.com/docs/3ds-secure-configure-sdk)
- [Add the 3DS authentication method to the Create a charge endpoint](https://docs.clover.com/docs/add-3-d-secure-authentication-to-create-a-charge)
