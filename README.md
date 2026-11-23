# Sprint 4 Project: E-Commerce Customer Behavior EDA

Exploratory data analysis of the **Olist Brazilian E-Commerce dataset** for the TripleTen Sprint 4 final project.

[Open in Colab](https://colab.research.google.com/github/cassem96-arch/sprint4-eda-project/blob/main/sprint4_eda_project.ipynb)

## Goal
Find out how healthy the business is, which product categories bring in the most revenue and the happiest customers, where customers are located, and whether delivery speed affects review scores.

## Dataset
7 CSV files from Olist (about 99k orders, September 2016 – October 2018): orders, order items, customers, products, reviews, payments, and Portuguese→English category names. The notebook loads them directly from the TripleTen S3 bucket, so it runs in Google Colab with **Runtime → Run all** and needs no uploads.

## Methods
- Inspecting the data with `shape`, `head()`, `info()` and `describe()`
- Cleaning: counting missing values, checking for duplicates, converting text dates to datetime
- SQL inside the notebook (in-memory `sqlite3` + `pd.read_sql`): order-status breakdown, top orders by revenue with a JOIN, top customer states
- pandas `merge()` across items, products, translations and reviews; `groupby().agg()` for revenue and review score by category
- matplotlib charts: customers by state (bar), monthly orders (line), delivery days by review score (bar)
- Correlation between delivery time and review score

## Key findings
- **97.02%** of 99,441 orders were delivered; only 0.63% were canceled.
- Orders grew **135.1%** (22,968 → 53,991) from January–August 2017 to January–August 2018. The busiest month was November 2017 with 7,544 orders.
- **Health & beauty** brings in the most revenue (R$1.45M) and has a strong 4.14 average review. The top 10 categories make up 62.4% of item revenue.
- **São Paulo** has 41.9% of the 96,096 unique customers. SP, RJ and MG together have 66.5%.
- Slower delivery means worse reviews (correlation **-0.334**): 1-star orders took 20.85 days on average, while 5-star orders took 10.22 days. Orders that took more than 20 days got a 1–2 star review 38.2% of the time, compared with 8.0% for orders delivered within 10 days.

## Files
- `sprint4_eda_project.ipynb`: the completed and executed notebook, with the Q9 interpretation and the Q10 executive summary
