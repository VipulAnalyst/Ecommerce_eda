# SWYNEX: E-commerce Orders: Exploratory Data Analysis

## Overview
Exploratory analysis of the cleaned e-commerce orders dataset from Task 1
(cleaned_data.csv, 116 orders, 14 columns), done in Python (pandas, matplotlib, seaborn).
The goal is to calculate key statistics and identify trends, patterns and anomalies.

## Files
- EDA_data.ipynb: full analysis with charts and written insights
- cleaned_data.csv: cleaned dataset from Task 1 (input)

## Approach
1. Loaded the cleaned dataset and converted Order_Date to datetime
2. Checked structure, data types, missing values and summary statistics
3. Identified anomalies using describe() and row-level checks
4. Analysed revenue by category, city, payment method and month
5. Compared order outcomes (Delivered / Cancelled / Pending) across payment methods

## Anomalies Found
| Order | Issue |
|---|---|
| ORD0052 | Quantity = -2 (invalid) |
| ORD0071 | Discount = 110 (over 100%) |
| ORD0091 | Total_Amount = 99999 (placeholder-like value; order is Pending) |

These rows were kept in the dataset. ORD0091 was excluded from all revenue charts and
totals because it would have inflated revenue by about 40%.

## Key Insights
1. *Electronics drives revenue.* Electronics brings in ~114.7k, about 46% of total order
   value (~247k). The top three categories (Electronics, Bags, Home & Kitchen) make up ~91%,
   while Stationery is under 2%.
2. *Revenue is concentrated in a few cities.* Delhi, Gurugram and Noida together account
   for ~50% of order value. Bengaluru is the weakest at ~7.4k (3%).
3. *Cancellations depend on payment method.* Credit Card (35%) and Cash On Delivery (29%)
   have much higher cancellation rates than Debit Card (15%) and UPI (12%).
4. *Cancelled and pending orders inflate some categories.* Counting only Delivered orders,
   Bags falls from ~62k to ~18k and Home & Kitchen (~32k) moves ahead of it. Order value
   placed is not the same as revenue collected.
5. *Monthly revenue is volatile.* August peaks at ~61k, March is the low at ~12k, and
   Apr-Jun are steady at ~33-35k. [Add what the August check showed, e.g. a few large
   orders drove the spike.] September is a partial month (data ends Sep 25), so its drop
   is not a real decline.

## Limitations
- Small dataset (116 orders), so some city, category and payment groups are small and
  differences should be read as indicative, not conclusive.
- Revenue figures use Total_Amount as recorded and include Cancelled and Pending orders
  unless stated otherwise.

## Tools
Python, pandas, matplotlib, seaborn, Jupyter Notebook (VS Code)
