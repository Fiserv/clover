---
title: "Customer API permissions in the Europe region"
slug: "customers-api-eu-permissions"
excerpt: ""
hidden: false
createdAt: "Mon May 13 2019 20:59:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:23 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


In the the Europe region, Clover has updated how much customer data is accessed by apps using the [Customers](ref:customers-1) endpoint. Every element in the Customers endpoint is considered personal identifiable information (PII). 

PII collection, storage, and use is regulated by laws applicable to the regions in which the third-party developer apps and their partner merchants operate. This does not imply any changes to the format of the Customers API endpoint; only that region-based permissions must be in place to access data in apps, using the same calls.

## Data minimization and required permissions

Permissions to access each data element in the Customers endpoint are as follows:

### Customer records

Based on payment type and a customer's choice to share their data, Clover devices may create a customer record. This record may reveal email addresses, phone numbers, home/business addresses, purchase history, and other data points that directly or indirectly identify an individual.

Before we grant access to customer records, we want to ensure that this access is a necessity for each reviewed app.

### Current permissions and limits

With our current `CUSTOMERS_R` and `CUSTOMERS_W` permission structure, your app has access to all customer data. If your app requires just these permissions, your app’s access to the Customer endpoint is reduced to the following subset of PII:

- `id` (Customer UUID)
- `merchant.id` (Merchant UUID)
- `firstName`
- `lastName`
- `customerSince`

### Required permissions

For the customer data elements not listed above, required permissions to the Customers endpoint are granted at the field-level. This level of granularity enables your app to retrieve only the PII it needs to function, helping both you and Clover minimize the data accessed and shared.

You must requestthe following permissions to receive field-level access to each respective data element of the Customers endpoint:

[block:parameters]
{
  "data": {
    "h-0": "Element",
    "h-1": "Required permission",
    "0-0": "`addresses`",
    "0-1": "`CUSTOMERS_ADDRESS_R`  \n`CUSTOMERS_ADDRESS_W`",
    "1-0": "`emailAddresses`",
    "1-1": "`CUSTOMERS_EMAIL_R`  \n`CUSTOMERS_EMAIL_W`",
    "2-0": "`phoneNumbers`",
    "2-1": "`CUSTOMERS_PHONE_R`  \n`CUSTOMERS_PHONE_W`",
    "3-0": "`cards`",
    "3-1": "`CUSTOMERS_CARDS_R`  \n`CUSTOMERS_CARDS_W`",
    "4-0": "`marketingAllowed`",
    "4-1": "`CUSTOMERS_MARKETING_R`  \n`CUSTOMERS_MARKETING_W`",
    "5-0": "`metadata.businessName`",
    "5-1": "`CUSTOMERS_BUSINESSNAME_R`  \n`CUSTOMERS_BUSINESSNAME_W`",
    "6-0": "`metadata.dobYear`  \n`metadata.dobMonth`  \n`metadata.dobDay`",
    "6-1": "`CUSTOMERS_BIRTHDATE_R`  \n`CUSTOMERS_BIRTHDATE_W`",
    "7-0": "`metadata.note`",
    "7-1": "`CUSTOMERS_NOTE_R`  \n`CUSTOMERS_NOTE_W`"
  },
  "cols": 2,
  "rows": 8,
  "align": [
    "left",
    "left"
  ]
}
[/block]


For example, if an app has just the `CUSTOMERS_EMAIL_R` permission, the response includes the customer’s email address and excludes all other fields in each Customer object.

## Data rights

These changes do not directly affect you or your application/integration, nor affect your obligations under applicable data privacy legislation. For instance, you are required to respond to and facilitate data access requests that come to you from those Clover merchants, merchant employees, or customers of those merchants.

For more on data access requests, review information for:

- United Kingdom (UK) (<a href="https://ico.org.uk/for-organisations/guide-to-data-protection/guide-to-the-general-data-protection-regulation-gdpr/individual-rights/" target="_blank">individual customer rights</a>)
- Rest of the European Union (EU) (<a href="https://europa.eu/youreurope/business/dealing-with-customers/data-protection/data-protection-gdpr/" target="_blank">Data protection under General Data Protection Regulation (GDPR)</a>)

## Data retention

Clover disables access to a customer record after a fixed time of not having meaningful interactions with the customer or customer record.
