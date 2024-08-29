---
title: "Text formats and notational conventions"
slug: "text-formatting-conventions"
excerpt: ""
hidden: false
metadata: 
  description: "Learn about text formats and notational conventions used in Clover developer documents, including the use of code blocks and information blocks to understand and emphasize essential information."
  image: 
    - "https://files.readme.io/f350207-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Mon Apr 15 2019 16:03:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 12 2024 11:47:12 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

Standard text format and notational conventions in developer documents help to understand and emphasize essential information.

## Text and brackets

[block:parameters]
{
  "data": {
    "h-0": "Format",
    "h-1": "Usage",
    "0-0": "Bold",
    "0-1": "Use **bold** text for:  \n  \n- Button and icon names, tabs,  and menus, options, and check box names, when indicating an action.  \n  Example: On the home screen, tap **Orders**.  \n- Navigation paths.  \n  Example: From the home page, click **File** > **Settings** > **Web configuration**.",
    "1-0": "Italics",
    "1-1": "Use _italics_ formatting for variable text, such as folder names or ID values that vary for each user.",
    "2-0": "Monospace",
    "2-1": "Use `Courier` monospaced, gray-highlighted text for short code samples, file paths, system messages, and user inputs.  \nExample: Open a web browser and navigate to `http://localhost:8080`.",
    "3-0": "Angle brackets \\<  >",
    "3-1": "Use for identifiers, parameters, or argument values provided by users.  \nExample:  \n`git config [<file-option>] [--type=<type>] --add name value`",
    "4-0": "Curly brackets {  }",
    "4-1": "Use for text that varies based on the user and needs to be replaced with values unique to the user or environment. For example, each Clover merchant has a unique identifier. In the documents, this is indicated with a placeholder: `{mId}` or `{merchantId}`. When copying sample code that includes bracketed values, replace both the brackets and sample values with your data.  \nExample: In the GET request for a single merchant, the sample URL includes the bracketed value `{mId}`. When using the URL in your own code, replace `{mId}` with the ID value of the merchant you want to retrieve.  \n  \n**GET request with placeholder:**  \n`curl -X GET https://apisandbox.dev.clover.com/v3/merchants/{mId}`  \n**GET request with actual value:**  \n`curl -X GET https://apisandbox.dev.clover.com/v3/merchants/XKNP0ZWV58J8E`",
    "5-0": "Square brackets [  ]",
    "5-1": "Use to indicate a parameter that is optional.  \nExample: In `function(param1 [, param2])`  \n`param1 `is required and `param2` is optional.",
    "6-0": "Links",
    "6-1": "Use text in Clover [green font](doc:text-formatting-conventions)  (#228800) for links to other sections of the docs or to external resources like our GitHub software development kit (SDK) repositories."
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Code blocks

Use for long code samples in separate blocks for easier reading. You can click **Copy** to use the content of each block in your code.

```json JSON code block
{
  "elements": [
      { "item": {"id": "ABWN2X43EXJN8"}},
      { "item": {"id": "ABWN2X43EXJN8"}},
      { "item": {"id": "F1RBG5MKD3SQR"}},
      { "item": {"id": "F1RBG5MKD3SQR"}},
      { "item": {"id": "S9230FJR93DFJ"}},
      { "item": {"id": "S9230FJR93DFJ"}}
  ]
}
```

## Information blocks

Use to provide additional information or caution about certain actions.

> 📘 NOTE
> 
> Notes are informational and provide you with extra details for the section you are reading.

> 🚧 IMPORTANT
> 
> Important blocks contain information you need to read to ensure your code works properly.

> ❗️ WARNING
> 
> Warnings caution you against actions that may cause data loss or damage to a Clover device.
