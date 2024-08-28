---
title: "Test your hosted checkout integration (Windows)"
slug: "testing-your-hosted-checkout-integration-windows"
excerpt: ""
hidden: false
metadata: 
  description: "Use the steps in this page to test a checkout session using basic tools, such as PowerShell and a web browser."
  image: []
  robots: "index"
createdAt: "Fri Nov 20 2020 17:19:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


You can test the hosted checkout experience without much code. Use the following steps to test a checkout session using basic tools, such as PowerShell and a web browser.

1. Copy the following PowerShell script:

```powershell
$headers = New-Object "System.Collections.Generic.Dictionary[[String],[String]]"
$headers.Add("X-Clover-Merchant-Id", "{merchantID}")
$headers.Add("Authorization", "Bearer {privateKey}")
$headers.Add("Content-Type", "application/json")

$body = "{
`n  `"customer`" : {
`n    `"email`": `"customer@example.com`",
`n    `"firstName`" : `"Example`",
`n    `"lastName`": `"Customer`",
`n    `"phoneNumber`": `"223-555-0002`"
`n  },
`n  `"shoppingCart`" : {
`n    `"lineItems`": [
`n      {
`n        `"name`": `"Lime`",
`n        `"unitQty`": 3,
`n        `"price`": 100
`n      },
`n      {
`n        `"name`": `"Pear`",
`n        `"unitQty`": 2,
`n        `"price`": 150
`n      }
`n    ]
`n  }
`n }
`n"

$response = Invoke-RestMethod 'https://sandbox.dev.clover.com/invoicingcheckoutservice/v1/checkouts' -Method 'POST' -Headers $headers -Body $body
$response | ConvertTo-Json
```

2. In a text editor, paste the command and then replace the following placeholders:
   - `merchantId`
   - `privateKey`
   - `emailAddress`
3. Copy the edited command.
4. Start a terminal session.
5. Paste the edited cURL command and press **Enter** to run it.  
   A response is returned.
6. Copy the URL value from the `href` field.
7. In a web browser, paste the URL and press **Enter**.
8. On the checkout page, verify the following information is correct:
   - Items and their quantities
   - Customer’s information
9. Enter the following card information:
   - Card Number:`6011 3610 0000 6668`
   - MM/YY: a month and year in the future
   - CVV: a 3-digit number
   - ZIP: a 5-digit number
10. Click **Pay**.  
    The payment is processed and a Payment Received message appears.
11. Verify a receipt is sent to your email address.
