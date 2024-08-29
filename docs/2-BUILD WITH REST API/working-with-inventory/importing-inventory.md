---
title: "Import inventory"
slug: "importing-inventory"
excerpt: ""
hidden: false
metadata: 
  description: "Use the sample inventory MS Excel file to get started with your test merchant."
  image: []
  robots: "index"
createdAt: "Wed Mar 02 2022 22:08:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:28 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


Clover merchants can import bulk inventory items using an MS Excel sheet. You can use the [sample inventory](https://clover.box.com/s/y08he8u7llov7shufskgyb5stlgcs6s8) file to get started with your test merchant.  
To bulk import inventory items:

1. Log in to your [sandbox Developer Dashboard](https://sandbox.dev.clover.com/developer-home/login).
2. From the Developer Account drop-down list, click a merchant name under Businesses. The Merchant Dashboard for the selected merchant appears.
3. From the left navigation menu, click **Inventory**. The Items page with import details appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/546e766-Bulk_inventory_update.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "550px",
      "border": true
    }
  ]
}
[/block]


4. Click **Download Template** to download a sample inventory spreadsheet. It is saved to your default Downloads folder.

- Go to the Instructions tab in the template spreadsheet and read the instructions.
- Click the Items tab to update the inventory details relevant to your business and save the file.  
  **Note: **You can rename the inventory spreadsheet, as needed.

5. Click **Import Your Inventory Spreadsheet**. The Import Inventory page appears. You can only import a spreadsheet in .xls or .xlsx format that does not exceed 10 MB in file size.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6c52477-Bulk_inventory_2.png",
        "Bulk inventory 2.png",
        948
      ],
      "align": "center",
      "sizing": "50",
      "border": true
    }
  ]
}
[/block]


6. Import the inventory spreadsheet. You can either: 

- Navigate to your inventory spreadsheet and drag and drop it into the Import Inventory page.  
  -or-
- Click Choose File to browse and select the inventory spreadsheet.  
  The To be added to inventory page displays the name of the imported spreadsheet and count of items in each of the tabs in the imported spreadsheet.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6cc82b6-Bulk_inventory_4.png",
        "Bulk inventory 4.png",
        976
      ],
      "align": "center",
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


7. Validate the information on the page and click **Continue**. A Success message appears.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/595a155-Bulk_inventory_3.png",
        "Bulk inventory 3.png",
        1784
      ],
      "align": "center",
      "sizing": "80",
      "border": true
    }
  ]
}
[/block]


8. Do one of the following:

- Click **Back to my inventory**. The Items page displays the inventory items.  
  -or- 
- Click **Start new import** to import another inventory spreadsheet.
