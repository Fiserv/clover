---
title: "Configure 3D Secure SDK for merchant self-hosted checkout"
slug: "3ds-secure-configure-sdk"
excerpt: ""
hidden: true
createdAt: "Wed Oct 25 2023 17:49:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Aug 06 2024 06:40:41 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

<!--Arpit - please add final procedure hereee-->

3D Secure (3DS) is a protocol that provides an additional security layer for online credit and debit card-not-present (CNP) transactions. Clover uses the <<glossary:EMVCo>> 3DS to authenticate customers and safeguard against CNP fraud.

To get started, see [3DS enablement for Clover merchants](https://docs.clover.com/docs/3ds-for-clover-merchants-overview#3ds-enablement-for-clover-merchants).

# Configure the 3DS SDK to your payment setup

Integrate the 3DS SDK while setting up the payment system [using the Clover-hosted iframe](https://docs.clover.com/docs/using-the-clover-hosted-iframe).  
Once you have configured the 3DS SDK into the payment system, ask your merchant to enable 3DS from the**Merchant Dashboard > Settings > Ecommerce > Fraud Tools > Cardholder authentication and liability protection**.

### Steps

1. To use the Clover 3DS, add the 3DS SDK to your webpage. Use one of the methods to load the script.

   1. Load the script using the script tag and create a global object.  
      **Note: **Merchant Uuid is required.
      1. Add `script` to the webpage `head` block to import the 3DS SDK.
         ```html
         <head>
           <script
             src="https://checkout.clover.com/clover3DS/clover3DS-sdk.js"
             async
           ></script>
         </head>
         ```
      2. Create a global object
         ```javascript
         window._3DSUtil = new Clover3DS({ merchantUuid: {{merchantUUid}} });}))
         document.addEventListener('executePatch', {{methodName}});
         Eg::
         document.addEventListener('executePatch', proceedFinalizeCall);
         ```
   2. Load the script asynchronously using Promise. The script is resolved when the script is loaded.

      ```javascript
      loadScript().then(() => {
          window._3DSUtil = new Clover3DS({ merchantUuid: {{merchantUUid}} });
          document.addEventListener('executePatch', {{methodName}});
      });




      const loadScript = (async = true, type = "text/javascript") => {
          return new Promise((resolve, reject) => {
              try {
                  const newScriptElement = document.createElement("script");
                  newScriptElement.type = type;
                  newScriptElement.async = async;
                  newScriptElement.src = "https://checkout.clover.com/clover3DS/clover3DS-sdk.js";




                  newScriptElement.addEventListener("load", (ev) => {
                      resolve({ status: true });
                  });
                  newScriptElement.addEventListener("error", (ev) => {
                      reject({
                          status: false,
                          message: `Failed to load the script ＄{FILE_URL}`
                      });
                  });




                  document.body.appendChild(newScriptElement);
              } catch (error) {
                  reject(error);
              }
          });
      };

      ```
2. Use the `window._3DSUtil.getBrowserInfo()` object to call the browser information.
   ```javascript
   '{"browser_accept_header":"*/*","browser_javascript_enabled":true,"browser_screen_width":"1792","browser_screen_height":"1120","browser_tz":"420","browser_user_agent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36","browser_color_depth":"24","browser_language":"en-US","browser_java_enabled":false,"browser_http_origin":{{web-page url}}}'
   ```
3. Initiate the 3DS SDK and call `v1/charges` endpoint.  
   **Notes: **

- `threeds` property is mandatory, with all the fields in the threeds object.
- If you are testing in the sandbox environment, replace <https://scl.clover.com/v1/charges> with [scl-sandbox.dev.clover.com/v1/charges](scl-sandbox.dev.clover.com//v1/charges). 

```curl
curl --location 'https://scl.clover.com/v1/charges' --header 'Authorization: Bearer f5f3ef06361d8d5f38165f80fecacfbe' --header 'Content-Type: application/json' --data '{"amount":{{amount}},"source":{{clv_token_generated}},"currency": "USD","threeds":{"source":"CLOVER","browser_info":{browser_ip: {{ip_address}}, ...window._3DSUtil.getBrowserInfo()}}}'
```

**The possible responses are:**

a. **Successful transaction**

```javascript
"threeds": {  
    "validation_result": "AUTHENTICATION_SUCCESSFUL",  
    "liability_protection_status": "PROTECTED"  
}
```

b. **Fingerprinting required i.e. (Method-Notification):** For this response, you need to gather browser fingerprints using JavaScript.

```javascript
"threeds": {  
        "validation_result": "THREEDS_METHOD_FLOW_REQUIRED",  
        "liability_protection_status": "NOT_PROTECTED",  
        "source": "CLOVER",  
        "data": {  
            "method_url": {{acsMethodUrl}},  
            "method_notification_url": {{methodNotificationUrl}},  
            "threeds_server_transaction_id": {{threeDSServerTransID}},  
            "threeds_protocol_version": "2.2.0"  
        }  
}
```

c. **Challenge flow required: **For this response, you need to gather browser fingerprints using JavaScript.

```javascript
"threeds": {  
        "validation_result": "CHALLENGE_FLOW_REQUIRED",  
        "liability_protection_status": "NOT_PROTECTED",  
        "source": "CLOVER",  
        "data": {  
            "acs_url": {{acsUrl}},  
            "acs_transaction_id": {{acsTransID}},  
            "threeds_server_transaction_id": {{threeDSServerTransID}},  
            "threeds_protocol_version": "2.2.0"  
        }  
}
```

d. **Transaction declined**

4. For responses b and c, gather browser fingerprints using JavaScript. The SDK will perform the fingerprinting or challenge notification flow. After the fingerprinting is complete, it'll dispatch an event (`executePatch`) with the updated status under `\_evt.detail.3DSStatus`. Implement the event-listener while initializing the SDK to fetch the updated status under `\_evt.detail.3DSStatus`.
   1. Method Notification Flow
      ```javascript
      	window.\_3DSUtil.perform3DSFingerPrinting({  
          {{\_3DSServerTransId}},  
          {{acsMethodUrl}},  
          {{methodNotificationUrl}}  
      });
      ```
   2. Challenge Notification Flow
      ```javascript
      window.clover3DSUtil.perform3DSChallenge({  
              messageVersion,  
              acsTransID,  
              acsUrl,  
              threeDSServerTransID  
      });
      ```

<br />

4. Finalize the 3DS transaction. This can be added in `executePatch eventListener handler`. Use the [test cards](<>) to test the 3DS functionality.
   ```curl
   curl --location 'https://scl.clover.com/v1/charges/finalize_payment' --header 'Authorization: Bearer f5f3ef06361d8d5f38165f80fecacfbe' --header 'Content-Type: application/json' --data '{"charge_id":{{charge_id obtained from v1/charge call}}, "threeds": { "source": "CLOVER",flow_status : event?.detail?._3DSStatus}'
   ```
   The possible responses for finalized endpoint are:  if executed,  
   a. After method flow: **Success**, **decline** or a **challenge flow**.  
   b. After challenge flow: **Success** or **decline**. 

## Test cards

You can use these test card details to test the 3DS feature in the sandbox environment.

| Card number      | Card type | Amount |
| :--------------- | :-------- | :----- |
| 373953192351004  | AMEX      | 25001  |
| 6011000990139424 | DISCOVER  | 6677   |
| 4012000033330026 | VISA      | 25001  |
| 4001230000000129 | VISA      | 1000   |
| 4811326490014875 | VISA      | 1009   |
| 4043130007524792 | VISA      | 7001   |
