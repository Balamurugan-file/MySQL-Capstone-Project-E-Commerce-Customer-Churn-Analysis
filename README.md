# E-Commerce Customer Churn Analysis

## Overview
This project analyzes customer churn behavior in an e-commerce platform using MySQL.
It covers end-to-end data handling - from cleaning raw data to running business-focused
queries that uncover churn patterns and customer behavior insights.

---

## Problem Statement
E-commerce businesses lose revenue when customers stop purchasing. This project uses
historical transactional data to identify churn drivers - such as tenure, payment
preferences, satisfaction scores, and complaint history - and surface actionable
insights for retention strategies.

---

## Dataset
- **Source:** E-Commerce Customer Churn Dataset
- **Rows:** ~5,630 customer records
- **Key Columns:** Tenure, PreferredPaymentMode, SatisfactionScore, CouponUsed,
  OrderCount, WarehouseToHome, Churn, Complain, CityTier

---

## Project Workflow

### 1. Data Cleaning
- Imputed missing values using **mean** - `WarehouseToHome`, `HourSpendOnApp`,
  `OrderAmountHikeFromlastYear`, `DaySinceLastOrder`
- Imputed missing values using **mode** - `Tenure`, `CouponUsed`, `OrderCount`
- Removed outlier rows where `WarehouseToHome > 100`
- Standardized inconsistent labels:
  - `Phone` → `Mobile Phone`
  - `COD` → `Cash on Delivery`
  - `CC` → `Credit Card`

### 2. Data Transformation
- Renamed columns:
  - `PreferedOrderCat` → `PreferredOrderCat`
  - `HourSpendOnApp` → `HoursSpentOnApp`
- Created derived columns:
  - `ChurnStatus` - `"Churned"` or `"Active"` based on Churn flag
  - `ComplaintReceived` - `"Yes"` or `"No"` based on Complain flag
- Dropped raw flag columns: `Churn`, `Complain`

### 3. Data Analysis (17+ Queries)
Key business questions answered:
- Churned vs. active customer count
- Average tenure and total cashback of churned customers
- Churn rate among customers who complained
- Most preferred payment mode among active customers
- Top order categories by average cashback amount
- Customer segmentation by warehouse distance:
  - `Very Close` ≤ 5km | `Close` ≤ 10km | `Moderate` ≤ 15km | `Far` > 15km
- High-value married customers in City Tier-1 with above-average order counts
- Cross-table analysis using a `customer_returns` table

---

## Tools & Skills Used
| Tool | Usage |
| :--- | :--- |
| MySQL | DDL, DML, Aggregations, JOINs, Subqueries, CASE, GROUP BY, HAVING |
| Database | `ecomm` |

---

## Key Insights
- Identified city tiers and order categories most associated with churn
- Revealed payment modes and customer segments with higher retention rates
- Mapped churn distribution across warehouse distance categories

---

## How to Run
1. Import the dataset into MySQL as the `ecomm` database
2. Run the data cleaning and transformation scripts in order
3. Execute the analysis queries to explore churn patterns
