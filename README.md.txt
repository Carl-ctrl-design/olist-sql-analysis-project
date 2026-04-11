# 🛒 Olist Brazilian E-Commerce SQL Analysis

## Project Overview
End-to-end SQL analysis of 100,000+ real e-commerce transactions 
from Olist, Brazil's largest online marketplace. This project 
demonstrates intermediate-to-advanced PostgreSQL skills applied 
to real business questions across sales, logistics, customer 
behavior, and geographic performance.

**Tools Used:** PostgreSQL 17 | pgAdmin 4 | GitHub  
**Dataset:** [Brazilian E-Commerce Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)  
**Period Covered:** September 2016 — August 2018  
**Total Records Analyzed:** 100,000+ orders across 9 relational tables

---

## Database Schema
The database contains 9 relational tables:

| Table | Records | Description |
|---|---|---|
| customers | 99,441 | Customer info and location |
| orders | 99,441 | Core order lifecycle data |
| order_items | 112,650 | Products within each order |
| order_payments | 103,886 | Payment details per order |
| order_reviews | 100,000 | Customer satisfaction scores |
| products | 32,951 | Product catalog and categories |
| sellers | 3,095 | Seller information |
| category_translation | 71 | Portuguese to English categories |

---

## Business Questions Answered

### 1. Monthly Revenue Trend
- Platform grew from $46,566 in Oct 2016 to peak of $1,153,528 in Nov 2017
- Total growth of 2,378% in 13 months
- November seasonality driven by Brazilian Black Friday
- **SQL concepts:** JOIN, SUM, EXTRACT, GROUP BY, ORDER BY

### 2. Top Product Categories by Revenue
- bed_bath_table is #1 at $1,692,714 across 9,272 orders
- computers category has highest avg order value at $1,271.63
- High revenue does not equal high satisfaction (see Q6 cross-analysis)
- **SQL concepts:** Multiple JOINs, COALESCE, HAVING, AVG

### 3. Top 10 Sellers by Revenue
- Top seller (Guariba, SP) generated $226,988 across 1,124 orders
- Two distinct seller models: high volume/low price vs low volume/high price
- SP state dominates top sellers list
- **SQL concepts:** CTE, RANK(), Window Functions, aliases

### 4. Average Delivery Time by Seller
- Fastest seller delivers in 5.0 days (Santo Andre, SP)
- SP sellers have structural logistics advantage
- Maua seller achieved 100% on-time delivery rate
- **SQL concepts:** Date arithmetic, EXTRACT(EPOCH), CASE WHEN, FILTER

### 5. Payment Method Preferences
- Credit card dominates at 75.2% of transactions ($12,542,084)
- Average credit card installments: 3.5 months
- Boleto essential at 19.5% for unbanked customers
- **SQL concepts:** CASE WHEN pivot, NULLIF, SUM OVER(), casting

### 6. Review Scores by Category
- Highest rated: books_general_interest (4.51/5.0)
- Lowest rated: office_furniture (3.52/5.0)
- bed_bath_table is #1 revenue but only 3.92 review score
- **SQL concepts:** Subquery, benchmark comparison, NULLIF, HAVING

### 7. Repeat Purchase Customers
- 97.0% of customers are one-time buyers (90,556 customers)
- Only 228 loyal customers (3+ orders) — 0.2% of base
- Loyal customers spend 3.15x more ($506.79 vs $160.76)
- Converting 10% of one-time buyers = ~$1.18M additional revenue
- **SQL concepts:** Multiple CTEs, customer_unique_id, segmentation

### 8. Churn Risk Customers
- All customers classified as Lost (dataset ends 2018, now 2026)
- Query logic is production-ready for live database deployment
- Avg lifetime value per customer: $165.20
- **SQL concepts:** CURRENT_DATE, INTERVAL, date-based filtering

### 9. Month over Month Revenue Growth
- Peak MoM growth: Jan 2017 at +649,979% (recovery from Dec anomaly)
- Most meaningful peak: Nov 2017 at +53.6% (Black Friday effect)
- Platform matured to stable 5-15% monthly growth by 2018
- **SQL concepts:** LAG() window function, MoM calculation, NULLIF

### 10. Revenue by State
- SP dominates at 37.4% of total revenue ($5,769,081)
- Top 3 states (SP+RJ+MG) = 62.5% of all revenue
- Remote states pay $100 more per order but wait 3x longer
- Northern states represent untapped growth opportunity
- **SQL concepts:** DENSE_RANK(), geographic aggregation, revenue share

---

## Key Business Insights

### Insight 1 — Retention Crisis
97% of customers never return after their first purchase.
Loyal customers spend 3x more. Converting just 10% of 
one-time buyers would generate $1.18M in additional revenue.
**Recommendation:** Implement loyalty program and email 
remarketing campaigns targeting one-time buyers.

### Insight 2 — Geographic Concentration Risk  
62.5% of revenue comes from just 3 states in Southeast Brazil.
Northern states have avg delivery times 3x longer than SP
but avg order values $100 higher — proving demand exists.
**Recommendation:** Invest in northern logistics infrastructure
to unlock underserved high-willingness-to-pay markets.

### Insight 3 — Revenue vs Satisfaction Disconnect
bed_bath_table is #1 in revenue ($1.69M) but scores only
3.92/5.0 in reviews — below platform average.
office_furniture has 25% low-score rate across 1,664 reviews.
**Recommendation:** Quality audit for underperforming categories
before satisfaction drives customers to competitors.

### Insight 4 — Seasonal Revenue Pattern
November consistently spikes due to Brazilian Black Friday.
December drops sharply post-holiday.
**Recommendation:** Begin marketing campaigns in October to
maximize Black Friday revenue capture every year.

---

## SQL Concepts Demonstrated
- SELECT, WHERE, ORDER BY, LIMIT
- GROUP BY with aggregate functions (SUM, COUNT, AVG, MIN, MAX)
- INNER JOIN across multiple tables simultaneously
- Common Table Expressions (CTEs) — single and chained
- Window Functions: RANK(), DENSE_RANK(), LAG(), SUM OVER()
- CASE WHEN for categorization and pivot tables
- Date arithmetic with EXTRACT(EPOCH), INTERVAL, CURRENT_DATE
- COALESCE and NULLIF for NULL handling
- Subqueries for benchmark comparison
- HAVING for post-aggregation filtering
- Data type casting (::NUMERIC)
- FILTER (WHERE) for conditional aggregation

---

## Project Structure
```
olist-sql-project/
├── data/                         ← CSV source files (not pushed to GitHub)
├── queries/
│   ├── 01_exploration.sql
│   ├── 02_monthly_revenue.sql
│   ├── 03_top_categories.sql
│   ├── 04_top_sellers.sql
│   ├── 05_delivery_time.sql
│   ├── 06_payment_methods.sql
│   ├── 07_review_scores.sql
│   ├── 08_repeat_customers.sql
│   ├── 09_churn_risk.sql
│   ├── 10_mom_revenue_growth.sql
│   └── 11_revenue_by_state.sql
└── README.md
```

---

## Author
**Carl Waiti**  
BSc Economics and Finance | Kenyatta University  
Google Data Analytics Professional Certificate  
[LinkedIn](https://www.linkedin.com/in/carl-waiti) | [Portfolio](https://carl-ctrl-design.github.io/C.Waiti)