---
title: "PAYMENT TOKENS"
slug: "tokens"
excerpt: "Encrypt a customer card, gift card, or ACH to use as a source token."
hidden: false
createdAt: "Fri Nov 25 2022 13:54:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Aug 05 2024 22:17:29 GMT+0000 (Coordinated Universal Time)"
---
Apps using <span style="text-decoration-line: line-through; color:red">an iframe or </span> an API integration receive and send source tokens that represent encrypted customer card data. During initial setup, most developers create a credit card token. ACH and gift card tokens are also available. Choose the token that makes sense for your implementation.

[block:html]
{
  "html": "<ul>\n    <li><a target=\"_blank\" href=\"/v3/reference/create-card-token\">\n        <span>Create a credit card token</span>\n        <span class=\"APIMethod APIMethod_fixedWidth APIMethod_post Sidebar-methodfUM3m6FEWm6w\"\n                data-testid=\"http-method\">post</span></a>\n                <br>Create an encrypted source token for a customer credit card.</li>\n  <li><a target=\"_blank\" href=\"/v3/reference/create-ach-token\">\n        <span>Create an ACH token</span>\n        <span class=\"APIMethod APIMethod_fixedWidth APIMethod_post Sidebar-methodfUM3m6FEWm6w\"\n                data-testid=\"http-method\">post</span></a>\n                <br>Create an encrypted source token for an automated clearinghouse (ACH) electronic payment.</li>\n    <li><a target=\"_blank\" href=\"/v3/reference/create-giftcard-token\">\n        <span>Create a gift card token</span>\n        <span class=\"APIMethod APIMethod_fixedWidth APIMethod_post Sidebar-methodfUM3m6FEWm6w\"\n                data-testid=\"http-method\">post</span></a>\n            Create an encrypted source token\n            <br>Create an encrypted source token for a gift card.</li>\n</ul>"
}
[/block]


<br>

> 📘 Note
> 
> If you are implementing an iframe setup, you do not need to use card tokens. See [Clover iframe integrations](doc:clover-iframe-integrations).
