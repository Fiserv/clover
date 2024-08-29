---
title: "Tax Reports: Examples"
slug: "tax-reports-examples"
excerpt: ""
hidden: false
metadata: 
  description: "Need to understand how taxes affect Clover merchant transactions? This topic provides various examples of how different tax rates and scenarios are applied to orders."
  image: 
    - "https://files.readme.io/8a62444-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Tue Nov 12 2019 21:45:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jul 16 2024 04:36:29 GMT+0000 (Coordinated Universal Time)"
---
<meta name="description" content="Need to understand how taxes affect Clover merchant transactions? This topic provides various examples of how different tax rates and scenarios are applied to orders.">

[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n</div>\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: hidden;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# Example 1: One Tax Applied to All Items

A merchant has one tax rate applied uniformly to all items. One tax, taxable amount matches sub-total of prices on the order. 

**Order** 

| Item      | Price      | Tax              | Tax rate | Tax collected | Subtotal   |
| :-------- | :--------- | :--------------- | :------- | :------------ | :--------- |
| Wrench    | $10.00     | Multnomah County | 5%       | $0.50         | $10.50     |
| Hammer    | $10.00     | Multnomah County | 5%       | $0.50         | $10.50     |
| **Total** | **$20.00** |                  |          | **$1.00**     | **$21.00** |

**Payment table** 

| Amount | Tax amount |
| :----- | :--------- |
| $21.00 | $1.00      |

**Payment tax rate table** 

| Taxable amount | Tax              | Tax rate |
| :------------- | :--------------- | :------- |
| $20.00         | Multnomah County | 5%       |

**Tax report** 

|              | Taxable amount | Tax              | Tax rate | Tax collected |
| :----------- | :------------- | :--------------- | :------- | :------------ |
| **Payments** | $20.00         | Multnomah County | 5%       | $1.00         |
| **Net**      | **$20.00**     |                  |          | **$1.00**     |

# Example 2: Two items have different tax rates

Wheat has a 10% wheat tax, and butter has a 5% butter tax. The net taxable amount is the same as the subtotal of the prices on the order.

**Order** 

| Item      | Price      | Tax        | Tax rate | Tax collected | Subtotal   |
| :-------- | :--------- | :--------- | :------- | :------------ | :--------- |
| Wheat     | $10.00     | Wheat tax  | 10%      | $1.00         | $11.00     |
| Butter    | $10.00     | Butter tax | 5%       | $0.50         | $10.50     |
| **Total** | **$20.00** |            |          | **$1.50**     | **$21.50** |

**Payment table** 

| Amount | Tax amount |
| :----- | :--------- |
| $21.50 | $1.50      |

**Payment tax rate table** 

| Taxable amount | Tax        | Tax rate |
| :------------- | :--------- | :------- |
| $10.00         | Wheat tax  | 10%      |
| $10.00         | Butter tax | 5%       |

**Tax report** 

|              | Taxable amount | Tax        | Tax rate | Tax collected |
| :----------- | :------------- | :--------- | :------- | :------------ |
| **Payments** | $10.00         | Wheat tax  | 10%      | $1.00         |
|              | $10.00         | Butter tax | 5%       | $0.50         |
| **Net**      | **$20.00**     |            |          | **$1.50**     |

# Example 3: Two Default Taxes

Each item gets the same two taxes. The net taxable amount is NOT the sum of taxable amounts in the Payment tax rate table.

**Order** 

| Item      | Price      | Tax              | Tax rate | Tax collected | Subtotal   |
| :-------- | :--------- | :--------------- | :------- | :------------ | :--------- |
| Wrench    | $10.00     | Multnomah County | 5%       | $0.50         | $11.50     |
|           |            | Oregon state     | 10%      | $1.00         |            |
| Hammer    | $10.00     | Multnomah County | 5%       | $0.50         | $11.50     |
|           |            | Oregon state     | 10%      | $1.00         |            |
| **Total** | **$20.00** |                  |          | **$3.00**     | **$23.00** |

**Payment table** 

| Amount | Tax amount |
| :----- | :--------- |
| $23.00 | $3.00      |

**Payment tax rate table** 

| Taxable amount | Tax              | Tax rate |
| :------------- | :--------------- | :------- |
| $20.00         | Multnomah County | 5%       |
| $20.00         | Oregon state     | 10%      |

**Tax report** 

|              | Taxable amount | Tax              | Tax rate | Tax collected |
| :----------- | :------------- | :--------------- | :------- | :------------ |
| **Payments** | $20.00         | Multnomah County | 5%       | $1.00         |
|              | $20.00         | Oregon state     | 10%      | $2.00         |
| **Net**      | **$20.00**     |                  |          | **$3.00**     |

# Example 4: Two Items with Same Tax, One Item has a Special Tax

Both the items have the same tax rate, but one of the items has a special tax rate.

**Order** 

| Item      | Price      | Tax              | Tax rate | Tax collected | Subtotal   |
| :-------- | :--------- | :--------------- | :------- | :------------ | :--------- |
| Wrench    | $10.00     | Multnomah County | 5%       | $0.50         | $11.50     |
|           |            | Wrench tax       | 10%      | $1.00         |            |
| Hammer    | $10.00     | Multnomah County | 5%       | $0.50         | $10.50     |
| **Total** | **$20.00** |                  |          | **$2.00**     | **$22.00** |

**Payment table** 

| Amount | Tax amount |
| :----- | :--------- |
| $22.00 | $2.00      |

**Payment tax rate table** 

| Taxable amount | Tax              | Tax rate |
| :------------- | :--------------- | :------- |
| $20.00         | Multnomah County | 5%       |
| $10.00         | Wrench tax       | 10%      |

**Tax report** 

|              | Taxable amount | Tax              | Tax rate | Tax collected |
| :----------- | :------------- | :--------------- | :------- | :------------ |
| **Payments** | $20.00         | Multnomah County | 5%       | $1.00         |
|              | $10.00         | Wrench tax       | 10%      | $1.00         |
| **Net**      | **$20.00**     |                  |          | **$2.00**     |

> 📘 NOTE
> 
> Since the `Wrench tax` does not apply to the `Hammer` item, the `Wrench tax` does not contribute to the `Net` amount in the **Tax report**.

# Example 5: Items with Zero Tax or Merchants are Tax Exempt

Mark items with no tax as a 0% "No Tax Applied" tax. Merchants, such as nonprofits or schools, who are tax-exempt can remove tax from an order. 

**Order 1** 

| Item            | Price      | Tax              | Tax rate | Tax collected | Subtotal   | Tax removed |
| :-------------- | :--------- | :--------------- | :------- | :------------ | :--------- | :---------- |
| Delivery charge | $10.00     | No tax applied   | 0%       | $0.00         | $10.00     | False       |
| Hammer          | $10.00     | Multnomah County | 5%       | $0.50         | $10.50     | False       |
| **Total**       | **$20.00** |                  |          | **$0.50**     | **$20.50** | **False**   |

**Order 2** 

| Item            | Price      | Tax            | Tax rate | Tax collected | Subtotal   | Tax removed |
| :-------------- | :--------- | :------------- | :------- | :------------ | :--------- | :---------- |
| Delivery charge | $10.00     | No tax applied | 0%       | $0.00         | $10.00     | False       |
| **Total**       | **$10.00** |                |          | **$0.00**     | **$10.00** | **False**   |

**Order 3 (Tax-exempt merchant)** 

| Item      | Price      | Tax | Tax rate | Tax collected | Subtotal   | Tax removed |
| :-------- | :--------- | :-- | :------- | :------------ | :--------- | :---------- |
| Wrench    | $10.00     | -   | -        | -             | $10.00     | True        |
| Hammer    | $10.00     | -   | -        | -             | $10.00     | True        |
| **Total** | **$20.00** | -   | -        | -             | **$20.00** | **True**    |

**Payment table** 

| Amount | Tax              | Tax amount |
| :----- | :--------------- | :--------- |
| $20.00 | Multnomah County | $0.50      |
| $10.00 | Wrench tax       | $0.00      |

**Payment tax rate table** 

| Order | Taxable amount | Tax              | Tax rate |
| :---- | :------------- | :--------------- | :------- |
| 1     | $10.00         | Multnomah County | 5%       |
| 1     | $10.00         | No tax applied   | 0%       |
| 2     | $10.00         | No tax applied   | 0%       |

**Tax report** 

|              | Taxable amount | Tax              | Tax rate | Tax collected |
| :----------- | :------------- | :--------------- | :------- | :------------ |
| **Payments** | $10.00         | Multnomah County | 5%       | $0.50         |
|              | $20.00         | No tax applied   | 0%       | $0.00         |
|              | $10.00         | Tax removed      | 0%       | $0.00         |
| **Net**      | **$50.00**     |                  |          | **$0.50**     |

# Example 6: VAT (Value Added Tax)

With VAT, an advertised price of the item includes the tax rather than adding tax to the order total at the time of payment. Clover saves the advertised price with VAT as the taxable amount.

For example, if a pair of socks is advertised in Ireland at `€6` and the VAT is `20%`, the customer pays the `€6` and the merchant revenue is `€5`. The collected tax is `€1` (`€5 x 20%`). Clover saves the advertised price of `€6` and the `20%` VAT value.

**Order** 

| Item      | Advertised price | Revenue | Tax         | Tax rate | Tax collected | Subtotal  |
| :-------- | :--------------- | :------ | :---------- | :------- | :------------ | :-------- |
| Socks     | €6.00            | €5.00   | Ireland tax | 20%      | €1.00         | €6.00     |
| **Total** | **€6.00**        |         |             |          | **€1.00**     | **€6.00** |

**Payment table** 

| Amount | Tax amount |
| :----- | :--------- |
| €6.00  | €1.00      |

**Payment tax rate table** 

| Taxable amount | Tax         | Tax rate | Tax paid |
| :------------- | :---------- | :------- | :------- |
| €6.00          | Ireland tax | 20%      | €1.00    |

**Tax report** 

|              | Taxable amount | Tax         | Tax rate | Tax collected |
| :----------- | :------------- | :---------- | :------- | :------------ |
| **Payments** | €6.00          | Ireland tax | 20%      | €6.00         |
| **Net**      | **€6.00**      |             |          | **€1.00**     |

# Example 7: VAT, Multiple Rates Per Item

Socks are advertised for €6. There are two VAT rates: 15% and 5%.

**Calculation**

- Revenue = €6 ÷ (1 + 0.15 + 0.05) = €5
- 15% tax = €5 x 0.15 = €0.75
- 5% tax = €5 x 0.05 = €0.25
- Total tax = €0.75 + 0.25 = €1.00

**Order** 

| Item      | Tax         | Tax Rate | Subtotal |
| :-------- | :---------- | :------- | :------- |
| **Socks** | Ireland Tax | 15%      | €6       |
|           | Dublin Tax  | 5%       |          |
| **Total** |             |          | **€6**   |

**Payment table** 

| Amount | Tax Amount |
| :----- | :--------- |
| €6     | €1.00      |

**Payment tax rate table** 

| Taxable Amount | Tax         | Tax Rate | Tax Paid |
| :------------- | :---------- | :------- | :------- |
| €6.00          | Ireland Tax | 15%      | €0.75    |
| €6.00          | Dublin Tax  | 5%       | €0.25    |

**Tax report** 

|          | Taxable Amount | Tax         | Tax Rate | Tax Collected |
| :------- | :------------- | :---------- | :------- | :------------ |
| Payments | €6.00          | Ireland Tax | 15%      | €0.78         |
|          | €6.00          | Dublin Tax  | 5%       | €0.29         |
| Net      | €6.00          |             |          | €1.07         |

# Example 8: Two Different Rate Objects with the Same Rate on the Same Order

A merchant has accidentally built their inventory using two 13.5% tax rate rows for the same tax and has assigned items to both tax rates. 

The order Includes:

- €4 bottle of water at a 13.5% rate #1
- €4 espresso at a 13.5% rate #2

With two different rates on the same order, Clover combines subtotals for each tax entity and separately rounds on a lower subtotal for the items taxed at each rate. Since the merchant is in Ireland, a VAT is included.

The tax code assumes that these rates are for separate entities and the tax paid calculations are separate for the water and the espresso. If there was only one 13.5% rate, the line item prices would be combined as €8 before calculating the tax. So it would use a larger total which leads to less rounding.

**Clover tax calculation**

- €4 at 13.5% rate #1 with the base price of €3.52 and €0.48 tax
- €4 at 13.5% rate #2 with the base price of €3.52 and €0.48 tax

**What the merchant expects**  
€8 at 13.5% with the base price of €7.05 and €0.95 tax

With two separate tax rates, there has to be more rounding, in this case, one more rounding up by one cent whereas there would be only one rounding with one tax rate.

## Clover tax calculation

**Order** 

| Item      | Tax                | Tax Rate | Subtotal |
| :-------- | :----------------- | :------- | :------- |
| Water     | Ireland Tax        | 13.5%    | €4       |
| Espresso  | Ireland Tax (copy) | 13.5%    | €4       |
| **Total** |                    |          | **€8**   |

**Payment table** 

| Amount | Tax   |
| :----- | :---- |
| €8.00  | €0.96 |

**Payment tax rate table**  
The system assumes that the tax rates should be calculated separately as they are separate entities.

| Taxable Amount | Tax                | Tax Rate | Tax Paid |
| :------------- | :----------------- | :------- | :------- |
| €4.00          | Ireland Tax        | 13.5%    | €0.48    |
| €4.00          | Ireland Tax (copy) | 13.5%    | €0.48    |

**Tax report** 

|              | Taxable Amount | Tax                | Tax Rate | Tax Collected |
| :----------- | :------------- | :----------------- | :------- | :------------ |
| **Payments** | €4.00          | Ireland Tax        | 13.5%    | €0.48         |
|              | €4.00          | Ireland Tax (copy) | 13.5%    | €0.48         |
| **Net**      | **€8.00**      |                    |          | **€0.96**     |

## What the merchant expects

**Order** 

| Item      | Tax         | Tax Rate | Subtotal |
| :-------- | :---------- | :------- | :------- |
| Water     | Ireland Tax | 13.5%    | €4       |
| Expresso  | Ireland Tax | 13.5%    | €4       |
| **Total** |             |          | **€8**   |

**Payment table** 

| Amount | Tax Amount |
| :----- | :--------- |
| €8.00  | €0.95      |

**Payment tax rate table** 

| Taxable Amount | Tax         | Tax Rate | Tax Collected |
| :------------- | :---------- | :------- | :------------ |
| €8.00          | Ireland Tax | 13.5%    | €0.95         |

**Tax report** 

|              | Taxable Amount | Tax         | Tax Rate | Tax Collected |
| :----------- | :------------- | :---------- | :------- | :------------ |
| **Payments** | €8.00          | Ireland Tax | 13.5%    | €0.95         |
| **Net**      | **€8.00**      |             |          | **€0.95**     |
