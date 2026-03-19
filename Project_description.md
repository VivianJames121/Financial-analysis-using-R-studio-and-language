---
title: "My_assignment"
author: "Vivian james"
date: "2026-02-11"
output:
  html_document: default
  pdf_document: default
---

## FINANCIAL STATEMENTS ANALYSIS --

The scenario here is, about the financial statement given and we need to do the analysis for it. And as being the data scientist, we need to work here, for it accordingly.One of your colleagues from the Auditing department has asked you to help them assess the financial statement of organization X.

# This is the so called project description below --

You have been supplied with two vectors of data: monthly revenue and monthly expenses for
the financial year in question. Your task is to calculate the following financial metrics:

- profit for each month
- profit after tax for each month (the tax rate is 30%)
- profit margin for each month - equals to profit after tax divided by revenue
- good months - where the profit after tax was greater than the mean for the year
- bad months - where the profit after tax was less than the mean for the year
- the best month - where the profit after tax was max for the year
- the worst month - where the profit after tax was min for the year

THE MAIN HIGHLIGHTED POINT HERE IS, THAT ALL RESULTS NEED TO BE PRESENTED HERE AS VECTORS.

Results for dollar values need to be calculated with $0.01 precision, but need to be presented in Units of $1,000 (i.e. 1k) with no decimal points.
Results for the profit margin ratio need to be presented in units of % with no decimal points.

# SO THE CODE BELOW IS ATTACHED-- TO GET THE INSIGHT FOR CODE CHUNKS AND WHAT DOES THEY GIVE HERE WHEN AFTER EXECUTING IT --


#Data --

```{r}
revenue <- c(14574.49, 7606.46, 8611.41, 9175.41, 8058.65, 8105.44, 11496.28, 9766.09, 10305.32, 14379.96, 10713.97, 15433.50)
```

Stores monthly sales (income) for 12 months.
Each number = money earned in one month.

```{r}
expenses <- c(12051.82, 5695.07, 12319.20, 12089.72, 8658.57, 840.20, 3285.73, 5821.12, 6976.93, 16618.61, 10054.37, 3803.96)
```

Stores monthly costs for the same 12 months.
Each value = money spent in that month.

#profit for each month --

```{r}
profit = revenue-expenses
profit
```
Calculates how much money is left after expenses.
Profit = Income − Cost.

#profit after tax for each month (the tax rate is 30%) --

```{r}
tax = round(profit *0.3, 2)
tax
```

Takes 30% of profit as tax and rounds to 2 decimals. 
So R multiplies every profit value by 0.30.

This tells:
“How much tax is paid in each month.”
 
```{r}
profit.after.tax = profit - tax
profit.after.tax
```

This is the actual money the business keeps.

This is the most important number for decision-making:

-Investors look at this
-Owners look at this
-Business growth depends on this

#profit margin for each month - equals to profit after tax divided by revenue --
```{r}
profit.margin = round(profit.after.tax / revenue,2 * 100)
profit.margin
```
This tells:

“Out of every ₹100 of sales, how much is real profit?”

Example:

If margin = 0.25 → 25% profit
Meaning ₹25 profit on every ₹100 of revenue.
This shows business efficiency, not just profit.

#good months - where the profit after the tax was greater than the mean for the year --

```{r}
mean.pat = mean(profit.after.tax)
mean.pat
```

```{r}
good.months = profit.after.tax > mean.pat
good.months
```
Marks TRUE if a month did better than average, else FALSE.

#bad.months - where the profit after the tax was less than the mean for the year --

```{r}
bad.months = !good.months
bad.months
```
Opposite of good months → below-average months.

#the best month - where the profit after tax was maximum for the year --

```{r}
best.month = profit.after.tax == max(profit.after.tax)
best.month
```
Marks TRUE for the highest profit month.

#the worst month - where the profit after tax was minimum for the year --

```{r}
worst.month = profit.after.tax == min(profit.after.tax)
worst.month
```

Marks TRUE for the lowest profit month.

#units of thousands --

```{r}
revenue.1000 = round(revenue/1000)
revenue.1000
```
```{r}
expenses.1000 = round(expenses/1000)
expenses.1000
```
```{r}
profit.1000 = round(profit/1000)
profit.1000
```

```{r}
profit.after.tax.1000 = round(profit.after.tax / 1000)
profit.after.tax.1000
```

This is only for readability.
Instead of 14574, it shows 15 (₹15k approx).
Used in reports and dashboards.

```{r}
m = rbind(revenue.1000, expenses.1000, profit.1000, profit.after.tax.1000, profit.margin, good.months, bad.months, worst.month, best.month)
m
```
