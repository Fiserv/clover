---
title: "Use internet check acceptance"
slug: "internet-check-acceptance"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how the Clover payment system supports internet check acceptance (ICA) which allows eCommerce merchants to take payments over the internet."
  image: []
  robots: "index"
createdAt: "Tue Dec 13 2022 15:15:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 09:08:35 GMT+0000 (Coordinated Universal Time)"
---
<meta name="description" content="Learn how the Clover payment system supports internet check acceptance (ICA) which allows eCommerce merchants to take payments over the internet.">.

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover payment system supports internet check acceptance (ICA) which allows eCommerce merchants to take payments over the internet. The ICA process requires merchants to provide payment details and customer consent to process the payment. The merchant needs to display a disclaimer agreement using specific templates to get the customer’s consent.

## Payment process required fields

Here is the list of optional and required fields that are displayed in the order payment process. You can skip the optional fields or add additional ones as per your process, but you must include all the required fields.

[block:parameters]
{
  "data": {
    "h-0": "Fields",
    "h-1": "Description",
    "h-2": "Required/optional",
    "0-0": "bank_account_number",
    "0-1": "Customer’s bank account number.",
    "0-2": "Required",
    "1-0": "bank_routing_number",
    "1-1": "Customer's bank routing number. A 9-digit code that identifies the transaction source of any financial institution.",
    "1-2": "Required",
    "2-0": "encrypted",
    "2-1": "Indicates whether bank account number and customer ID are encrypted.  \nValues:  \n  \n- True  \n- False",
    "2-2": "Optional",
    "3-0": "check_type",
    "3-1": "Indicates the check type.  \nValues:  \n  \n- Personal check  \n- Corporate check",
    "3-2": "Required",
    "4-0": "account_type",
    "4-1": "Indicates the customer’s bank account type.  \nValues:  \n  \n- Savings  \n- Checkings",
    "4-2": "Required",
    "5-0": "customer_id_type",
    "5-1": "Indicates the type of identification (ID) document for the customer.  \nValues:  \n  \n- Driver license  \n- Tax ID  \n- Military ID",
    "5-2": "Required",
    "6-0": "customer_id_state",
    "6-1": "State indicated on the customer ID, for example, NJ driver's license.  \nSee [State Abbreviation for TeleCheck](doc:state-abbreviation-for-telecheck).",
    "6-2": "Required",
    "7-0": "customer_id",
    "7-1": "Value or details of customer ID, for example, driver's license number.",
    "7-2": "Required",
    "8-0": "first_name",
    "8-1": "First name on the check.",
    "8-2": "- Required if the check type is personal check.  \n- Optional is the check type is corporate check.",
    "9-0": "last_name",
    "9-1": "Last name on the check.",
    "9-2": "- Required if the check type is personal check.  \n- Optional is the check type is corporate check.",
    "10-0": "business_name",
    "10-1": "Business name on the check.",
    "10-2": "- Required if the check type is corporate check.  \n- Optional is the check type is personal check.",
    "11-0": "email",
    "11-1": "Customer’s email address.",
    "11-2": "Required",
    "12-0": "phone",
    "12-1": "Customer’s phone address.",
    "12-2": "Required",
    "13-0": "session_id",
    "13-1": "Temporary identifier that is unique to each customer’s session.",
    "13-2": "Optional",
    "14-0": "address_line1",
    "14-1": "Address line 1 of the customer. Includes the Street address/P.O. Box/Company name.",
    "14-2": "Optional",
    "15-0": "address_line2",
    "15-1": "Address line 2 of the customer. Includes the Apartment/Suite/Unit/Building name.",
    "15-2": "Optional",
    "16-0": "address_city",
    "16-1": "City of the customer address. Includes the District/Suburb/Town/Village.",
    "16-2": "Optional",
    "17-0": "address_state",
    "17-1": "State of the customer address. Includes the County/Province/Region.",
    "17-2": "Optional",
    "18-0": "address_zip",
    "18-1": "ZIP or postal code of the customer address.",
    "18-2": "Required",
    "19-0": "address_country",
    "19-1": "Customer billing address country, if provided.",
    "19-2": "Optional"
  },
  "cols": 3,
  "rows": 20,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


### Generate a session ID

To generate a Session ID, the merchants need to:

1. Create a concatenation of subscriber ID, date, and a 9-digit sequence number incremented with each session of the day. Example: 87654321245516123456789, where:

- 87654321 is the subscriber ID.
- 2/24/11 is the date.
- 123456789 is the sequence number.

2. Apply an SHA-1 hash to the value from step 1. For example, the session ID is: d5f5a536346ecd54423ff9f8c551cd08d16a61be.

## Use agreement templates

The internet check acceptance (ICA) process requires the customer to provide order and payment details and consent to process the payment. The merchant needs to display a disclaimer agreement using specific templates to get the customer’s consent.

Use the templates in this section as given in the authorization disclaimer. The templates contain the required text for ICA authorization agreement. 

Note: The payment process can be completed only after the customer provides consent.

There are two types of templates: Warranty and Verification template. See **How to identify which template to use?** section to identify which template to use.

### Warranty template

**Warranty service in TeleCheck** - This needs to be displayed if the merchant is offering warranty service. Warranty service grants merchants premier-level defense against fraudulent transactions by transferring all fraud liability from the business to TeleCheck. Returned checks become TeleCheck’s responsibility, relieving merchants from potential loss and the copious hours of trying to collect payments on their own. 

#### ICA warranty template for personal checks

_Today, being [**insert today’s date**], I, [**insert consumer’s name**], by entering my routing and account number above and clicking “Authorize,” I authorize my payment in the amount indicated above to be processed as a one-time electronic funds transfer (EFT) or draft drawn from my checking or savings account as indicated above and, if necessary, to have my account electronically credited or debited to correct errors. I understand that my payment will be processed within 1-2 banking days._

_If the payment returns unpaid, I authorize you or your service provider to collect the payment and a one-time return item fee and, if applicable, costs, by EFT(s) or draft(s) drawn from my account. Click here to view your state’s returned item fee and, if applicable, costs (**insert the state fee table URL**).  
Due to the speed of electronic payment processing, I understand that after I authorize my payment, I will not be able to revoke my authorization._

- [ ] I consent to the use of Electronic Records and Signatures (insert Link – Read Electronic Record and Signature Disclosure).

**_PLEASE PRINT A COPY OF THIS PAGE FOR YOUR RECORDS. ALTERNATIVELY, CONTACT US AT [(XXX) XXX-XXXX] TO LEARN HOW YOU CAN OBTAIN A COPY._**

#### ICA warranty template for business checks

_Today, being [**insert today’s date**], I, [**insert first and last name of Company representative**], as an authorized representative of [**insert signer’s Company Name**] \(Company), by entering Company’s routing and account number above and clicking “Authorize,” I authorize the payment in the amount indicated above to be processed as a one-time electronic funds transfer (EFT) or draft drawn from Company’s checking or savings account as indicated above and, if necessary, to have the account electronically credited or debited to correct errors. I understand that the payment will be processed within 1-2 banking days._

_If the payment returns unpaid, I authorize you or your service provider to collect the payment and a one-time return item fee and, if applicable, costs, by EFT(s) or draft(s) drawn from Company’s account. Click here to view your state’s returned item fee and, if applicable, costs (**insert the state fee table URL**).  
Due to the speed of electronic payment processing, I understand that after I authorize the payment on behalf of Company, I will not be able to revoke my authorization._

_I make these authorizations as an authorized representative of Company and Company agrees to be bound by the Nacha Rules in effect, both now and as amended from time to time._

- [ ] I consent to the use of Electronic Records and Signatures (insert Link – Read Electronic Record and Signature Disclosure). 

**_PLEASE PRINT A COPY OF THIS PAGE FOR YOUR RECORDS. ALTERNATIVELY, CONTACT US AT [(XXX) XXX-XXXX] TO LEARN HOW YOU CAN OBTAIN A COPY._**

### Verification template

#### ICA verification template for personal checks

_Today, being [**insert today’s date**], I, [**insert consumer’s name**], by entering my routing and account number above and clicking “Authorize,” I authorize my payment in the amount indicated above to be processed as a one-time electronic funds transfer (EFT) or draft drawn from my checking or savings account as indicated above and, if necessary, to have my account electronically credited or debited to correct errors. I understand that my payment will be processed within 1-2 banking days._

_Due to the speed of electronic payment processing, I understand that after I authorize my payment, I will not be able to revoke my authorization._

- [ ] I consent to the use of Electronic Records and Signatures (i**nsert Link – Read Electronic Record and Signature Disclosure**).

**_PLEASE PRINT A COPY OF THIS PAGE FOR YOUR RECORDS. ALTERNATIVELY, CONTACT US AT [(XXX) XXX-XXXX] TO LEARN HOW YOU CAN OBTAIN A COPY._**

#### ICA verification template for business checks

_Today, being [**insert today’s date**], I, [**insert first and last name of Company representative**], as an authorized representative of [**insert signer’s Company Name**] \(Company), by entering Company’s routing and account number above and clicking “Authorize,” I authorize the payment in the amount indicated above to be processed as a one-time electronic funds transfer (EFT) or draft drawn from Company’s checking or savings account as indicated above and, if necessary, to have the account electronically credited or debited to correct errors. I understand that the payment will be processed within 1-2 banking days._

_Due to the speed of electronic payment processing, I understand that after I authorize the payment on behalf of Company, I will not be able to revoke my authorization._

_I make these authorizations as an authorized representative of Company and Company agrees to be bound by the Nacha Rules in effect, both now and as amended from time to time._

- [ ] I consent to the use of Electronic Records and Signatures (i**nsert Link – Read Electronic Record and Signature Disclosure**).

**_PLEASE PRINT A COPY OF THIS PAGE FOR YOUR RECORDS. ALTERNATIVELY, CONTACT US AT [(XXX) XXX-XXXX] TO LEARN HOW YOU CAN OBTAIN A COPY._**

## Identify a template to use

To know if your merchant is signed up for a Warranty or Settlement product, check the JSON section of the `ecom_config` endpoint.

| Product type (ICA) | Check type | Template type                     |
| :----------------- | :--------- | :-------------------------------- |
| Warranty           | Corporate  | `E_CHECK_ICA_BUSINESS_WARRANTY`   |
| Warranty           | Personal   | `E_CHECK_ICA_PERSONAL_WARRANTY`   |
| Settlement         | Corporate  | `E_CHECK_ICA_BUSINESS_SETTLEMENT` |
| Settlement         | Personal   | `E_CHECK_ICA_PERSONAL_SETTLEMENT` |

Example: Merchants who support the warranty product.

```json
"ach_products" : [ {
      "name" : "internet_check_acceptance",
      "features" : [ "E_CHECK_ICA_BUSINESS_WARRANTY", "E_CHECK_ICA_PERSONAL_WARRANTY" ]
    },
```

Example: Merchants who support the settlement product.

```json
"ach_products" : [ {
      "name" : "internet_check_acceptance",
      "features" : [ "E_CHECK_ICA_BUSINESS_SETTLEMENT","E_CHECK_ICA_PERSONAL_SETTLEMENT" ]
    },
```

## Return payment fees

See [TeleCheck Returned Check Fees](https://merchants.fiserv.com/en-us/customer-center/merchants/telecheck-returned-check-fees/) for the state-by-state collection fee and cost table for returned payments. These state-specific collection fees and costs are subject to change, and linking to a TeleCheck-hosted page minimizes the number of maintenance updates required. You can select how to display these state fees and costs.
