---
title: "Payments with Developer Pay API"
slug: "developer-pay-api"
excerpt: ""
hidden: false
metadata: 
  description: "Deprecated. Use Clover Ecommerce API for card-not-present (CNP) transactions. The Developer Pay API documentation is provided for reference purposes only."
  image: 
    - "https://files.readme.io/ce6ff3d-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Thu Aug 08 2019 16:41:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 09 2024 09:59:14 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


> ❗️ IMPORTANT
> 
> The Developer Pay API is superseded by the Ecommerce API. Developer Pay apps will no longer be available on the App Market starting **October 27, 2021**. New Clover apps providing card-not-present payments should use the Ecommerce API instead of Developer Pay.
> 
> If you want to migrate an existing Developer Pay app, see [Migrating from Developer Pay to Ecommerce](doc:migrating-from-developer-pay-to-ecommerce).

[block:html]
{
  "html": "<div>\n<section class=\"header\">\n   <p style=\"background-color: #f3f8f3;\nborder-left: 3px solid #280; padding: 1em;\">\n  <b>IMPORTANT NOTICE to Clover Developers</b><br>If your published app asks for the <b>process credit card permission</b>, we're trying to contact you about your app's move to the Ecommerce API. <br><br>If you haven't received an email from us, please email <a href=\"mailto:appmarketbusiness@clover.com?subject=Moving to Ecommerce API\">App Market Business</a> for more information.</p>\n</div>"
}
[/block]


With the Developer Pay API (US and Canada), you can build simple payment solutions using the Clover REST API.

The Developer Pay API consists of two endpoints:

- `GET /v2/merchant/{mId}/pay/key`
- `POST /v2/merchant/{mId}/pay`

# Limitations of Developer Pay API

Developer Pay supports basic sale transactions; many payment functions available on Clover hardware and in other Clover SDKs are not available with this API. 

The following functions are not supported:

- Card vaulting (tokenization) without processing a payment
- Authorizations with tip adjustment
- Pre-authorizations
- Refunds
- Voids

# Getting information for the Pay endpoint

`GET /v2/merchant/{mId}/pay/key`

This endpoint returns the `key` and `prefix` you'll need to construct a request body for the `/pay` endpoint. Prepend the prefix value to the credit card number, and then use RSA/OAEP/SHA1 encryption on the resulting string using the provided modulus and exponent.

**Permissions required**: Read payments

**Parameters**: No URL parameters

**Request**: No request data needed

**Response:** 

```json Response from /pay/key
{
  "pem" : string
  "prefix" : string
  "modulus" : string //base 10
  "exponent" : string
  "id" : string
}
```

# Authorizing and capturing a payment

`POST /v2/merchant/{mId}/pay`

This endpoint authorizes and captures a credit card per the merchant's configuration. An `orderId` for an existing order from the Clover API must be included in the payload sent to this endpoint. If this is the first time you're using the card with this specific merchant, you must encrypt the card data with the results from the `GET /v2/merchant/{mId}/pay/key` endpoint. After you've made a payment with a card, you'll get a token that can be used for subsequent transactions in place of the `cardEncrypted`, `cvv`, `expMonth`, `expYear`, and `zip` parameters.

> 📘 NOTE
> 
> In order to use the Developer Pay API to process credit cards, you need an OAuth-generated API token. Merchant-generated API tokens are not supported.

**Permissions required**: Write payments, Online payments

**Parameters**: No URL parameters

**Request**

```json Example Request
{
  "orderId": "HCFFREA222N02", 
  "taxAmount": 9, 
  "zip": "94041", 
  "expMonth": 1, 
  "cvv": "111", 
  "amount": 100, 
  "currency": "usd", 
  "last4": "1111", 
  "expYear": 2015, 
  "first6": "411111", 
  "cardEncrypted": "X8UeKej+AEG1h0wD9Xw=="
}
```

**Response**

Returns an object that includes result statuses and the ID for the payment object. If the merchant is set up for card tokenization, the response will include a token you can use for subsequent transactions for this particular card and merchant.

