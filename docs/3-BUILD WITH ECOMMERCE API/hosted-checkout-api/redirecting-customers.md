---
title: "Redirect customers"
slug: "redirecting-customers"
excerpt: ""
hidden: false
metadata: 
  description: "The redirectUrls parameter redirects customers to another link (URL) after payment. You can set more than one redirect location or URL."
  image: []
  robots: "index"
createdAt: "Fri Nov 20 2020 17:13:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n   \n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  \n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


When you request a hosted checkout session using the [checkouts](https://docs.clover.com/reference/createcheckout) endpoint, you can include the `redirectUrls` parameter. This parameter redirects customers to another link (URL) after payment. You can set more than one redirect location or URL.  
You can include the following status in the `redirectUrls` object:

- `success`—use this URL when a payment is successfully completed.
- `failure`—use this URL when a payment is attempted but not completed.
- `cancel`—use this URL when the customer leaves the checkout session before payment.

By default, a Clover-hosted confirmation page appears after a successful payment.

> 📘 Note
> 
> If `redirectUrls` parameters are configured on the Merchant Dashboard, then the URLs in the request are used instead of the URLs set in the [Create Checkout](https://docs.clover.com/reference/createcheckout) API.

## Example–Set a redirect URL when payment is successfully completed

**Prerequisites**

- Use secure HTTP(S) URL for `redirectUrls—success, failure, cancel`—as unencrypted (HTTP) URL will not work.
- Include the customer details in the payload.

```javascript
app.route('/redirects', methods = ['GET', 'POST'])
def redirects(): #if request.method == 'POST':
    url = "https://sandbox.dev.clover.com/invoicingcheckoutservice/v1/checkouts"
payload = {
    "customer": {
        "firstName": "ace",
        "lastName": "place",
        "email": "test@clover.com"
    },
    "redirectUrls": {
        "success": "https://www.merchant.com/",
        "failure": "https://www.merchant.com/",
        "cancel": "https://www.merchant.com/",

    },
    "shoppingCart": {
        "lineItems": [{
            "name": "itemA",
            "price": 500,
            "unitQty": 1
        }]
    }
}
headers = {
    "accept": "application/json",
    "X-Clover-Merchant-Id": "6CQXXXXXXXYE1",
    "content-type": "application/json",
    "authorization": "80e0****-****-****-********3f4a"
}

response = requests.request("POST", url, headers = headers, json = payload)
print(response.text)
return render_template("redirect.html")
```
