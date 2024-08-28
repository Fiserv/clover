---
title: "Error codes (internal)"
slug: "error-codes-internal"
excerpt: ""
hidden: true
createdAt: "Thu Jun 18 2020 14:47:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
The Ecommerce API returns error codes and messages when a request contains invalid or incomplete data and Clover cannot process the request as sent. The following tables explain the errors you may encounter.

Invalid request errors

| Error code                     | Description                                                                                                            | Request type                                              |    |
| :----------------------------- | :--------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------- | :- |
| amount_too_large               | The `amount` provided exceeds the amount allowed by Clover                                                             | Charge (maybe won't be returned cf invalid_charge_amount) |    |
| amount_too_small               |                                                                                                                        | Not implemented                                           |    |
| api_key_expired                |                                                                                                                        | Any                                                       |    |
| card_declined                  | The `source` provided was declined by the payment gateway                                                              | Charge                                                    |    |
| card_on_file_missing           | The customer attempting to pay does not have a `source` on file to complete the payment                                | Charge                                                    |    |
| charge_already_captured        | The `charge` provided has already been captured                                                                        | Capture charge                                            |    |
| charge_already_refunded        | The `charge` provided has already been refunded                                                                        | Refund                                                    |    |
| charge_disputed                |                                                                                                                        | Not implemented                                           |    |
| charge_exceeds_source_limit    |                                                                                                                        | Not implemented                                           |    |
| charge_expired_for_capture     |                                                                                                                        | Not implemented                                           |    |
| country_unsupported            |                                                                                                                        | Not implemented                                           |    |
| email_invalid                  | The `email` provided is not valid                                                                                      | Create charge, create or update customer, pay for order   |    |
| expired_card                   | The expiration date (a combination of `card.exp_month` and `card.exp_year`) provided is in the past                    | Token                                                     |    |
| incorrect_address              |                                                                                                                        | Not implemented                                           |    |
| incorrect_cvc                  | The `card.cvv` provided  is not a three- or four-digit value                                                           | Token                                                     |    |
| incorrect_number               | The value provided in `card.number` is not valid                                                                       | Token                                                     |    |
| incorrect_zip                  |                                                                                                                        | Not implemented                                           |    |
| invalid_card_type              | The `card.brand` provided is not a recognized value                                                                    | Token                                                     |    |
| invalid_wallet_type            |                                                                                                                        | Not yet implemented (wallets coming Sept 2020)            |    |
| invalid_charge_amount          | The `amount` provided exceeds the amount allowed by Clover                                                             | Charge                                                    |    |
| invalid_request                | The value provided in `card.number` is not a valid raw or encrypted PAN                                                | Token                                                     |    |
| invalid_tip_amount             | The `tip_amount` provided is not a valid amount                                                                        | Create charge and pay for order                           |    |
| invalid_tax_amount             | The `tax_amount` provided is not a valid amount                                                                        | Create charge                                             |    |
| invalid_cvc                    | The `card.cvv` provided  is not a three- or four-digit value                                                           | Create token, create or update customer                   |    |
| invalid_expiry_month           | The `card.exp_month` provided is not a one- or two-digit value                                                         | Token                                                     |    |
| invalid_expiry_year            | The `card.exp_year` provided is not a two- or four-digit value                                                         | Token                                                     |    |
| invalid_number                 | The PAN provided in `card.number` is invalid                                                                           | Token                                                     |    |
| missing                        | The token request failed upstream and the upstream message could not be processed                                      | Token                                                     |    |
| order_already_paid             | The order identified by the ID in the request URL has already been paid                                                | Pay order                                                 |    |
| order_creation_failed          |                                                                                                                        | Not implemented                                           |    |
| order_required_settings        |                                                                                                                        | Not implemented                                           |    |
| order_status_invalid           |                                                                                                                        | Not implemented                                           |    |
| parameter_invalid_empty        |                                                                                                                        | Not implemented                                           |    |
| parameter_invalid_integer      |                                                                                                                        | Not implemented                                           |    |
| parameter_invalid_string_blank |                                                                                                                        | Not implemented                                           |    |
| parameter_invalid_string_empty |                                                                                                                        | Not implemented                                           |    |
| parameter_missing              |                                                                                                                        | Not implemented                                           |    |
| parameter_unknown              |                                                                                                                        | Not implemented                                           |    |
| postal_code_invalid            |                                                                                                                        | Not implemented                                           |    |
| processing_error               | The request could not be processed as submitted                                                                        | Create token and create customer                          |    |
| rate_limit                     | Your application has made too many requests and additional requests will not be processed until the rate limit expires | Any                                                       |    |
| resource_missing               | The item provided in the request does not exist                                                                        | Any                                                       |    |
| token_already_used             | The `source` value is not a multipay token and was already used for a different payment                                | Charge                                                    |    |