```json Example Response
{
  "authCode" : string
  "failureMessage" : string
  "token" : string
  "result" : (APPROVED|DECLINED)
  "avsResult" : (SUCCESS|ZIP_CODE_MATCH|ZIP_CODE_MATCH_ADDRESS_NOT_CHECKED|
                 ADDRESS_MATCH|ADDRESS_MATCH_ZIP_NOT_CHECKED|NEITHER_MATCH|
                 SERVICE_FAILURE|SERVICE_UNAVAILABLE|NOT_CHECKED|
                 ZIP_CODE_NOT_MATCHED_ADDRESS_NOT_CHECKED|
                 ADDRESS_NOT_MATCHED_ZIP_CODE_NOT_CHECKED)
  "paymentId" : string
  "cvvResult" : (SUCCESS|FAILURE|NOT_PROCESSED|NOT_PRESENT)
}
```

# Payment flow

![](https://files.readme.io/e3c3d30-Developer_Pay_API.png "Developer Pay API.png")

1. To get the encryption information needed for the `/pay` endpoint, send a GET request to `/v2/merchant/{mId}/pay/key`.
2. Encrypt the card information:   

- Prepend the `prefix` value to the card number.
- Generate an RSA public key using the `modulus` and `exponent` values.
- Using the public key, encrypt the combined prefix and card number from step one.
- Base64 encode the resulting encrypted data into a string to be sent in the `cardEncrypted` field. 

> 📘 NOTE
> 
> The modulus returned by Clover is in base 10. Various libraries expect moduli in different bases.

3. To pay for the order, send a POST request to `/v2/merchant/{mId}/pay`. Pass the encrypted card data and order information in the request.

When the order is paid, the order and payment data are automatically synchronized between the Clover server and the merchant's Clover devices.

**Example code**

The following encryption example code is from the [Java Example App](https://drive.google.com/file/d/1QmQGpLQn-5NiIbjYa2G_qVjeLD-JftfI/view?usp=sharing).

```java
public static PublicKey getPublicKey(final BigInteger modulus, final BigInteger exponent) {
    try {
      final KeyFactory factory = KeyFactory.getInstance("RSA");
      final PublicKey publicKey = factory.generatePublic(new RSAPublicKeySpec(modulus, exponent));
      return publicKey;
    } catch (GeneralSecurityException e) {
      throw new BaseException(e);
    }
}
public static String encryptPAN(final String prefix, final String pan, PublicKey publicKey) {
   byte[] input = String.format("%s%s", prefix, pan).getBytes();
   try {
     Cipher cipher = Cipher.getInstance("RSA/None/OAEPWithSHA1AndMGF1Padding", "BC");
     cipher.init(Cipher.ENCRYPT_MODE, publicKey, RANDOM);
     byte[] cipherText = cipher.doFinal(input);
     return DatatypeConverter.printBase64Binary(cipherText);
   } catch (GeneralSecurityException ignore) {
     return null;
   }
 }
```

> 📘 NOTE
> 
> Customer transactions appear with URLs in their credit card statements. We recommend that you limit your app's site URL to thirteen characters. Any additional characters will not appear in statements.
> 
> To provide a consistent customer experience while also keeping the site URL short, you can use a URL shortening service.

# Payment flow using a vaulted card

Once you complete the steps in the payment flow, you will have a token you can use to process additional transactions if the merchant has been configured to accept vaulted cards. To use this token, build a request in the following format.

```json Request using vaulted card
{
    "orderId": "{{orderId}}", //the Clover order 
    "currency": "usd",
    "amount": 100,
    "tipAmount": 0,
    "taxAmount": 0,
    "first6": "601136",
    "last4": "6668",
    "vaultedCard": {
      "token": "7297162975886668",
      "first6": "601136",
      "last4": "6668",
      "expirationDate": 1219, //expiration in mmdd format
    }
}
```

The `vaultedCard` object contains the token returned in the `vaultedCard` for the initial payment request. Pay attention to the following when making a payment request with a token:

- The `last4` and `first6` values need to be in **both** the `vaultedCard` and the main request body
- The `expMonth` and `expYear` from the first request need to be combined as a single string as the value of `expirationDate`

Submit the request to the same `/v2/merchant/{mId}/pay` endpoint as the original request.
