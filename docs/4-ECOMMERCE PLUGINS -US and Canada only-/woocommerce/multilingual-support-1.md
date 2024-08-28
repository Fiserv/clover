---
title: "Update multi-lingual support"
slug: "multilingual-support-1"
excerpt: ""
hidden: false
metadata: 
  description: "Current version of the Clover Payments plugin for WooCommerce supports English and Canadian French. You can change the default supported location to Canadian French."
  image: []
  robots: "index"
createdAt: "Thu May 12 2022 20:13:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


The current version of the Clover Payments plugin for WooCommerce supports English and Canadian French. To update the supported location to Canadian French:

1. Log in to the WordPress Dashboard.
2. From the left navigation menu, click **Settings** > **General Settings.**
3. From the Site Language drop-down list, select "Francais du Canada."

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2543ae8-UpdateLang.png",
        "UpdateLang.png",
        2602
      ],
      "align": "center",
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


Verify in the merchant eCommerce website

- Information on the merchant eCommerce website displays in Canadian French.
- All custom error messages implemented by the plugin display in Canadian French, for example:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0887459-Locale2.jpg",
        "Locale2.jpg",
        938
      ],
      "align": "center",
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


Hover over any ellipses icon to view the error details in a pop-up message.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0611e8e-Screen_Shot_2022-05-04_at_1.28.41_PM.png",
        "Screen Shot 2022-05-04 at 1.28.41 PM.png",
        1070
      ],
      "align": "center",
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


> 📘 Note
> 
> See [Clover iframe integrations](doc:clover-iframe-integrations) for more information on Clover's iframe.
