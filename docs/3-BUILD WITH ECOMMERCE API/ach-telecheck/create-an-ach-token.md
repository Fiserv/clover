---
title: "Create an ACH token"
slug: "create-an-ach-token"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to create an ACH token to create single pay token for single payments."
  image: []
  robots: "index"
createdAt: "Mon Sep 11 2023 15:17:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 09:04:13 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=\"Learn how to create an ACH token to create single pay token for single payments.\">\n\n<!--DS-5688-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Automated Clearing House (ACH) is an electronic network for processing electronic payments between banks. To process secure ACH payments, use the API `source` token along with an [OAuth token](https://docs.clover.com/docs/obtaining-an-oauth-token) to complete the Ecommerce API flow.

## Steps

1. [Generate a PAKMS key](https://docs.clover.com/docs/ecommerce-generating-a-card-token#generate-a-pakms-key).
2. Send a POST request to the `/v1/tokens` endpoint. See [Create an ACH token](https://docs.clover.com/reference/create-ach-token).
3. Enter information in the required fields.

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "h-2": "Require/Optional",
    "0-0": "`bank_account_number`",
    "0-1": "Customer's bank account number.  \nLength: 10–12 digits.",
    "0-2": "Required",
    "1-0": "`bank_routing_number`",
    "1-1": "Customer's bank routing number. A 9-digit code that identifies the transaction source of any financial institution (FI).",
    "1-2": "Required",
    "2-0": "`encrypted`",
    "2-1": "Indicates whether the bank account number and customer identifier (Id) are encrypted.  \nValues:  \n  \n- True  \n- False",
    "2-2": "Optional",
    "3-0": "`check_type  `",
    "3-1": "Indicates whether a bank account is a personal or a business account.  \nValues:  \n  \n- Personal_check (first name, last name, and email required)  \n- Corporate_check (first name, last name, and email not required)",
    "3-2": "Required",
    "4-0": "`account_type`",
    "4-1": "Indicates whether a bank account is a checking or a savings account.  \nValues:  \n  \n- Savings  \n- Checking",
    "4-2": "Required",
    "5-0": "`customer_id_type`",
    "5-1": "Indicates the type of customer identification document.  \nExample: driver_license, ssn, tax_id, or miilitary_id",
    "5-2": "Required",
    "6-0": "`customer_id_state`",
    "6-1": "State indicated on the customer ID, for example, NJ driver license.",
    "6-2": "Required",
    "7-0": "`customer_id`",
    "7-1": "Value or details of the customer ID, for example, driver license number.",
    "7-2": "Required",
    "8-0": "`first_name`",
    "8-1": "First name on the check. ",
    "8-2": "Required for personal check.",
    "9-0": "`last_name`",
    "9-1": "Last name on the check. ",
    "9-2": "Required for personal check.",
    "10-0": "`business_name`",
    "10-1": "Business name on the check. ",
    "10-2": "Required for corporate check.",
    "11-0": "`email`",
    "11-1": "Customer’s email address.",
    "11-2": "Required",
    "12-0": "`phone`",
    "12-1": "Customer’s phone number.",
    "12-2": "Required",
    "13-0": "`session_id`",
    "13-1": "Indicates the session identification of an authenticated session.",
    "13-2": "Optional",
    "14-0": "`address_line1`",
    "14-1": "First line of the address. Can include the street address, PO box, or company name.",
    "14-2": "Required",
    "15-0": "`address_line2`",
    "15-1": "Second line of the address. Can include the apartment, suite, unit, or building number.",
    "15-2": "Optional",
    "16-0": "`address_city`",
    "16-1": "City of the customer address. Can include district, suburb, town, or village.",
    "16-2": "Required",
    "17-0": "`address_state`",
    "17-1": "State of the customer address. Can include county, province, or region.",
    "17-2": "Required",
    "18-0": "`address_zip`",
    "18-1": "Postal or ZIP code of the customer address.",
    "18-2": "Required",
    "19-0": "`address_country`",
    "19-1": "Billing address country, if provided.",
    "19-2": "Optional",
    "20-0": "`agreement`",
    "20-1": "Agreement-related information.  \n**Note:** Use the generic id for the sandbox: `2c74dcc0-61ad-4f08-8764-a29aeb98f4a4`  \nor for production: `4f77df6d-70c9-4f36-af1d-f8ad1ad7b0cc`",
    "20-2": "Required",
    "21-0": "`apikey`",
    "21-1": "Universally unique identifier (ID) of the API.",
    "21-2": "Required"
  },
  "cols": 3,
  "rows": 22,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


A single-use ACH token is returned. The token is alphanumeric and begins with `clv\_`. Example:      `clv_1ABCDefgHI23jKL4m5nOPqR`

4. Use the ACH token for a single payment for [charge](https://docs.clover.com/reference/createcharge) or [pay for an order](https://docs.clover.com/reference/postordersidpay).

## Request example

```curl
curl --request POST \
     --url 'https://token-sandbox.dev.clover.com/v1/tokens' \
     --header 'apikey: xxx' 
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '{
        "ach": {
                "bank_account_number": "1234567891",
                "bank_routing_number": "123456789",
                "check_type": "personal_check",
                "account_type": "checking",
                "customer_id_type": "driver_license",
                "customer_id_state": "CA",
                "customer_id": "10981111",
                "first_name": "John",
                "last_name": "Doe",
                "address_line1": "1800 Amphibious Blvd",
                "address_city": "Mountain View",
                "address_state": "CA",
                "address_zip": "94045",
                "phone": "0005550001",
                "email": "john.doe@example.com",
                "agreement": {
                	"agreement_id": "2c74dcc0-61ad-4f08-8764-a29aeb98f4a4",
                	"type": "E_CHECK_GENERIC",
                	"locale": "en_US",
                	"template_data": "firstName:John"
                }
        },
}'
```

## Response example

```java
{"id": "clv_1ABCDefgHI23jKL4m5nOPQrS", "object": "token", "ach": {"account_last4": "7891", "routing_last4": "6789"}}
```
