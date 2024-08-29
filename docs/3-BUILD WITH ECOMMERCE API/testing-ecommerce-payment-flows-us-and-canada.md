---
title: "Testing Ecommerce payment flows (US and Canada)"
slug: "testing-ecommerce-payment-flows-us-and-canada"
excerpt: ""
hidden: true
createdAt: "Mon Jun 08 2020 18:45:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
You will need to successfully complete payment flows for all the supported transaction types for your app to be approved.

The following sections provide steps you should follow to confirm your Ecommerce integration properly processes the transactions required for the US and Canada. Your video of each transaction allows Clover to see that the entire payment flow is handled correctly.

## Preparing to test

The test card numbers provided below allow you to test each flow and ensure your application processes the payment as expected. You'll find additional test card numbers [here](https://docs.clover.com/docs/test-card-numbers).

| Card type | Format  | Number              | Response |
| :-------- | :------ | :------------------ | :------- |
| Discover  | Plastic | 6011 3610 0000 6668 | Success  |
| Visa      | Manual  | 4005 5717 0222 2222 | Decline  |

## Testing Ecommerce payment flows

Integrations that support a subset of transaction types can skip the tests that do not apply.

### Test #1: Sale with tipping enabled

1.
2.
3.
4.
5.
6.

_The sale is processed with tipping option presented._

### Test #2: Sale with tipping disabled

1.
2.
3.
4.
5.
6.

_The sale is processed with tipping option _not_ presented._

### Test #3: Sale with tip added and a 15% tip

1.
2.
3.
4.
5.
6.

_The sale with a tip is processed._

### Test #4: Sale with tip option present but not selected

1.
2.
3.
4.
5.
6.

_The sale is processed with no tip selected._

### Test #5: Sale with tipping disabled and partial authorization

This test shows that an integration correctly handles a partial authorization and allows the merchant to complete the transaction with a second form of payment.

1.
2.
3.
4.
5.
6.
7.
8.
9.
10.

### Test #6: Sale with tipping disabled and partial authorization

1.
2.
3.
4.
5.

### Test #7: Refund a specific amount

1.
2.
3.
4.
5.

_The refund is complete._

### Test #8: Refund a partial amount

1.
2.
3.
4.
5.

_The refund is complete._
