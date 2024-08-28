---
title: "HTTP Status and Error codes"
slug: "appendix"
excerpt: ""
hidden: false
metadata: 
  description: "This page provides status and error codes related to Clover Payments API."
  image: []
  robots: "index"
createdAt: "Mon Apr 04 2022 23:29:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


For test cards, see [Test card numbers](https://docs.clover.com/docs/test-card-numbers).

## HTTP Status Code Summary

| Code number        | Description       |
| :----------------- | :---------------- |
| 200                | OK                |
| 400                | Bad Request       |
| 401                | Unauthorized      |
| 402                | Request Failed    |
| 403                | Forbidden         |
| 404                | Not Found         |
| 409                | Conflict          |
| 429                | Too Many Requests |
| 500, 502, 503, 504 | Server Errors     |

[block:html]
{
  "html": "<div></div>\n\n<style></style>"
}
[/block]


## Error codes from Clover Payment APIs

| Code                    | Description                                                                                                         | Request type                                              | Message to buyer                                                            |
| :---------------------- | :------------------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------- | :-------------------------------------------------------------------------- |
| amount_too_large        | The `amount` provided exceeds the amount allowed by Clover ($999, 999.99).                                          | Create charge and pay for order.                          | Transaction cannot be processed, please contact the merchant.               |
| card_declined           | The `source` provided was declined by the payment gateway.                                                          | Create charge and pay for order.                          | Transaction declined, please use a different card.                          |
| card_on_file_missing    | The customer attempting to pay does not have a source on file to complete the payment.                              | Charge                                                    | Transaction failed, incorrect card data.                                    |
| charge_already_captured | The `charge` provided has already been captured.                                                                    | Capture charge                                            | Transaction has already been captured.                                      |
| charge_already_refunded | The `charge` provided has already been refunded.                                                                    | Refund                                                    | Transaction has already been refunded.                                      |
| email_invalid           | The `email` provided is not valid.                                                                                  | Create charge, create, or update customer, pay for order. | Email ID is invalid, enter valid email ID and retry.                        |
| expired_card            | The expiration date (the combination of `card.exp_month` and `card.exp_year`) provided is in the past.              | Token                                                     | Card expired, enter valid card number and retry.                            |
| incorrect_cvc           | The `card.cvv` provided is not a three- or four-digit value.                                                        | Token                                                     | CVV value is incorrect, enter correct CVV value and retry.                  |
| incorrect_number        | The value provided in `card.number` is not valid.                                                                   | Token                                                     | Card number is invalid, enter valid card number and retry.                  |
| invalid_card_type       | The `card.brand` provided is not a recognized value.                                                                | Token                                                     | Card brand is invalid or not supported, please use valid card and retry.    |
| invalid_charge_amount   | The `amount` provided exceeds the amount allowed by Clover.                                                         | Charge                                                    | Invalid transaction amount, please contact merchant.                        |
| invalid_request         | The value provided in `card.number` is not a valid raw or encrypted PAN.                                            | Token                                                     | Card is invalid, please retry with a new card.                              |
| invalid_tip_amount      | The `tip_amount` provided is not a valid amount.                                                                    | Create charge and pay for order.                          | Invalid tip amount, please correct and retry.                               |
| invalid_tax_amount      | The `tax_amount` provided is not a valid amount.                                                                    | Create charge                                             | Incorrect tax amount, please correct and retry.                             |
| Missing                 | The token request failed upstream, and the upstream message could not be processed.                                 | Token                                                     | Unable to process transaction.                                              |
| order_already_paid      | The order identified by the ID in the request URL has already been paid.                                            | Pay order                                                 | Order already paid.                                                         |
| processing_error        | A generic error indicating that the request could not be processed as submitted.                                    | Any                                                       | Transaction could not be processed.                                         |
| rate_limit              | Your application made too many requests and additional requests will not be processed until the rate limit expires. | Any                                                       | Transaction could not be processed, please contact the merchant.            |
| resource_missing        | The data item (charge, order, or refund) provided in the request does not exist.                                    | Any                                                       | Transaction could not be processed due to incorrect or invalid data.        |
| token_already_used      | The source value is not a `multi-pay` token and was already used for a different payment.                           | Charge                                                    | Transaction could not be processed, please re-enter card details and retry. |
