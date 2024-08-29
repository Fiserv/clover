---
title: "(DS- 6417)Clover iframe features"
slug: "clover-iframe-features-copy"
excerpt: ""
hidden: true
createdAt: "Tue May 28 2024 06:22:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Aug 15 2024 10:38:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Learn how to add Clover-hosted iframe as a single page component with all of the required fields and to integrate each one individually.”>"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover iframe (inline frame) provides access to card and page elements. On your payment page, you can add Clover-hosted iframe as a single page component with all of the required fields, or integrate each page element individually, if required for the design of your app.

# Card elements

The SDK includes seven card elements that you can combine and use as required fields in your application. For each element, you can set custom styling as a second parameter. See [Customize iframe elements with CSS](doc:customizing-iframe-elements-with-css) for more information on styling iframes. All elements are auto-validating.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3fcf4ec-Screenshot_2024-08-10_at_20.43.02.png",
        null,
        "Card elements - GPay and Apple Pay"
      ],
      "align": "center",
      "sizing": "600px",
      "border": true,
      "caption": "Card elements - GPay and Apple Pay"
    }
  ]
}
[/block]


## 1. cardNumber

Use the `cardNumber` element to accept a credit card number. Optionally, you can set up custom styling with the second parameter when creating a new `cardNumber`.

```javascript
const card = elements.create('CARD_NUMBER', styles);
```

## 2. cardHolderName

Use the `cardHolderName` element to accept a credit cardholder's name. Optionally, you can set up custom styling with the second parameter when creating a new `cardHolderName`. 

```javascript
const card = elements.create('CARD_NAME', styles);
```

## 3. cardDate

Use the `cardDate` element to accept a credit card's expiration date. Optionally, you can set up custom styling with the second parameter when creating a new `cardDate`. This element supports both MM/YY and MM/YYYY formats.

```javascript
const cardDate = elements.create('CARD_DATE', styles);
```

## 4. cardCvv

Use the `cardCvv` element to accept a card verification number. Optionally, you can set up custom styling with the second parameter when creating a new `cardCvv`.

```javascript
const cardCvv = elements.create('CARD_CVV', styles);
```

## 5. cardPostalCode

Use the `cardPostalCode` element to accept a cardholder's postal code. Optionally, you can set up custom styling with the second parameter when creating a new `cardPostalCode`.

```javascript
const cardPostalCode = elements.create('CARD_POSTAL_CODE', styles);
```

## 6. cardStreetAddress

Use the `cardStreetAddress` element to accept a cardholder's street address. This information is used for all Address Verification Service (AVS) fraud rules. Optionally, you can set up custom styling with the second parameter when creating a new `cardStreetAddress`.

**Note:** You must pass the `merchantId` parameter when configuring the Clover SDK to use the street address field. If the <<glossary:merchantId>> is not accessible and the merchant has enabled the AVS fraud rules, the payment from a tokenized card fails with an AVS error at the time of charge or order pay.

```javascript java
const cardPostalCode = elements.create('CARD_POSTAL_CODE', styles);

const clover = new Clover('12a3b45167a89123d4567989123e45f67', {
    merchantId: 'xxxxxxxxxxxxx'
});
const elements = clover.elements();
```

## 7. paymentRequestButton

Use the paymentRequestButton element to add a button to request payments for transactions using Apple Pay® or Google Pay™.

### Add Apple Pay button to the Clover iframe

Clover lets accept payments through Apple<sup>®</sup> Pay using iframe integrations. 

#### Prerequisites

