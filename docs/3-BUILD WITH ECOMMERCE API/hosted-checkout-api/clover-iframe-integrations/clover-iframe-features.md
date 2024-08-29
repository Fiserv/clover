---
title: "Clover iframe features"
slug: "clover-iframe-features"
excerpt: ""
hidden: false
metadata: 
  title: "Clover iframe features"
  description: "Learn how to add Clover-hosted iframe as a single page component with all of the required fields and to integrate each one individually."
  image: []
  robots: "index"
createdAt: "Tue Nov 10 2020 23:53:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:46:57 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<meta name=\"description\" content=“Learn how to add Clover-hosted iframe as a single page component with all of the required fields and to integrate each one individually.”>"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The Clover iframe (inline frame) provides access to card and page elements. On your payment page, you can add a Clover-hosted iframe as a single page component with all of the required fields or integrate each page element individually, if required, for the design of your app.

# Card elements

The SDK includes seven card elements that you can combine and use as required fields in your application. For each element, you can set custom styling as a second parameter. See [Customize iframe elements with CSS](doc:customizing-iframe-elements-with-css) for more information on styling iframes. All elements are auto-validating.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/896154a-Card_elements.png",
        null,
        "Card elements"
      ],
      "align": "center",
      "sizing": "600px",
      "border": true,
      "caption": "Card elements"
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

Use the `paymentRequestButton` element to add a button for Google Pay™ transactions. When you click GPay™, a new window displays for the Google Pay flow. The size of the button is rendered based on the width and height of the `#payment-request-button` element.

All Google Pay assets and buttons must follow the <a href="https://developers.google.com/pay/api/web/guides/brand-guidelines" target="_blank">Google Pay Web Brand Guidelines</a>. The Google Pay payment button has specific size properties. 

- Default width is `90px` (`min-width: 90px;`)
- Default height is `40px` (`min-height: 40px;`)
- The `max-width` and `max-height` values are set by the width and height of the `<div>` container you use for mounting the `paymentRequestButton` (`<div id="payment-request-button"></div>`).
- When creating a new `paymentRequestButton`, the payment `amount` (in cents) is required.

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
      "sizing": "40% ",
      "border": true,
      "caption": "Default button that displays if the customer has a saved payment method"
    }
  ]
}
[/block]


<hr>

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

The Clover Privacy Policy is automatically added to the footer of every iframe using a `<div>` container with the `clover-footer` class.

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
      "sizing": "50% ",
      "border": true,
      "caption": "Secure Payments Powered by Clover - Privacy Policy"
    }
  ]
}
[/block]
