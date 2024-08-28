---
title: "Calculate order totals"
slug: "calculating-order-totals"
excerpt: ""
hidden: false
metadata: 
  description: "The page provides an example to calculate order totals."
  image: []
  robots: "index"
createdAt: "Fri Oct 30 2020 01:45:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Dec 11 2023 16:33:27 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


When you create orders, you can view order details and receipts using the **Orders** app on the Merchant Dashboard for your test merchant. The order receipt displays the order total breakdown.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bfa9733-sample_receipt.png",
        "sample_receipt.png",
        "Order receipt that displays the order total breakdown"
      ],
      "align": "center",
      "sizing": "35",
      "border": true,
      "caption": "Sample order receipt"
    }
  ]
}
[/block]


The following example shows how to calculate order totals.

> 📘 NOTE
> 
> When rounding decimal amounts smaller than a cent, such as tax per line item, calculate rounding with the round half up rule. For example, the rounding value of $33.654 is $33.65 and the rounding value of $33.455 is $33.46.

# Step 1: Line item calculations

Starting with the line item price, add any modifier costs.

In the following table, the cost of the `Avocado` and `Tofu` modifiers are $1.00 each. When you add the price of these modifiers to the `Caesar Salad` price, the subtotal with modifiers is $14.00 ($12.00 + $1.00 + $1.00). Similarly, the `Greek Salad` subtotal with modifiers is $12.00 ($10.00 + $1.00 + $1.00).

