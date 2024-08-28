---
title: "Ecommerce - Card tokenization"
slug: "ecommerce-tokenization"
excerpt: ""
hidden: true
createdAt: "Tue Jul 23 2024 10:40:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Aug 07 2024 15:08:49 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Tokenization is a process to substitute sensitive data, such as credit card numbers or PAN, with a non-sensitive equivalent value known as Token. 

A token cannot be reverse-engineered by a third-party to get the original sensitive data. By using a token in place of raw credit card data, we can minimize the risk of handling sensitive data in transit. See [Ecommerce Tokenization](https://medium.com/clover-platform-blog/ecommerce-tokenization-understanding-methods-that-keep-card-data-safe-5dea8e95a3de) to learn more.

## Advantages of tokenization

- Enhance security - Replace PAN details on a card with a randomly generated token.
- Improves PCI DSS Compliance - Meet security requirements and reduce the scope and cost of PCI compliance efforts.
- Improves authorization rates - Payment tokens improve the gateway payment authorization rates.
- Facilitate recurring payments - Allow more subscription billing and uninterrupted service for subscription-based businesses.

Clover supports the following tokenization services:

- [Clover tokenization](https://docs.clover.com/docs/create-a-card-token)
- [<<glossary:TransArmor token>>](https://docs.clover.com/docs/use-transarmor-token)

The following table explains the tokenization services in Clover to determine your integration with Clover:

[block:parameters]
{
  "data": {
    "h-0": "Use cases",
    "h-1": "Clover tokens",
    "h-2": "TransArmor tokens",
    "0-0": "Function",
    "0-1": "Generate tokens to process charges on the Clover gateway",
    "0-2": "Generate payment tokens to process charges on the Clover and Fiserv payment system",
    "1-0": "Structure",
    "1-1": "Alphanumeric  \nExample: clv_12345jklbhd",
    "1-2": "Numeric  \nExample: 1234456789021",
    "2-0": "Scope",
    "2-1": "Specific to a merchant or merchant group",
    "2-2": "Specific to a merchant or a merchant group",
    "3-0": "Compatibility",
    "3-1": "Specific to Clover payments",
    "3-2": "Compatible with across Fiserv payment systems"
  },
  "cols": 3,
  "rows": 4,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
