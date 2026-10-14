# Customer Churn Analysis — Power BI

Telecom customer churn analysis built in Power BI, covering data cleaning, star schema data modeling, and DAX-based business insights across 7,000 synthetic customer records.

##  Dashboard



![Dashboard](Customer%20Churn%20Analysis%201.pdf)



##  Business Problem

Customer retention is cheaper than acquiring new customers. This project identifies which customer segments are most likely to churn and why — enabling targeted retention strategies.

##  Data Model

Star schema with 1 dimension table and 4 fact tables:
- **Customers** (dimension) — demographics, contract type, payment method
- **Subscriptions** (fact) — plan type, monthly/total charges
- **Usage** (fact) — internet service, streaming, support add-ons
- **SupportTickets** (fact) — ticket history, resolution time
- **ChurnStatus** (fact) — churn outcome and reason

##  Data Cleaning (Power Query)

- Removed duplicate rows (primary-key based deduplication on CustomerID)
- Standardized inconsistent text casing (Gender, Churn status)
- Fixed mixed date formats across tables
- Handled missing values (conditional columns for blank ChurnReason)
- Trimmed whitespace and standardized CustomerID formatting

##  Key DAX Measures

- `Total Customers`, `Churned Customers`, `Active Customers`
- `Churn Rate` = Churned / Total Customers
- `Retention Rate` = 1 - Churn Rate
- `Churn Rate by Contract Type`, `Churn Rate by Payment Method` (using CALCULATE + ALLEXCEPT)
- `Tenure Range` — calculated column grouping customers into tenure bands

##  Key Insights

- **Contract type is the strongest churn driver**: Month-to-month customers churn at 29.1%, vs 7.0% (Two Year) and 6.8% (One Year) — a 4x difference.
- **Churn risk declines with tenure**: New customers (0-12 months) churn at ~24%, dropping steadily to ~7% for customers with 61+ months tenure.
- **Payment method has a moderate effect**: Electronic Check users churn at 20.4%, the highest among payment methods.
- **No single dominant churn reason**: Poor service quality, better offers elsewhere, price, and relocation are all roughly equally cited (~18-20% each).

##  Recommendations

1. Offer incentives to convert month-to-month customers to annual contracts.
2. Build a dedicated onboarding/support program for customers in their first 6-12 months.
3. Audit service quality and support response times — the top cited churn reason.
4. Encourage Electronic Check users to switch to automatic payment methods.

##  Tools Used

Power BI · Power Query · DAX · Python (synthetic data generation)

##  Files

- `Customer Churn Analysis.pbix` — Power BI project file
- `Customer Churn Analysis 1.pdf` — Dashboard export
