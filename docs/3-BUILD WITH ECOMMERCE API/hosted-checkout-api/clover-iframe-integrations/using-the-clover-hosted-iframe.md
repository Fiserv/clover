---
title: "Use the Clover-hosted iframe"
slug: "using-the-clover-hosted-iframe"
excerpt: ""
hidden: false
metadata: 
  description: "This tutorial provides instructions for integrating the Clover-hosted iframe into your app and guides you through a simple test transaction."
  image: []
  robots: "index"
createdAt: "Thu Feb 13 2020 10:35:20 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Aug 08 2024 17:50:15 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

The in-line frame (iframe) allows you to insert an HTML page into another HTML-based webpage. With the Clover-hosted iframe integration, your website can communicate with the Clover Ecommerce APIs.

You can combine the Clover-hosted iframe (provided by Clover's `sdk.js`) with an Ecommerce software development kit (SDK) to build a secure payment experience on your website. The Clover-hosted iframe includes fields and elements that you need to get the customer information from the merchant browser to the Clover server.

## Information flow for a charge request

The following diagram displays the information flow and the software components interaction required to complete a [charge request](https://docs.clover.com/docs/create-a-charge). Add an HTML`<form>` to your ecommerce webpage and insert the Clover-hosted elements to collect and process a customer’s card information.  
This information is used to create the card token that the server processes to complete the payment. This charge operation must be a server-to-server call.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b727df5-clover-hosted.png",
        null,
        "Information flow for charge request  \nGreen: Clover software  \nBlue:  your apps software"
      ],
      "align": "center",
      "border": true,
      "caption": "Information flow for charge request  \nGreen: Clover software  \nBlue:  your apps software"
    }
  ]
}
[/block]


## Browser support

Apple Safari, Google Chrome, Mozilla Firefox, and Microsoft Edge browsers support the Clover iframe.

> ❗️ Important
> 
> **Secure your site**: Developers using the Clover-hosted iframe integration are advised to check their code and remove any reference to `cdn.polyfill.io`. For example:
> 
> [block:html]{"html":"<div class=\"cm-s-neo\" data-testid=\"SyntaxHighlighter\" style=\"padding: 1em;border-left:0.5em solid #dfe2e5\">\n  <p class=\"cm-s-neo\"><span class=\"cm-tag\">&lt;head&gt;</p>\n  <p class=\"cm-s-neo\"><span class=\"cm-tag\">...</span></p>\n  <p class=\"cm-s-neo\"><span class=\"action\">delete this→</span>\n    <span class=\"cm-tag\">&lt;script src=<span class=\"cm-string\">\n      \"https://cdn.polyfill.io/v3/polyfill.min.js\"</span>&gt; &lt;/script&gt;</span>\n      <span class=\"action\">←</span>\n  </p>\n  <p class=\"cm-s-neo\"><span class=\"cm-tag\">&lt;script src=<span class=\"cm-string\">\n    \"https://checkout.sandbox.dev.clover.com/sdk.js\"</span>&gt; &lt;/script&gt;</span>\n    </p>\n  <p class=\"cm-s-neo\"><span class=\"cm-tag\">&lt;/head&gt;</span></p>\n</p>\n</div>\n<style> \n .cm-s-neo, .cm-tag, .cm-string {font-size: 9px;background-color: #f9f9f9;margin-bottom:2px!important;\n  font-family: SFMono-Regular, Consolas, \"Liberation Mono\", Menlo, Courier, monospace;}\n .cm-s-neo .cm-node, .cm-s-neo .cm-tag, .cm-s-neo .p \n  {font-size: 9px ;line-height:9px; margin-bottom:2px!important; color:#5d5d5d;\n    font-family: SFMono-Regular, Consolas, \"Liberation Mono\", Menlo, Courier, monospace;}\n .action \n  {font-size: small; font-weight:600;line-height:9px;color: var(--red);}\n .callout-heading h2, .callout-heading p{\n    font-size: 1.25em;\n    font-weight: var(--markdown-title-weight, 600);\n    line-height: 20px;\n}\n</style>\n"}[/block]