1. **Domain validation**: Clover recommends that merchants verify their domains through the Merchant Dashboard before hosting the Apple Pay button on iframe. See [take payments with Apple Pay](https://www.clover.com/help/take-payments-apple-pay).
2. **Support and eligibility**: Apple Pay services are available on supported browsers (Safari version 17.5 or above) or devices (Apple Pay v3) for eligible merchants.
3. **Guidelines, terms, and conditions**: 
   - Follow the [Apple Pay Web Brand Guidelines for all](https://developer.apple.com/apple-pay/acceptable-use-guidelines-for-websites/)  Apple Pay assets and button designs.
   - Agree to the [Apple Pay API Terms & conditions](https://www.braintreepayments.com/legal/apple-pay-web-terms)  when you use Apple Pay integrations.

#### Add button for Apple Pay transactions

Use the `paymentRequestButton` element to add a button for Apple Pay™ transactions. When you click the ApplePay™ button, a new window displays for the Apple Pay transaction flow. The button size is rendered based on the width and height of the `#payment-request-button` element. When creating a new `paymentRequestButton` the payment `amount` (in cents) is required.

- Use the  [Apple Pay Web Brand Guidelines](https://developer.apple.com/apple-pay/acceptable-use-guidelines-for-websites/). 
- Use specific size properties for the Apple Pay payment button:
  - display: inline-block;
  - background-size: 100% 60%;
  - background-repeat: no-repeat;
  - background-position: 50% 50%;
  - border-radius: 5px;
  - padding: 0px;
  - box-sizing: border-box;
  - Default width is `300px (min-width: 200px;)`
  - Default height is `40px (min-height: 32px;)(max-height: 64px;)`
  - Values for `max-width` and `max-height` are set by the width and height of the `<div>` container you use for mounting the `paymentRequestButton (<div id="payment-request-button"></div>)`.
- Use a wrapper for the custom view.

```javascript
// Sample payment amount
const applePayRequest = clover.createApplePaymentRequest({amount: 1290, countryCode: 'CA', currencyCode: 'USD'});

//By default USD and US, amounts should be sent in cents. 
// Example:

const applePayRequest = clover.createApplePaymentRequest({amount: 1290});

//Example of response: 
{
"countryCode":"US",
"currencyCode":"USD",
"merchantCapabilities":["supports3DS","supportsEMV"],
"supportedNetworks":["visa","masterCard","amex","discover"],
"total":{
"label":"Amount to be   charged", "type":"final",
"amount":"12.90"
},
"requiredShippingContactFields":["email"],
"requiredBillingContactFields":["postalAddress","name"]
}

// Create paymentRequestButton & mount to <div> container
const paymentRequestAppleButton = elements.create('PAYMENT_REQUEST_BUTTON_APPLE_PAY', {
    applePaymentRequest: applePayRequest, sessionIdentifier: '{clover merchant uuid/clover app uuid}'
  });
Note: If merchants register their domains in the Merchant Dashboard, they are required to pass merchant uuid. Also, if developers register their domains through the developer_app settings on the Developer Dashboard, they are required to pass developer_app uuid.

  paymentRequestAppleButton.mount('#{apple-div}');

Note://#{apple-div} is an element ID where a button will be mounted

//Use the following method if you update the amount during the session:
clover.updateApplePaymentRequest({amount: 2400, countryCode: 'US', currencyCode: 'USD'})

Note: Pass the same country and currency codes that are used during the initial request creation.
```

**Tip:** The ApplePay button provides an encrypted Clover payment token. When the token is received, a charge or pay sessions is initiated separately.

```javascript
// Handle validation errors after tokenization

paymentRequestAppleButton.addEventListener('paymentMethod', function(tokenData) {
  console.log(tokenData);});
```

#### Configure webhooks

You need to receive and respond to the following webhook notifications:

1. Add an Event Listener for Payment Method:  
   Before creating a payment session, set up an event listener for the 'paymentMethod' event on the window object. This will allow you to get the token details when the event occurs.

Use the following methods to update the status:

```javascript
window.addEventListener('paymentMethod', (event) => {
const { tokenRecieved, customerEmail, status } =  event?.detail;
});
```

**Note:** The Apple Pay session lasts for 30 seconds. Therefore, complete the charge process and SDK status update (SUCCESS or FAIL) within 30 seconds.

2. Update Apple Pay Session Status:  
   After the transaction is complete (whether it succeeds or fails), update the Apple Pay session status.

**Note:** If a customer cancels an active Apple Pay transaction session while the payment is in progress or if the session times out, initiate a void for the payment.

Use the following methods to update the status:

```javascript
window.addEventListener('paymentMethodEnd', (event) => {
  const { eventMessage, status } = event?.detail
  if (status === 'session_cancelled') {
    //void the payment if it was executed or initiated 
  }
});
```

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/61bcd6c-2024-08-08_23-00-18.png",
        "",
        "Default button that displays - Apple Pay"
      ],
      "align": "center",
      "sizing": "50",
      "border": true,
      "caption": "Apple Pay button"
    }
  ]
}
[/block]