[block:parameters]
{
  "data": {
    "h-0": "Line item",
    "h-1": "Price",
    "h-2": "Modifiers",
    "h-3": "Cost",
    "h-4": "Subtotal with modifiers",
    "0-0": "Caesar Salad",
    "0-1": "$12.00",
    "0-2": "Avocado  \nTofu",
    "0-3": "$1.00  \n$1.00",
    "0-4": "$14.00",
    "1-0": "Greek Salad",
    "1-1": "$10.00",
    "1-2": "Avocado  \nTofu",
    "1-3": "$1.00  \n$1.00",
    "1-4": "$12.00"
  },
  "cols": 5,
  "rows": 2,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


# Step 2: Line item discounts

From the line item subtotal with modifiers:

1. Subtract any percentage discounts, and then
2. Subtract any numerical discounts.

In the following table, the value of the `Lunch deal` line item discount is $1.00. When you apply this discount to the `Caesar Salad` subtotal, the new subtotal after discounts is $13.00 ($14.00 - $1.00).

The value of the `25% off select salads` line item discount is 25% of the.`Greek Salad` subtotal (25% of $12.00 = $3.00). When you apply this discount to the `Greek Salad` subtotal, the new subtotal after discounts is $9.00 ($12.00 - $3.00).

| Line item    | Subtotal | Line item discounts   | Value | Subtotal after discounts |
| :----------- | :------- | :-------------------- | :---- | :----------------------- |
| Caesar Salad | $14.00   | Lunch deal            | $1.00 | $13.00                   |
| Greek Salad  | $12.00   | 25% off select salads | $3.00 | $9.00                    |
|              |          |                       |       | **$22.00**               |

# Step 3: Order-level discounts

From the subtotal after line item discounts:

1. Subtract any order-level percentage discounts and then
2. Subtract any order-level numerical discounts.

In the following table, the value of the `15th visit 15% off` order-level discount is 15% of each line item subtotal. When you subtract this discount from the `Caesar Salad` subtotal, the new subtotal after order-level discounts is $11.05 ($13.00 - $1.95). Similarly, the `Greek Salad` subtotal after order-level discounts is $7.65 ($9.00 - $1.35).

| Line item    | Subtotal | Order level discounts | Value | Subtotal after discounts |
| :----------- | :------- | :-------------------- | :---- | :----------------------- |
| Caesar Salad | $13.00   | 15th visit 15% off    | $1.95 | $11.05                   |
| Greek Salad  | $9.00    |                       | $1.35 | $7.65                    |
|              |          |                       |       | **$18.70**               |

# Step 4: Service charges

To the subtotal after order-level discounts, add any service charges.

In the following table, apply a service charge of 5% to the order subtotal after order-level discounts.

| Subtotal | Service charge rate | Service charge collected |
| :------- | :------------------ | :----------------------- |
| $18.70   | 5%                  | $0.94                    |

# Step 5: Taxes

To retrieve tax rates for order line items, send a `GET` request to `/v3/merchants/{mId}/orders/{orderId}/line_items?expand=taxRates`.

```json Sample response
{
    "elements": [
        {
            ...
            "name": "Greek Salad",
            "price": 1000,
            ...
            "taxRates": {
                "elements": [
                    {
                        "id": "6HA0Z3Z5DPCBC",
                        ...
                        "name": "Tax B",
                        "rate": 500000 // 5% tax applied to Greek Salad
                    }
                ]
            }
        },
        {
            ...
            "name": "Caesar Salad",
            "price": 1200,
            ...
            "taxRates": {
                "elements": [
                    {
                        "id": "77FAGR71YYD5M", // tax rate object
                        ...
                        "name": "Tax A",
                        "rate": 1000000 // 10% tax applied to Caesar Salad
                    }
                ]
            }
        }
    ],
    "href": "http://sandbox.dev.clover.com/v3/merchants/{mId}/orders/{orderId}/line_items?limit=100"
}
```

> 🚧 IMPORTANT
> 
> If `vat` is set to `true` in the merchant properties, the merchant uses a value-added tax. This means the tax amount is already included in the line item total and no additional amount should be added for tax.

Using the subtotal after order-level discounts (Step 3), calculate tax rates per taxable line item.

In the following table:

- Apply a 10% `Tax A` tax to `Caesar Salad`
- Apply a 5% `Tax B` tax to `Greek Salad`

| Line item    | Subtotal after discounts | Tax   | Tax rate | Tax collected |
| :----------- | :----------------------- | :---- | :------- | :------------ |
| Caesar Salad | $11.05                   | Tax A | 10%      | $1.11         |
| Greek Salad  | $7.65                    | Tax B | 5%       | $0.38         |
|              |                          |       |          | **$1.49**     |

> 📘 NOTE
> 
> If multiple line items in an order are taxed using the same tax rate object, Clover calculates taxes on the subtotal of those items. In the above example, if the same `Tax A` object of 10% is applied to the $11.05 and $7.65 values, calculate tax on the sum of these values.
> 
> ```
> ($11.05 + $7.65) * 0.10) = $1.87
> ```

See [Tax Reports: Examples](doc:tax-reports-examples) for more information about calculating taxes for line items.

# Step 6: Order total

The order total is the sum of the subtotal after any discounts, taxes, and service charges, if any.

In the following table, the order total is $21.51 ($18.70 + $1.87 + $0.94).

| Subtotal after discounts | Taxes | Service charges | Total      |
| :----------------------- | :---- | :-------------- | :--------- |
| $18.70                   | $1.49 | $0.94           | **$21.13** |

# Apply multiple tax rates to line items

A line item can have multiple tax rates. In the following table, each line item has the `Tax A` and `Tax B` applied to it.

| Line item    | Subtotal after discounts | Tax   | Tax rate | Tax collected |
| :----------- | :----------------------- | :---- | :------- | :------------ |
| Caesar Salad | $11.05                   | Tax A | 10%      | $1.11         |
|              |                          | Tax B | 5%       | $0.55         |
| Greek Salad  | $7.65                    | Tax A | 10%      | $0.77         |
|              |                          | Tax B | 5%       | $0.38         |
|              |                          |       |          | **$2.81**     |

See [Tax Reports: Examples](doc:tax-reports-examples) for more examples of different use cases for calculating line item tax calculations.
