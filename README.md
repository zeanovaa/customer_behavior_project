# 🛍️ Fashion Customer Behavior Analysis

End-to-End Data Analysis Project: From raw data processing in Python to SQL-based exploration and Power BI visualization.

---

## **Project Overview**

This project analyzes transactional data from 3,900 retail customers to uncover hidden patterns in shopping behavior. The primary goal was to assist the marketing team in understanding revenue drivers, evaluating the effectiveness of the subscription model, and identifying customer segments for targeted campaigns.

**Key Highlight:**

Discovered that Male customers contribute 68% of total revenue, challenging the initial assumption that the primary target audience was female. Additionally, identified that the current Subscription Model fails to increase Average Order Value (AOV), prompting a strategic recommendation for restructuring.

---

## **Repository Structure**

```
├── customer_shopping_behavior.csv   # Raw dataset
├── power-bi-project.ipynb              # Python script for cleaning & feature engineering
├── customer_behavior.sql             # SQL scripts for business questions
├── customer_behavior_dashboard.pbix # Power BI file
└── README.md
```

---

## **Dashboard Preview**

<img width="1570" height="857" alt="image" src="https://github.com/user-attachments/assets/bcea019b-8982-4621-b919-c4ec694c88df" />

---

## **Business Problem**

A leading retail company noticed a shift in purchasing patterns but lacked granular insights to explain the "Why."

**Objectives:**

- **Revenue Drivers:** Identify which demographics and categories drive the most sales.
- **Loyalty Assessment:** Evaluate if "Subscribers" are actually more profitable than regular customers.
- **Customer Segmentation:** Group customers based on purchasing history to improve retention.

---

## **Tech Stack & Workflow**

### 1. Data Cleaning & Feature Engineering (Python/Pandas)

Before analysis, the raw data required processing:

- **Missing Values:** Imputed 37 missing Review Rating values using the median rating of their respective categories.
- **Redundancy Removal:** Dropped Promo Code Used column as it had 100% correlation with Discount Applied.

**Feature Engineering:**

- Created age_group (Young Adult, Adult, Middle-Aged, Senior) using quartile binning.
- Converted Frequency of Purchases into numeric purchase_frequency_days for statistical analysis.

### 2. Exploratory Data Analysis (SQL - PostgreSQL)

Executed complex SQL queries to answer business questions.

- **Aggregations:** Calculated revenue per gender, category, and shipping type.
- **Segmentation Logic:** Used CASE WHEN to categorize customers into New, Returning, and Loyal.
- **Sub-queries:** Identified high-value customers who used discounts.

### 3. Visualization (Power BI)

Built an interactive dashboard to track:

- Total Customers & Revenue ($).
- Demographics breakdown (Gender, Age).
- Correlation between Shipping Type and Purchase Amount.

---

## **Key Insights & Findings**

### 1. The Gender Revenue Gap

Contrary to typical fashion retail trends, men are the biggest spenders.

- **Male Revenue:** $157,890 (67.7%)
- **Female Revenue:** $75,191 (32.3%)

**Action:** Marketing budget should be reallocated to target men more aggressively with "Essential Bundles."

### 2. The Subscription Paradox

The loyalty program is not driving higher spending.

- **Subscribers AOV:** $59.49
- **Non-Subscribers AOV:** $59.87

**Insight:** Subscribers are likely signing up just for discounts, not out of brand loyalty.

**Action:** Restructure subscription benefits (e.g., offer Free Express Shipping only for orders >$75) to force an increase in basket size.

### 3. High Customer Loyalty

80% of customers (3,116 users) are classified as "Loyal" (>10 purchases).

**Action:** Shift focus from "User Acquisition" to "retention & Upselling" to prevent churn in this mature user base.

---

## **Sample SQL Code**

Here is a snippet of the SQL query used for Customer Segmentation:

```
WITH customer_type AS (
 SELECT customer_id, previous_purchases,
 CASE
 WHEN previous_purchases = 1 THEN 'New'
 WHEN previous_purchases BETWEEN 2 AND 10 THEN 'Returning'
 ELSE 'Loyal'
 END AS customer_segment
 FROM customer
)
SELECT customer_segment, COUNT(DISTINCT customer_id) as total_customer
FROM customer_type
GROUP BY customer_segment;
```

---

## **Recommendations**

- Launch "Men's Edit" Campaign: Since men drive 68% of sales, create curated collections specifically for this demographic.
- Tiered Subscription Model: Stop giving flat discounts. Introduce tiers where benefits scale with spending to boost the stagnant AOV.
- Promote Express Shipping: Data shows Express users spend more ($60.48) than Standard users ($58.46). Highlight express options at checkout for high-value items.

---

## **Acknowledgements & Credits**

This project was developed based on the comprehensive tutorial and dataset provided by Amlan Mohanty.

- **Concept & Data Source:** Amlan Mohanty  
- **Implementation & Analysis:** Humaira Zeanova

---

## **Contact**

- **Name:** Humaira Zeanova  
- **LinkedIn:** https://www.linkedin.com/in/humairazeanova  
- **Email:** zeanovahumaira@gmail.com
- **Portfolio:** https://zeanovaa.github.io/portfolio

---
