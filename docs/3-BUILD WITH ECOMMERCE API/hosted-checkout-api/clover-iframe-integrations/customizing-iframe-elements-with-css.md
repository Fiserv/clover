---
title: "Customize iframe elements with CSS"
slug: "customizing-iframe-elements-with-css"
excerpt: ""
hidden: false
metadata: 
  description: "Learn how to customize Clover iframe elements to match your website branding."
  image: []
  robots: "index"
createdAt: "Thu Feb 13 2020 10:33:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


The Clover iframe lets you customize the payment and checkout page to match your website branding. You can use an object containing Cascading Style Sheets (CSS) to define the style of the iframe and the elements inside it.

## Define iframe elements

When creating an iframe, use your custom JavaScript style object to:

- Define the iframe style. The iframe always inherits 100% of the width and height of its container element. Use the CSS applied to the container to change the iframe dimensions.
- Define the styles inside the iframe, such as the border and custom font of card and page elements:
  - `cardNumber`
  - `cardHolderName`
  - `cardDate`
  - `cardCvv`
  - `cardPostalCod`
  - `cardStreetAddress`
  - `paymentRequestButton`

For more information on card and page elements, see [Clover iframe features](https://docs.clover.com/docs/clover-iframe-features).

**Code sample**

```javascript
// const clover = new Clover('7e525404872b8186b82b5057cfacebff');
const clover = new Clover('080391318a9041e4d122082d369b64c7', {
    merchantId: 'M1V5CF1WV0FSJ'
  });
const elements = clover.elements();
const styles = {
  body: {
    fontFamily: 'Roboto, Open Sans, sans-serif',
    fontSize: '16px',
  },
  input: {
    fontSize: '20px'
  }
};
const cardNumber = elements.create('CARD_NUMBER', styles);
const cardName = elements.create('CARD_NAME', styles)
const cardDate = elements.create('CARD_DATE', styles);
const cardCvv = elements.create('CARD_CVV', styles);
const cardPostalCode = elements.create('CARD_POSTAL_CODE', styles);
const cardStreetAddress = elements.create('CARD_STREET_ADDRESS', styles);
cardNumber.mount('#card-number');
cardName.mount('#card-name');
cardDate.mount('#card-date');
cardCvv.mount('#card-cvv');
cardPostalCode.mount('#card-postal-code');
cardStreetAddress.mount('#card-street-address');


// const paymentRequest = clover.paymentRequest(paymentReqData);
const paymentRequestButton = elements.create('PAYMENT_REQUEST_BUTTON', {
paymentReqData
});
paymentRequestButton.mount('#payment-request-button');
paymentRequestButton.addEventListener('paymentMethod', function(ev) {
alert(JSON.stringify(ev));
})
paymentRequestButton.addEventListener('paymentMethodStart', function(ev) {
console.log(“Gpay in progress”);
  })
//   });

```

## Design the form submission and GPay button

- **Form submission button**—If you are adding a form submission button, use your website CSS container element to define the style and dimension of the button. This lets you create a button that matches your website style standards.
- **GPay button**—If you are adding Google Pay™ option in your payment form, you must create a `#paymentRequestButton`. container in your website CSS to define the size and width of the button.

See [Clover iframe features](https://docs.clover.com/docs/clover-iframe-features#7-paymentrequestbutton).

**Code sample**

In this example, the form submission button—Submit Payment—is `.button-container`, and the GPay button container is `#paymentRequestButton`. All Google Pay assets and buttons must follow the [Google Pay Web Brand Guidelines](https://developers.google.com/pay/api/web/guides/brand-guidelines).

```css
.container .button-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.container .button-container button {
  background-color: #xxxxxx;
  border:
  border-radius: xx;
  color: white;
  font-size: xx;
  display: xxxx;
  height: xx;
  width: xx;
}

#paymentRequestButton.  {
  width: 85%;
  height: 40px;
  margin: 0 auto;
}

@media (min-width: 200px) {
  body {
    width: auto;
  }
}

@media (min-width: 600px) {
  body {
    width: 600px
  }
}

.hr {
  width: 100%; 
  height: 10px; 
  border-bottom: 1px solid black; 
  text-align: center;
  margin: 20px 0;
}

.hr span {
  font-size: 10px; 
  background-color: #FFF; 
  padding: 0 10px;
}

.clover-privacy-link {
  font-family: Roboto, "Open Sans", sans-serif;
}

section {
  flex-wrap: wrap;
  width: 100%;
  justify-content: space-evenly;
```
