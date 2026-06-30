# Olist-ECommerce-Customer-Insights-Dashboard
# Olist E-Commerce Analytics Dashboard 📊

An enterprise-grade, multi-page Power BI dashboard engineered using the Olist Brazilian E-Commerce dataset. This project translates raw transactional retail data into high-impact, actionable business intelligence across marketing, operations, and customer experience domains.

## 🔗 Project Architecture
- **Data Model:** Optimized Star Schema Architecture (Fact & Dimension Tables) with Type 1/Type 2 SCD principles.
- **Interactivity:** Fully dynamic filtering utilizing a centralized **Page Navigator** and custom state-reset mechanisms via **Power BI Bookmarks**.

---

## 🚀 Key Dashboard Pages & Strategic Insights

### 1. Executive Overview
- **Objective:** Provide C-suite executives with a macro-lens view of the business health, revenue streams, and high-level growth trajectory.
- **Metrics Tracked:** Total Revenue, Gross Order Volume, Regional Sales Leaderboards, and Category-wise Revenue distribution.

### 2. Campaign Analytics
- **Objective:** Empower marketing teams to audit and fine-tune ad spend, customer acquisition efficiency, and conversion funnels.
- **Metrics Tracked:** Customer Acquisition Cost (CAC), Return on Ad Spend (ROAS), and Marketing Channel Efficiency.

### 3. Customer Insights & Logistics Performance
- **Objective:** Analyze post-purchase consumer behavior, product affinity, operational bottleneck identification, and fulfillment health.
- **Metrics Tracked:** - **Customer Lifetime Value (CLV) & Average Order Value (AOV):** Tracks long-term consumer equity against single-transaction values.
  - **Fulfillment Success Rate %:** Evaluates operational efficiency by monitoring successfully delivered vs. canceled/delayed orders.
  - **Order Value Distribution:** A segmented histogram categorization ($0-$50, $50-$100, etc.) providing insight into price-point concentration.
  - **Logistical Service Level Agreement (SLA) Tracking:** Dual-gauge tracking system highlighting Average Delivery Lead Time vs. a strict 7-day organizational benchmark alongside Customer Satisfaction (CSAT) trends.

---

## 📸 Dashboard Previews

### Customer Insights Tab
![Customer Insights Dashboard](<img width="1007" height="777" alt="Customer Dashboard" src="https://github.com/user-attachments/assets/a3a08d29-e1fb-4b7b-b93c-3fdcac31e1f7" />
)


---

## 🛠️ Advanced DAX Formulations Built

Here are examples of production-ready, context-aware DAX measures written for this project:

### 🔄 Repeat Buyer Ratio %
*Captures business health by tracking customer retention strategies.*
```dax
Repeat Buyer Ratio = 
DIVIDE(
    CALCULATE(
        DISTINCTCOUNT(FACT_ORDERS[CUSTOMER_ID]), 
        FILTER(
            VALUES(FACT_ORDERS[CUSTOMER_ID]), 
            COUNT(FACT_ORDERS[ORDER_ID]) > 1
        )
    ), 
    DISTINCTCOUNT(FACT_ORDERS[CUSTOMER_ID])
)
