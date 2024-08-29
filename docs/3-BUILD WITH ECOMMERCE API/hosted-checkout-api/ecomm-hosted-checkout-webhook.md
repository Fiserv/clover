---
title: "Configure Ecommerce hosted checkout webhooks"
slug: "ecomm-hosted-checkout-webhook"
excerpt: ""
hidden: false
metadata: 
  title: "Configure Ecommerce hosted checkout Webhooks"
  description: "When generating an API token to use for the hosted checkout feature, merchants can configure a Webhook setting. This page provides the steps to configure Ecommerce hosted checkout Webhooks."
  image: []
  robots: "index"
createdAt: "Wed Dec 22 2021 21:49:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 13 2024 07:14:46 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

## What is a webhook?

Webhooks send an HTTP callback or message to allow one server to communicate with another. You can configure webhook settings on the Clover  Merchant Dashboard. With webhooks configured on a hosted checkout page, your application can receive notifications when merchants who have installed your app perform certain actions. For more information on webhook settings, see the [Webhook site](https://webhook.site/#!/5a88c091-2960-4bcf-9eec-796b80838f6f).

> 📘 NOTE
> 
> You need to create an Ecommerce API token to use the hosted checkout page for making payments. See [Set up an API token](https://docs.clover.com/docs/setting-up-an-api-token).

## Configure webhook on the Merchant Dashboard

1. Log in to the [Clover Merchant Dashboard](https://sandbox.dev.clover.com/dashboard).
2. From the left navigation menu, click **Account & Setup**. The Account and Setup page appears.
3. Scroll down to the Ecommerce section and click **Hosted Checkout**. The Hosted Checkout page appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/01050e3-webhook1.png",
        "",
        "Hosted Checkout"
      ],
      "align": "center",
      "sizing": "80% ",
      "border": true,
      "caption": "Hosted Checkout"
    }
  ]
}
[/block]


4. Set or update the hosted checkout page style, ReCAPTCHA setting, and redirect URLs.
5. In the Webhook section > Webhook URL field, enter a secure HTTPS link (URL).
6. Click **Generate**. The Signing Secret field displays a secret key.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d8570df-webhook_signing_secret.png",
        "",
        "Webhook URL"
      ],
      "align": "center",
      "sizing": "300px",
      "border": true,
      "caption": "Webhook URL"
    }
  ]
}
[/block]


7. Click **Save**.
8. Click **Copy** to copy the key in the Signing Secret field to receive webhook messages after the customer has made a payment in a hosted checkout session. You can use this secret key to validate the Clover signature header in the webhook.  
   **Note: **After a customer completes a payment on the hosted checkout page, a webhook notification is sent to the merchant’s configured webhook URL.  
   Example:

> Created Time  
> Message: Approved for 100 or Decline for 100  
> Status: APPROVED or DECLINED  
> Type: PAYMENT  
> Id: Payment universally unique identifier (UUID)  
> MerchantId: Merchant UUID  
> Data: Checkout Session UUID

## Validate the Clover-signature header in the webhook

To secure webhooks you need to validate the webhook source, destination, and  `payload`. Hash-based Message Authentication Code (HMAC) is used in the signature header verification to authenticate and validate webhooks. An HMAC is calculated using a secret key and a cryptographic hash function like `SHA-2` or `SHA-3`. This HMAC becomes the signature of the webhook; it is then used to authenticate the webhook, and validate its `payload`.

You can include a `Clover-Signature` header field in the webhook message. This allows you to verify the validity of a webhook message. The value for the header includes the `current time`, `payload` and the `webhook` secret key.

Example to validate the`Clover-Signature` header:  
`Clover-Signature: t=1642599079,v1=tf1535bddbf8923d77ca9665eed5fc89b8b5506bbad137cd4ca76aa2a8d2a342`.

1. Append the message's timestamp with a period (`.`) and the raw request `payload`. For example, using the example above—`1642599079.json`—where `json` is the raw request body of the received webhook message.
2. Hash the value from the second string through the  `HmacSHA256` using the webhook secret key. The secret key displays in the Signing Secret field, generated for the [webhook URL](https://docs.clover.com/docs/ecomm-hosted-checkout-webhook#configure-webhook-on-the-merchant-dashboard) for your hosted checkout page.
3. Compare the two strings with the `v1` signature value. If they match, then the validation is successful.
