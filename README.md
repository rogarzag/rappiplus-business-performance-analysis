# RappiPlus Business Performance Analysis

**Author:** Rodrigo Garza García  
**Role:** Strategy & Public Affairs | Business Analysis & Data Analytics  
**Portfolio:** [GitHub Profile](https://github.com/rogarzag)

End-to-end business performance analysis for **RappiPlus**, covering data quality, revenue, costs, profitability, marketing, conversion, retention, product performance, and an A/B test. The project combines **Python, SQL, statistical testing, and Tableau** to turn multiple data sources into business insights and interactive dashboards.

## 📊 Interactive Dashboard

Explore the full interactive story on Tableau Public:

[View Dashboard on Tableau Public](https://public.tableau.com/views/RappiPlusBusinessPerformanceDashboard/RappiPlusBusinessPerformanceStory?:language=es-ES&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

### Executive Overview

![RappiPlus Executive Overview](images/executive_overview.png)

### Order & Product Detail

![RappiPlus Order & Product Detail](images/order_product_detail.png)

## 🎯 Business Objective

The project evaluates RappiPlus from several business perspectives:

- Can the available data be trusted?
- Is the business profitable?
- Which products and categories drive performance?
- Where do users drop off in the conversion funnel?
- Do users return after registration?
- Did the checkout UI experiment improve conversion?
- How can the results be communicated clearly through an executive dashboard?

## 📌 Executive Summary

The raw dataset reports **$51.99M in revenue**, but a small number of extreme-quantity records have a disproportionate impact on the results. These observations account for **81.45% of reported revenue** and **91.12% of known product cost**.

To better represent typical operating performance, the Tableau dashboards use an adjusted view that excludes extreme and invalid quantities.

### Adjusted business performance

- **Revenue:** $9.64M
- **Known Product Cost:** $3.83M
- **Product-Level Profit Before Marketing:** $5.78M
- **Average Order Value:** $385.97
- **Average Items per Order:** 1.50
- **Top-Selling Product:** Vacuum-Pro-Black — 6,284 units

### Customer behavior

- **Final funnel conversion:** 80.04%
- Largest relative funnel drop: `begin_checkout → add_payment_info`
- **Week-3 retention:** approximately 40%–44% across cohorts
- Best week-3 cohort: **February — 43.98%**

### A/B test

- Control conversion: **15.69%**
- Treatment conversion: **16.29%**
- **p-value: 0.4161**
- Result: no statistically significant evidence that the checkout UI change improved conversion.

## 🗂️ Data Sources

The project uses multiple datasets covering different areas of the business:

- **Orders:** order-level sales, quantities, prices, discounts, products, countries, and devices
- **Product Catalog:** product categories, suppliers, and unit costs
- **Marketing:** marketing spend by date, country, campaign, and channel
- **Events (SQL):** user activity across the conversion funnel
- **Users & User Activity (SQL):** registration and retention behavior
- **Checkout Experiment:** control and treatment results for an A/B test

## 🧹 Data Quality & Preparation

Python and Pandas were used to:

- inspect data types, missing values, and duplicates;
- validate dates and numeric fields;
- recover missing marketing channels from campaign IDs;
- identify invalid and extreme quantities;
- review incomplete product-cost information;
- validate reported monetary values;
- preserve unknown-country orders when their sales information remained valid.

A total of **300 orders (1.20%)** had an unknown country. These records were retained because they contained valid sales information and there was not enough evidence to assign them reliably to another country.

## 💰 Profitability & Sales Analysis

The notebook keeps both the raw and adjusted views.

### Raw profitability view

- Reported Revenue: **$51.99M**
- Known Product Cost: **$43.12M**
- Marketing Spend: **$2.87M**
- Estimated Profit After Product Cost and Marketing: **$5.99M**

### Adjusted operating view

The adjusted view excludes extreme and invalid quantities to avoid allowing a small number of unusually large records to dominate the analysis.

- Adjusted Revenue: **$9.64M**
- Adjusted Product Cost: **$3.83M**
- Adjusted Product-Level Profit: **$5.78M**

Marketing is analyzed separately in the notebook. It is not directly allocated to individual products or orders in Tableau because the marketing dataset is stored at a different level of granularity.

## 🛒 Conversion Funnel

SQL was used to measure unique users across the expected customer journey:

`first_visit → select_item → add_to_cart → begin_checkout → add_payment_info → purchase`

Key results:

- `first_visit`: 7,796 users
- `purchase`: 6,240 users
- Final conversion: **80.04%**
- Largest relative decline: `begin_checkout → add_payment_info` with **86.71%** stage conversion

The `select_item → add_to_cart` ratio is slightly above 100%, indicating that the event tracking is not strictly sequential for every user.

## 🔁 Cohort Retention

Monthly cohorts were created using registration month and user activity at:

- Day 7
- Day 14
- Day 21

Retention remained relatively stable at approximately **40%–44%** across cohorts.

The **February cohort** achieved the strongest week-3 retention at **43.98%**.

## 🧪 A/B Test — Checkout UI

A two-proportion z-test was used to compare checkout conversion between the control and treatment groups.

- Control: **15.69%**
- Treatment: **16.29%**
- Z-statistic: **-0.8133**
- p-value: **0.4161**
- Significance level: **0.05**

Because the p-value is greater than 0.05, the null hypothesis is not rejected. The observed difference is not statistically significant.

## 📈 Tableau Dashboards

### 1. RappiPlus Executive Overview

Includes:

- Adjusted Revenue
- Adjusted Cost
- Adjusted Profit
- Average Order Value
- Average Items per Order
- Monthly Revenue & Profit
- YTD Revenue
- Revenue & Profit by Category
- Date and Country filters

### 2. RappiPlus Order & Product Detail

Includes:

- Units Sold by Product
- Product-level Quantity, Cost, Revenue, and Profit
- Conditional profit formatting
- Date, Country, Product Category, and Product filters

Both dashboards are combined in the **RappiPlus Business Performance Story**.

## 💡 Key Business Insights

1. **Extreme-quantity records materially distort the raw financial picture.** The adjusted view is more useful for understanding typical order behavior.
2. **Monthly adjusted revenue and profit remain relatively stable**, supporting a more consistent operating picture than the raw dataset suggests.
3. **Home, Electronics, and Fashion contribute similar revenue and profit**, with no single category overwhelmingly dominating the adjusted results.
4. **Vacuum-Pro-Black leads unit sales**, while product-level profitability varies considerably.
5. **The main conversion opportunity appears between checkout and payment information.**
6. **Retention is stable rather than rapidly declining**, with week-3 retention remaining above 40% across all observed cohorts.
7. **The tested checkout UI change should not be considered a proven conversion improvement** based on the current experiment.

## 🛠️ Tools & Skills

- **Python:** Pandas, data cleaning, validation, exploratory analysis
- **SQL:** funnel analysis, cohort retention, conditional aggregation
- **Statistics:** two-proportion z-test, hypothesis testing
- **Tableau:** KPI dashboards, filters, interactive views, business storytelling
- **Business Analysis:** KPI definition, data interpretation, profitability analysis, decision-oriented recommendations

## 📂 Repository Structure

```text
rappiplus-business-performance-analysis/
│
├── README.md
├── RappiPlus_Business_Performance_Portfolio.ipynb
├── requirements.txt
│
└── images/
    ├── executive_overview.png
    └── order_product_detail.png
```

## 🔐 Reproducibility Note

The SQL portion was originally executed using a TripleTen training database. Database credentials are intentionally excluded from this public repository.

The public notebook keeps the SQL queries for demonstration purposes and can use the environment variable:

```text
RAPPIPLUS_DATABASE_URL
```

if a valid PostgreSQL connection is available.

## 📎 Project Context

This was developed as the final project of the **TripleTen Data Analyst Bootcamp**, integrating the main tools and analytical techniques used throughout the program into a single business case.
