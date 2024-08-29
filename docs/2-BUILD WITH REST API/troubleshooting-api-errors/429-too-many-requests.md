---
title: "429 Too Many Requests"
slug: "429-too-many-requests"
excerpt: ""
hidden: false
metadata: 
  description: "A 429 error is returned when your app has made too many requests and exceeded the server's rate limit."
  image: 
    - "https://files.readme.io/b640396-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Mon Apr 08 2019 22:14:22 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n     <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


# Respect rate limits

If you are making API requests successively and your requests exceed the rate limits, a `429 Too Many Requests` error is returned. See [API Usage & Rate Limits](doc:api-usage-rate-limits) for complete information about rate limiting.

The following best practices may help you avoid 429 errors:

- Avoid constant polling by using webhooks to trigger updates
- Cache your own data when storing specialized values or if you need to store very large data sets.
- Use the `modifiedTime` query parameter to retrieve only updated data
- If requesting data for multiple merchants, stagger your requests to avoid bursts of high traffic volume.
- If backfilling data, make your requests during non-peak business hours.
