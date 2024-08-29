---
title: "Sales decline disclosure templates"
slug: "sales-decline-disclosure-templates"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides sales decline template to display the decline notice."
  image: []
  robots: "index"
createdAt: "Tue Dec 13 2022 15:16:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


If the payment fails resulting in a sales decline, you need to display a decline disclosure notice to the customer. Use the relevant sales decline template to display the decline notice:

## Sales decline due to negative data or risk

Transactions may be declined due to either negative information in TeleCheck’s database or TeleCheck’s issuance of a risk-based decline. In this case, the Adverse Action Disclosure notice must be provided to customers for any transaction type every time TeleCheck issues an applicable decline. The decline of a single-entry transaction or numerous times when processing recurring payments can trigger the issuance of an Adverse Action Disclosure.

_We are sorry that we cannot complete your transaction. An adverse action was taken in relation to your transaction based, in part, on information obtained from TeleCheck Services LLC, a consumer reporting agency.  
**What is TeleCheck? **TeleCheck provides payment acceptance services to both merchants and financial institutions by reporting on check writing histories. Please visit <https://getassistance.telecheck.com/index.html> to learn more about TeleCheck._  
_You may have received a decline for one of the following reasons:_  
 _1. Risk-based Decline (Code 3)_  
_TeleCheck monitors transactions for risk indicators to determine whether they appear to be potentially high risk to protect consumers, merchants, and financial institutions from fraud and losses. Some reasons for a transaction being flagged as high risk are:_  
    a. _Transaction carried risk indicators indicating potentially fraudulent activity on your account_  
    b. _Insufficient history on your account (new bank account or infrequent check writing)_

 _2. Unpaid debt associated with your checking account (Code 4)_  
 _TeleCheck will issue a decline alert if it has at least one record in its files of unpaid debt associated with your bank account and/or personal information. Please contact TeleCheck to learn more details about the information in its records and what you can do to resolve any issues._

_Contact Information  
TeleCheck Services, Inc.  
ATTN: Resolutions Department  
P. O. Box 6806 Hagerstown,  
MD 21741-6806  
Tel: 1-800-366-2425 <https://getassistance.telecheck.com/index.html>  
You may call or write TeleCheck for further information. TeleCheck may need to verify personal information in order to authenticate your specific transaction and protect your personal information in our databases. You will need to provide (1) the declined transaction’s record number (if provided), (2) your driver’s license number and its state of issuance (3) if applicable, the bank routing and account number you used for the declined transaction, and (4) your social security number (if the declined transaction was with a financial institution).  
**Under the Fair Credit Reporting Act**  
Consumers have the right to a free copy of their information held in TeleCheck’s files for a period of 60 days following an adverse action. Consumers also may dispute the accuracy or completeness of any information in TeleCheck’s consumer report. TeleCheck did not make the decision to take an adverse action (that is, to not accept a payment or approve the opening of an account) and may be unable to provide you with all specific reasons as to why an adverse action was taken._

## Sale error response

The following text is used when the payment is not declined but data provided cannot be verified:  
_We are unable to verify your checking account or identity information. Please review the information you entered to ensure that all information is correct._

## Sale ineligible response

The following text is used when the payment is not eligible for processing as an electronic item:  
_We are unable to electronically process this transaction. Please use a different form of payment at this time._
