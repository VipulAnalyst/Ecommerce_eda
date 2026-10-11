# SWYNEX: E-commerce Orders: Exploratory Data Analysis

**Author:** Vipul Dubey

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
4. Analysed recorded order value by category, city and month
5. Compared order outcomes (Delivered / Cancelled / Pending) across payment methods

## Anomalies Found
| Order | Issue |
|---|---|
| ORD0052 | Quantity = -2 (invalid) |
| ORD0071 | Discount = 110 (over 100%) |
| ORD0091 | Total_Amount = 99999 (placeholder-like value; order is Pending) |

These rows were kept in the dataset. ORD0091 was excluded from the all-status order-value charts and totals. The remaining
anomalies were retained, so these figures are exploratory and need validation.

## Key Insights
1. *Electronics leads recorded order value.* Electronics accounts for ~114.7k, about 46% of total order
   value (~247k). The top three categories (Electronics, Bags, Home & Kitchen) make up ~91%,
   while Stationery is under 2%.
2. *Recorded order value is concentrated in a few cities.* Delhi, Gurugram and Noida together account
   for ~50% of order value. Bengaluru is the weakest at ~7.4k (3%).
3. *Cancellation rates differ across payment methods in this sample.* Credit Card (35%) and Cash On Delivery (29%)
   have much higher cancellation rates than Debit Card (15%) and UPI (12%).
4. *Cancelled and pending orders inflate some categories.* Counting only Delivered orders,
   Bags falls from ~62k to ~19.2k and Home & Kitchen (~32k) moves ahead of it. Delivered order value does not prove that payment was collected.
5. *Monthly recorded order value varies.* August peaks at ~59.5k, March is the low at ~12k, and
   Apr-Jun are steady at ~31.5–34k. The latest recorded date is Sep 25; September coverage is
   incomplete or unverified. Its lower total cannot by itself establish a business decline.

## Limitations
- Small dataset (116 orders), so some city, category and payment groups are small and
  differences should be read as indicative, not conclusive.
- Order-value figures use Total_Amount as recorded and include Cancelled and Pending
  orders unless stated otherwise; they are not accounting revenue or confirmed collections.
- Negative quantity and invalid discount values remain. Product/category consistency
  also needs validation before treating category totals as reliable business metrics.
- Dataset provenance and full reporting coverage have not been verified.

## Tools
Python, pandas, matplotlib, seaborn, Jupyter Notebook (VS Code)

## Run locally

Use Python 3.10 or newer. Download or clone this repository, then run:

```bash
python -m pip install -r requirements.txt
python -m notebook
```

Open `EDA_data.ipynb` from the repository folder and run all cells in order.
The notebook reads `cleaned_data.csv` using a relative path. No input CSV values
are modified by this notebook.
