---
title: "Use the Clover ECommerce Gift Card API"
slug: "ds-6929-use-the-clover-ecommerce-gift-card-api"
excerpt: ""
hidden: true
createdAt: "Mon Aug 12 2024 06:53:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Aug 12 2024 10:08:29 GMT+0000 (Coordinated Universal Time)"
---
<!-- Gray navigation menu -->

## What is a gift card

A gift card is a prepaid payment card used to make purchases at participating restaurants, stores, or online retailers. A gift card can have different denominations. You can redeem the value of these cards for services, merchandise, or even cash, depending on the terms and conditions set by the card issuer.

## Clover Gift Cards 💳

You can:

- Use Clover Gift Card Solutions to check out online or in person at the point of sale (POS). This is a native gift card with an SCV (security code value) that uses the integrated gift card solution payment gateway from Fiserv.
- Use a non-native gift card with an FCA (foreign access code). A non-Fiserv gift card or a gift card that does not use the Fiserv payment gateway.
- Use the purchase or split tender feature to start the transaction with a gift card and complete the transaction with another credit or debit card.
- Use the Gift Card API to perform the following actions:

  - Activation
  - Balance inquiry
  - Redeem
  - Reload
  - Cashout
  - Refund or void a transaction

## Use the Clover Gift Card API

### Prerequisites for merchants

- Set up gift card tiers in Gift Solutions. For merchants who use the Clover device, configure a merchant account for the gift card tiers in Clover Gift Card Solutions to enable the processing of gift cards. The Clover server synchronizes the order data with the merchant's Clover devices. You can use the gift card endpoint to leverage the gift card features added to Clover payment solutions.
- Your merchant needs to sign up for [Clover Gift Cards](https://www.clover.com/pos-systems/gift-cards) for gift card plans.

<br />

### Prerequisites for developers

<!--

 

Index page design idea:

<https://developer.fiserv.com/product/CommerceHub/docs/?path=docs/Resources/Guides/Payment-Sources/Gift-Card.md>.

\-->
