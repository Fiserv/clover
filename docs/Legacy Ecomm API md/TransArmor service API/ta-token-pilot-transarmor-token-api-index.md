---
title: "(TA token Pilot) TransArmor token API Index"
slug: "ta-token-pilot-transarmor-token-api-index"
excerpt: ""
hidden: true
metadata: 
  description: "Display transarmor APIs index used in Clover e-commerce network."
  image: []
  robots: "index"
createdAt: "Wed Aug 07 2024 10:01:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Aug 14 2024 10:02:58 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--\nDS-6871\n-->"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

[block:html]
{
  "html": "<!--Add a top nav throughout the pilot doc content (v2.2: grayscale, no overlap)-->\n<div><!--div set-->\n <div class=\"top-container\">\n    <div class=\"topnav\">\n      <a href=\"https://docs.clover.com/docs/use-transarmor-token\">TransArmor token overview</a>\n      <a href=\"https://docs.clover.com/docs/ta-token-pilot-create-a-transarmor-token\">Create a Transarmor token</a>\n      <a href=\"https://docs.clover.com/docs/ta-pilot-use-existing-transarmor-tokens\">Use existing Transarmor tokens</a>\n      <a href=\"https://docs.clover.com/reference/ta-token-pilot-transarmor-token-api-index\">TransArmor token API Index</a>\n    </div><!--end topnav-->\n  </div><!--end top-container-->\n</div>\n\n<!--css-->\n<style>\n/* Add a background color to the top navigation */\n.topnav {\n  font-family: 'Graphik-Regular', sans-serif;\n  background-color: #5D5D5D;\n  overflow: hidden;\n}\n\n/* Style the links inside the navigation bar */\n.topnav a {\n  font-family: 'Graphik-Regular', sans-serif;\n  float: left;\n  color: #f2f2f2;\n  text-align: center;\n  padding: 10px 12px;\n  text-decoration: none;\n  font-size: 12px;\n}\n\n/* Change the color of links on hover */\n.topnav a:hover {\n  background-color: #D8D8D8;\n  color: black;\n}\n\n/* Add a color to the active/current link */\n.topnav a.active {\n  background-color: #5D5D5D;\n  color: white;\n}\n</style>"
}
[/block]


# Use this API Index with the TransArmor API Pilot

This section defines the APIs modified to introduce the transarmor token (TA) update.

- **During the pilot** -  Use these APIs as a reference to create a TA token and use existing TA tokens.
- **After the pilot and launch are complete** - You will be required to use these APIs as they will replace the legacy functionality that only supports single-pay tokens.

## TA token Pilot API endpoints

[block:html]
{
  "html": "<!--BEGIN list-->\n    <!--Inventory-->\n        <span>\n        <ul>\n          <li><a href=\"/reference/create-card-ta-token\"> Create a card token<span class=\"APIMethod APIMethod_fixedWidth APIMethod_post PageNavItemEndpointBadgeThaLyYpVXh2Q PageNavItem-badge2W6A2bDejhcE\" data-testid=\"http-method\" element-id=\"1368\">post</span></a></li>\n          <li><a href=\"/reference/createcharge-1\"> Create a charge <span class=\"APIMethod APIMethod_fixedWidth APIMethod_post PageNavItemEndpointBadgeThaLyYpVXh2Q PageNavItem-badge2W6A2bDejhcE\" data-testid=\"http-method\" element-id=\"1368\">post</span></a></li>\n          <li><a href=\"/reference/postordersidpay-1\"> Pay for an order <span class=\"APIMethod APIMethod_fixedWidth APIMethod_post PageNavItemEndpointBadgeThaLyYpVXh2Q PageNavItem-badge2W6A2bDejhcE\" data-testid=\"http-method\" element-id=\"1368\">post</span></a></li>\n        </ul>\n        </span>\n<!--END list-->\n<hr />"
}
[/block]


[block:html]
{
  "html": "<!--NOTES for writers-->\n<!--TEMPLATE for easy dropdown -->\n<!--\n<details>\n    <summary>Click to toggle</summary>\n    <span>Oh, hello</span>\n</details>\n-->\n  <!--<p>This section is copied from the left-nav of the authoring interface of v3. </p>\n  <p>I used the v3 list because the list from the 2024-Q1 version has diff names for the endpoints <br>\n  due to all the duplicate imports. I wanted the exact/correct slugs from v3—but bc I could not <br>\n  make it public, I used the list from the authoring version (via inspect source) instead. <br>\n  Then, I cleaned up the HTML: </p>\n   <ul>\n    <li>stripped the styles and then returned styles for the methods. <br>\n\t\t<li>replaced all dash-readme URLs (\"/project/clover-platform/v3/refs/...\") <br>\n\t\twith /reference/ URLs (\"/reference/...\"). <br>\n    <li>validated the HTML.<br>\n    <li>tested the links. They work. Yay!\n--> "
}
[/block]