[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/10b78e0-image_12.png",
        "",
        "Apple Pay payment button with credit card"
      ],
      "align": "center",
      "sizing": "50",
      "border": true,
      "caption": "Apple Pay payment button with credit card"
    }
  ]
}
[/block]


> 🚧 IMPORTANT
> 
> You are agreeing to the [Apple Pay API Terms & conditions](https://www.braintreepayments.com/legal/apple-pay-web-terms)  when you use Apple Pay integrations.

### Add Google Pay button to Clover iframe

Clover lets you accept payments through Google Pay using iframe integrations.

#### Prerequisites

- Follow the [Google Pay Web Brand Guidelines](https://developers.google.com/pay/api/web/guides/brand-guidelines)  for all Google Pay assets and button designs.
- Agree to the [Google Pay API Terms of Service](https://payments.developers.google.com/terms/sellertos)  when you use Google Pay integrations.

#### Add a button for Google Pay transactions

Use the `paymentRequestButton` element to add a button for Google Pay™ transactions. When you click GPay™, a new window displays for the Google Pay flow. The size of the button is rendered based on the width and height of the `#payment-request-button` element. When creating a new paymentRequestButton, the payment amount (in cents) is required.

1. Use the [Google Pay Web Brand Guidelines](https://developers.google.com/pay/api/web/guides/brand-guidelines)  .
2. Use specific size properties for the Google Pay payment button:
   - Default width is `90px` (min-width: 90px;)
   - Default height is `40px` (`min-height: 40px;`)
   - Values for`max-width` and `max-height` are set by the width and height of the `<div>` container you use for mounting the `paymentRequestButton` (`<div id="payment-request-button"></div>`).

```javascript
// Sample payment amount
const paymentReqData = {
  total: {
    label: 'Demo total',
    amount: 1099,
  },
  // Default buttonType is 'long' for button with card brand & last 4 digits
  options: {
    button: {
      buttonType: 'short' // For button without additional text
    }
  }
};

// Create paymentRequestButton & mount to <div> container
const paymentRequestButton = elements.create('PAYMENT_REQUEST_BUTTON', {
  paymentReqData
 });

paymentRequestButton.mount('#payment-request-button');

// Handle validation errors after tokenization
paymentRequestButton.addEventListener('paymentMethod', function(tokenData) {
  console.log(tokenData);
});
```

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/07013ed-GPay_with_last4.png",
        "GPay_with_last4.png",
        620
      ],
      "align": "center",
      "sizing": "50",
      "border": true,
      "caption": "Default button that displays if the customer has a saved payment method"
    }
  ]
}
[/block]


[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/69f8d0f-test_card.png",
        null,
        "Default button that displays if the customer does not have a saved payment method"
      ],
      "align": "center",
      "sizing": "650px",
      "border": true,
      "caption": "Default button that displays if the customer does not have a saved payment method"
    }
  ]
}
[/block]


> 🚧 IMPORTANT
> 
> By using Google Pay integrations, you are agreeing to the <a href="https://payments.developers.google.com/terms/sellertos" target="_blank">Google Pay API Terms of Service</a>.

# Page elements

The Clover Privacy Policy is automatically added to footer of every iframe using a `<div>` container with the `clover-footer` class.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/91966ae-Clover_iframe_footer.png",
        "Clover iframe footer.png",
        806
      ],
      "align": "center",
      "sizing": "80",
      "border": true,
      "caption": "Secure Payments Powered by Clover - Privacy Policy"
    }
  ]
}
[/block]
