---
title: "Update multi-lingual support"
slug: "multilingual-support"
excerpt: ""
hidden: false
metadata: 
  description: "Current version of the Clover Adobe Commerce payments extension supports US English, Canadian English, and Canadian French. You can change the default supported location to Canadian French."
  image: []
  robots: "index"
createdAt: "Wed May 04 2022 20:13:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3008; Region pill icon added to topic on 2.27.2023-->\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">United States</div>\n    <br>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    \n    <div class=\"label\">Canada</div>\n      <br>\n</div>\n\n</div>\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Current version of the Clover Adobe Commerce payments extension supports US English, Canadian English, and Canadian French. You can change the default supported location to Canadian French:

1. Log in to Adobe Commerce dashboard.
2. In the Configuration page of your app, click **Stores** > **Settings** > **Configuration**.
3. In the Locale Options section, from the **Locale** drop-down list, select **French (Canada)**.
4. Click **Save Config**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2747849-Config.jpeg",
        "Config.jpeg",
        1510
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


Verify in the merchant eCommerce website:

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
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


4. From the top-right menu, click **Account settings**. My Account page appears.
5. From the **Interface Locale ** drop-down list, select **French (Canada)**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a955464-Locale4.jpg",
        "Locale4.jpg",
        1748
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


The following image displays the Configuration Details page after you change the settings to French (Canada).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/35e034c-Multi-Lingual.png",
        "Multi-Lingual.png",
        1632
      ],
      "sizing": "100",
      "border": true
    }
  ]
}
[/block]


> 📘 Note
> 
> See [Clover iframe integrations](doc:clover-iframe-integrations) for more information on Clover's iframe.