> 📘 NOTE
> 
> For additional information about the security concern with using polyfill script, see the related [announcement](https://docs.clover.com/docs/alert-remove-iframe-references-to-polyfillio).

[block:html]
{
  "html": "<!--REMOVED reference to polyfill:\nIt does not run on Microsoft Internet Explorer 11 browser by default, \nbut you can use polyfills to make the iframe functional in the browser.\n\nCodeblock: HTML - Adding polyfills for EI11\n<head>\n  ...\n  <script src=\"https://cdn.polyfill.io/v3/polyfill.min.js\"></script>\n  <script src=\"https://checkout.sandbox.dev.clover.com/sdk.js\"></script>\n</head>\n-->"
}
[/block]


## Add the Clover SDK to your webpage

1. To use the Clover iframe features, you need to import the Clover SDK to your webpage.  
   Add a `<script>` block to the `<head>` block of your webpage.
2. In your HTML form, add `<script>` to import the Clover SDK and use the [Clover iframe features](https://docs.clover.com/docs/clover-iframe-features). Use the sandbox or production `sdk.js `file to define the source (src).  
   Sandbox: `<https://checkout.sandbox.dev.clover.com/sdk.js>`  
   Production: `<https://checkout.clover.com/sdk.js>`

```html
<head>
  ...
  <script src="https://checkout.sandbox.dev.clover.com/sdk.js"></script>
</head>
```

## Configure the SDK

To make payment requests on a merchant's behalf, set up the Clover SDK to use the merchant's public key retrieved from the [PAKMS endpoint](https://docs.clover.com/reference/getapikey).

1. Create a `clover` constant (`const`) and pass the merchant's key as the parameter of a new `Clover` object.
2. Create another constant  (`const`) for `clover.elements()`. This constant creates card tokens based on information entered in the iframe. Each entity in the iframe is an element.

```javascript
merchantId to const clover.
const clover = new Clover('12a3b456789c12345d67891234e56f78', {
    merchantId: 'xxxxxxxxxxxxx'
});
const elements = clover.elements();
```

**Note**: <<glossary:merchantId>> is required.

3. If you want to configure a language, add a `locale` to `const clover`. Clover supports:

- English USA (`en-US`) by default
- English Canadian (`en-CA`)
- French Canadian (`fr-CA`). For example, the following appended command supports French Canadian:

```javascript
const clover = new Clover('12a3b456789c12345d67891234e56f78', {
    locale: 'fr-CA'
});
const elements = clover.elements();
```

4. To support the reCAPTCHA verification service, street address input field, or other optional features, add `merchantId` to the iframe configuration.

```javascript
merchantId to const clover.
const clover = new Clover('12a3b456789c12345d67891234e56f78', {
    merchantId: 'xxxxxxxxxxxxx'
});
const elements = clover.elements();
```

> 🚧 IMPORTANT
> 
> Apps for a single merchant can hardcode the public key to initialize the iframe SDK.
> 
> If your app uses a model where a customer may expect to use one card token between multiple merchants, send an email to [Clover developers relations](mailto:developer-relations@devrel.clover.com) team.

## Set up the payment form

You can create an HTML `<form>` where customers enter their credit card information. To set up your payment form:

1. Add a `<form>` to contain card data fields on your webpage.
2. Set the `id` attribute and make a note of this value. Example: `payment-form`.

```html
<body>

  <form action="/charge" method="post" id="payment-form">
    <!-- this form contains the card data fields -->
  </form>
 
</body>
```

3. In the `<form>`, create an `<input>` field to enter the amount of the charge.

```html
<form action="/charge" method="post" id="payment-form">
	  
  <div class="form-row top-row">
    <div id="amount" class="field card-number">
      <input name="amount" placeholder="Amount">
    </div>
  </div>
  
</form>
```

4. Add `<div>` containers to enable customers to enter their card details. For each card data field, add a `<div>` to display error messages (`class="input-errors"`).

```html
<form action="/charge" method="post" id="payment-form">
  ...
  
  <div class="form-row top-row">
    <div id="amount" class="field card-number">
      <input name="amount" placeholder="Amount">
    </div>
  </div>

  <div class="form-row top-row">
    <div id="card-number" class="field card-number"></div>
    <div class="input-errors" id="card-number-errors" role="alert"></div>
  </div>

  <div class="form-row">
    <div id="card-date" class="field third-width"></div>
    <div class="input-errors" id="card-date-errors" role="alert"></div>
  </div>
  
  <div class="form-row">
    <div id="card-cvv" class="field third-width"></div>
    <div class="input-errors" id="card-cvv-errors" role="alert"></div>
  </div>
    
  <div class="form-row">
    <div id="card-postal-code" class="field third-width"></div>
    <div class="input-errors" id="card-postal-code-errors" role="alert"></div>
  </div>
    
  <div id="card-response" role="alert"></div>
    
  ...
</form>
```

5. Add a `<button>` for the users to finalize their payment.

```html
<form action="/charge" method="post" id="payment-form">
  ...
  
  <div class="button-container">
    <button>Submit Payment</button>
  </div>
  
</form>
```

After the payment `<form>` is set up, you can use JavaScript components to make it interactive. See [Create an interactive payment](https://docs.clover.com/docs/using-the-clover-hosted-iframe#create-an-interactive-payment-form).

## Create an interactive payment <form>

To make the payment `<form>`  interactive, add JavaScript components provided with the iframe.

1. Complete the steps to [set up the payment form](https://docs.clover.com/docs/using-the-clover-hosted-iframe#set-up-the-payment-form).
2. Use the `<form>` element ID from the [set up the payment form](https://docs.clover.com/docs/using-the-clover-hosted-iframe#set-up-the-payment-form) section to create a constant to access the payment form.

```javascript
const form = document.getElementById('payment-form');
```

3. Create instances of the card elements and mount them to the `<div>` containers. When creating containers, you can add CSS styling as the second parameter to match your website branding. See [Customize iframe elements with CSS](https://docs.clover.com/docs/customizing-iframe-elements-with-css).

```javascript
const cardNumber = elements.create('CARD_NUMBER', styles);
const cardDate = elements.create('CARD_DATE', styles);
const cardCvv = elements.create('CARD_CVV', styles);
const cardPostalCode = elements.create('CARD_POSTAL_CODE', styles);
  
cardNumber.mount('#card-number');
cardDate.mount('#card-date');
cardCvv.mount('#card-cvv');
cardPostalCode.mount('#card-postal-code');
```

4. Add event listeners (`addEventListener`) for displaying any error messages to the user.

The SDK's real-time validation of the card data fields ensures that the customer entries match the expected format. With the change and blur event listeners, you can handle real-time validation in the iframe.

```javascript
const cardResponse = document.getElementById('card-response');
const displayCardNumberError = document.getElementById('card-number-errors');
const displayCardDateError = document.getElementById('card-date-errors');
const displayCardCvvError = document.getElementById('card-cvv-errors');
const displayCardPostalCodeError = document.getElementById('card-postal-code-errors');

  // Handle real-time validation errors from the card element
  cardNumber.addEventListener('change', function(event) {
    console.log(`cardNumber changed ${JSON.stringify(event)}`);
  });

  cardNumber.addEventListener('blur', function(event) {
    console.log(`cardNumber blur ${JSON.stringify(event)}`);
  });

  cardDate.addEventListener('change', function(event) {
    console.log(`cardDate changed ${JSON.stringify(event)}`);
  });

  cardDate.addEventListener('blur', function(event) {
    console.log(`cardDate blur ${JSON.stringify(event)}`);
  });

  cardCvv.addEventListener('change', function(event) {
    console.log(`cardCvv changed ${JSON.stringify(event)}`);
  });

  cardCvv.addEventListener('blur', function(event) {
    console.log(`cardCvv blur ${JSON.stringify(event)}`);
  });

  cardPostalCode.addEventListener('change', function(event) {
    console.log(`cardPostalCode changed ${JSON.stringify(event)}`);
  });

  cardPostalCode.addEventListener('blur', function(event) {
    console.log(`cardPostalCode blur ${JSON.stringify(event)}`);
  });
```
```json Sample iframe validation response
{
  "CARD_NUMBER": {
    "error":"Card number is invalid.",
    "touched":true // whether there was any interaction with the field
  },
  "CARD_DATE": {
    "error":"Card expiry is invalid.",
    "touched":true
  },
  "CARD_CVV": {
    "touched":true
  },
  "CARD_POSTAL_CODE": {
    "touched":false
  }
}
```

5. Add an event listener (`addEventListener`) to the submit event. This listener takes the validated card data from the payment form and calls the `clover.createToken()` method. A token is generated.

```javascript
// Listen for form submission
form.addEventListener('submit', function(event) {
  event.preventDefault();
  // Use the iframe's tokenization method with the user-entered card details
  clover.createToken()
    .then(function(result) {
    if (result.errors) {
      Object.values(result.errors).forEach(function (value) {
        displayError.textContent = value;
      });
    } else {
      cloverTokenHandler(result.token);
    }
  });
});
```

```json Sample tokenization result
{
	"token": "clv_1TST39I92..."
}
```

6. Add the generated token to the server application to charge the tokenized card.

```javascript
function cloverTokenHandler(token) {
  // Insert the token ID into the form so it gets submitted to the server
  var form = document.getElementById('payment-form');
  var hiddenInput = document.createElement('input');
  hiddenInput.setAttribute('type', 'hidden');
  hiddenInput.setAttribute('name', 'cloverToken');
  hiddenInput.setAttribute('value', token);
  form.appendChild(hiddenInput);
  form.submit();
}
```

## Create a charge

Once you create an interactive payment form and generate a card token (see [Generate a card token](https://docs.clover.com/docs/ecommerce-generating-a-card-token)) you can now create a charge. For detailed information, see [Create a charge](https://docs.clover.com/docs/create-a-charge).

**Prerequisites**

- Create a charge request must be a server-to-server call as shown in the [information flow for a charge request](https://docs.clover.com/docs/using-the-clover-hosted-iframe#information-flow-for-a-charge-request).
- Use an `idempotency` key, which is a required value generated by your app for Clover, to safely retry the `v1/charges` request without accidental double charges. See [Use idempotency keys](https://docs.clover.com/docs/ecommerce-accepting-payments#use-idempotency-keys) for more information.

**Steps**

1. On the payment form, enter the customer's card details to pay for an order.
2. Send the `amount` and the token (as the value of `source`) to the `/v1/charges` endpoint to complete the transaction.
3. Set the `authorization: Bearer` as your OAuth-generated `auth_token`. The charge is  
   processed for the specified amount using the token.

```curl
curl --request POST \
  --url 'https://scl-sandbox.dev.clover.com/v1/charges' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer {access_token}' \
  --header 'idempotency-key {uuid4_key}' \
  --header 'content-type: application/json' \
  --header 'x-forwarded-for: {client_ip}' \
  --data '{"amount":4500,"currency":"usd","source":"clv_1ABCD7234efghDIJKlMNOp5qrS"}'
```

<!--

 

````
Create a `charges.js` file that will route the transaction data to the Clover server using the Node SDK. Once your routing is set up and add the required `action` and `method` attributes to your `<form>`.\`\`\`javascript  
```//charges routevar express = require('express');  
var router = express.Router();  
const cloverInst = require('clover-ecomm-node-sdk')('apiToken');router.post('/', async (req, res) => {  
const amount = req.body.amount;  
const cloverToken = req.body.cloverToken;  try {  
const chargeResponse = await cloverInst.charges.create({  
  source: cloverToken,  
  amount: amount,  
  currency: 'usd',  
  capture: 'true',  
})    res.json(chargeResponse);  
} catch(err) {  
res.json(err);  
}})module.exports = router;\`\`\`\`\`\`\`html<form action="/charges" method="post" id="payment-form">  
...</form>
````

\-->

# Watch video: Use Clover-hosted iframe with Ecommerce APIs

[block:parameters]
{
  "data": {
    "h-0": "Let’s learn",
    "0-0": "In this video, learn:  \n  \n- How to combine the Clover-hosted iframe with the Clover Ecommerce SDK to create a secure payment experience?  \n- How to create a payment form to generate a credit card token?  \n- How to pass the credit card token to `v1/charges` endpoint?  \n- How to make an API call through Postman or use a function with the credit card token as a parameter.?"
  },
  "cols": 1,
  "rows": 1,
  "align": [
    "left"
  ]
}
[/block]


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2F256rQaR0cPQ%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D256rQaR0cPQ&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2F256rQaR0cPQ%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=256rQaR0cPQ",
  "title": "Clover Hosted iFrame with Clover Ecommerce APIs",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/256rQaR0cPQ/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=256rQaR0cPQ",
  "typeOfEmbed": "youtube"
}
[/block]
