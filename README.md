# Brazilian E-Commerce Business Analysis — Olist

## Project Overview

This project analyzes the **Brazilian E-Commerce Public Dataset by Olist**, a real-world anonymized e-commerce dataset containing approximately 99,000 orders and related information about customers, products, sellers, payments, reviews, and deliveries.

The objective is to understand business performance from multiple perspectives, including:

- Sales and order trends
- Customer purchasing behavior
- Product and category performance
- Delivery and logistics performance
- Seller performance
- Payment behavior
- Customer satisfaction
- Geographic differences

The analysis combines data cleaning, exploratory data analysis (EDA), business metrics, segmentation, and visualization to identify actionable business insights.

---

## Business Problem

An e-commerce marketplace needs to understand how sales performance, customer behavior, delivery operations, seller performance, and customer satisfaction interact.

The key business questions addressed in this project are:

1. How did sales and order volume change over time?
2. Which product categories contributed the most sales value?
3. How concentrated is the customer base?
4. What payment methods are most commonly used?
5. How well does the marketplace perform against estimated delivery dates?
6. Which sellers and geographic regions show higher delivery risk?
7. How is delivery performance associated with customer satisfaction?
8. What areas provide opportunities for improving customer retention and operational performance?

---

## Objectives

- Perform end-to-end exploratory data analysis on a real e-commerce dataset.
- Identify important sales and customer behavior patterns.
- Measure delivery performance using actual versus estimated delivery dates.
- Analyze product, category, seller, and geographic performance.
- Investigate the relationship between delivery experience and customer reviews.
- Translate analytical findings into practical business recommendations.
- Build a portfolio project demonstrating business-oriented data analysis.

---

## Dataset

**Dataset:** Brazilian E-Commerce Public Dataset by Olist

The dataset contains approximately 100,000 orders from the Brazilian e-commerce marketplace Olist, covering orders placed primarily between 2016 and 2018.

The project uses the following related datasets:

- Customers
- Orders
- Order Items
- Order Payments
- Order Reviews
- Products
- Sellers
- Geolocation
- Product Category Translation

### Dataset Source

Kaggle — Brazilian E-Commerce Public Dataset by Olist

https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

### Dataset License

The dataset is distributed under the **CC BY-NC-SA 4.0** license.

Dataset attribution and licensing requirements should be respected when redistributing or publishing the dataset.

---

## Tools & Technologies

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Jupyter Notebook**
- Exploratory Data Analysis
- Data Cleaning
- Business KPI Analysis
- Statistical reasoning
- Data Visualization

---

## Dataset Relationships

The main relationships between the datasets are:

```text
Customers
    │
    │ customer_id
    ▼
Orders
    │
    ├──────────────► Order Payments
    │
    ├──────────────► Order Reviews
    │
    ▼
Order Items
    │
    ├──────────────► Products
    │
    └──────────────► Sellers

Products
    │
    └──────────────► Product Category Translation
```

Geolocation data provides additional geographic information for customers and sellers.

---

# Data Preparation

The analysis included several data-quality and preparation steps.

### Data Quality Checks

The following checks were performed:

- Missing-value analysis
- Duplicate-row analysis
- Data-type validation
- Order-status validation
- Date consistency checks
- Missing delivery-date investigation
- Category translation validation

The orders dataset contained no duplicate rows.

Missing delivery dates were not blindly removed because their presence is related to order status and can provide useful business information.

### Date Transformation

Order timestamp fields were converted to datetime format to support:

- Delivery duration calculations
- Estimated delivery duration
- Delivery delay analysis
- Monthly sales trends
- Monthly delivery-performance analysis

### Derived Metrics

Several business metrics were created:

```text
Delivery Days
Estimated Delivery Days
Delivery Delay Days
Delivery Performance
Purchase Month
Average Order Value (AOV)
Late Delivery Rate
Customer Purchase Frequency
```

### Delivery Performance Classification

Orders were classified as:

```text
Early      → Delivered before estimated date
On Time    → Delivered on estimated date
Late       → Delivered after estimated date
Not Delivered → No customer delivery date available
```

---

# Key Performance Indicators

| KPI | Value |
|---|---:|
| Total Orders | 99,441 |
| Delivered Orders | 96,478 |
| Unique Customers | 96,096 |
| Delivered Sales Value | 13.22M |
| Delivered AOV | 137.04 |
| Average Delivery Time | 12.09 days |
| Late Delivery Rate | 6.77% |
| Average Review Score | 4.09 / 5 |
| Repeat Customer Rate | 3.12% |

> **Important:** Product `price` is used as a sales-value / GMV proxy in this project. It should not be interpreted as accounting revenue or profit because the dataset does not contain sufficient information to calculate true revenue or profitability.

---

# Key Business Insights

## 1. Sales Performance

Delivered product sales value increased substantially during the observed period.

Several major business months reached close to **1 million** in delivered product sales value, including:

- November 2017 — approximately 1.01M
- April 2018 — approximately 1.00M
- May 2018 — approximately 1.00M
- March 2018 — approximately 0.98M
- January 2018 — approximately 0.95M

Average Order Value remained relatively stable across major business months, generally around **125–150**.

This suggests that the observed increase in sales value appears to have been influenced substantially by order volume rather than by large increases in average order value.

Partial months at the beginning and end of the dataset were excluded when making meaningful monthly comparisons.

---

## 2. Delivery Performance

Among all orders:

- **89.15%** were delivered earlier than the estimated date.
- **1.30%** were delivered exactly on the estimated date.
- **6.57%** were delivered late.
- **2.98%** did not have a customer delivery date and were classified separately as Not Delivered.

When considering only delivered orders, the late-delivery rate was **6.77%**.

Among late orders:

- Median delay was approximately **7 days**.
- Average delay was approximately **10.62 days**.
- Maximum observed delay was **188 days**.

### Monthly Risk Pattern

Delivery performance varied considerably by month.

Among months with at least 1,000 orders, **March 2018** recorded an observed late-delivery rate of approximately **18.42%** across 7,211 orders.

This suggests a potential seasonal, operational, or logistics-related issue that would warrant further investigation.

The analysis does not establish the underlying cause.

---

## 3. Customer Behavior

The dataset contained **96,096 unique customers**.

Customer purchase frequency showed a strong concentration of one-time purchases:

- **93,099 customers** placed one order.
- **2,997 customers** placed multiple orders.
- **96.88%** were one-time customers.
- **3.12%** placed multiple orders.
- Repeat customers averaged approximately **2.12 orders**.
- The highest observed customer placed **17 orders**.

This indicates an opportunity to investigate customer retention and repeat-purchase strategies.

> The 3.12% figure represents observed repeat purchasing within this historical dataset. It should not be interpreted as a formal retention rate.

---

## 4. Customer Geographic Distribution

Customer activity was geographically concentrated.

The largest customer bases were:

| State | Share of Unique Customers |
|---|---:|
| São Paulo (SP) | 41.92% |
| Rio de Janeiro (RJ) | 12.88% |
| Minas Gerais (MG) | 11.71% |
| Rio Grande do Sul (RS) | 5.49% |
| Paraná (PR) | 5.08% |

São Paulo alone represented approximately **42% of unique customers**.

This concentration is important when evaluating regional sales, logistics, fulfillment capacity, and marketing opportunities.

---

## 5. Product & Category Performance

Category performance varied across sales value, order volume, and order-based AOV.

### Top Categories by Delivered Sales Value

| Category | Delivered Sales Value |
|---|---:|
| Health & Beauty | 1.23M |
| Watches & Gifts | 1.17M |
| Bed, Bath & Table | 1.02M |
| Sports & Leisure | 0.95M |
| Computers & Accessories | 0.89M |

Health & Beauty generated the highest delivered sales value among categories.

Bed, Bath & Table recorded the highest number of delivered orders, with approximately **9,272 orders**.

Watches & Gifts generated approximately **1.17M** in delivered sales value from 5,495 delivered orders and had an order-based AOV of approximately **212.23**.

These results show that category performance is influenced by both order volume and value per order.

### Product Concentration

The top 10 products by delivered sales value contributed approximately **3.35%** of total delivered product sales value.

This indicates that delivered sales value was relatively distributed across products rather than being dominated by a very small number of products.

---

## 6. Payment Behavior

Credit card was the dominant payment method.

| Payment Type | Share of Payment Records |
|---|---:|
| Credit Card | 73.92% |
| Boleto | 19.04% |
| Voucher | 5.56% |
| Debit Card | 1.47% |
| Not Defined | 0.003% |

Approximately **66.85% of credit-card payment records used multiple installments**, while approximately 33.15% used a single installment.

> Payment-method percentages are based on payment records, not unique customers or unique orders. A single order can contain multiple payment records.

---

## 7. Customer Satisfaction

The overall average review score was:

**4.09 / 5**

Review distribution:

- 5 stars — **57.78%**
- 4–5 stars — **77.07%**
- 1–2 stars — **14.69%**
- 3 stars — **8.24%**

Although the overall review profile was positive, the meaningful low-rating segment provides an opportunity to investigate recurring customer-experience problems.

---

# Delivery Performance & Customer Satisfaction

One of the strongest patterns in the analysis was the relationship between delivery performance and customer review scores.

### Average Review Score by Delivery Performance

| Delivery Performance | Average Review |
|---|---:|
| Early | 4.29 |
| On Time | 4.03 |
| Late | 2.27 |
| Not Delivered | 1.76 |

Among late orders:

- **53.73%** received a 1-star review.

Among orders classified as Not Delivered:

- **70.33%** received a 1-star review.

This indicates a strong association between delivery problems and lower customer satisfaction.

> These results show association, not causation.

---

# Delivery Duration & Customer Satisfaction

Customer satisfaction also declined as actual delivery duration increased.

| Delivery Time | Average Review |
|---|---:|
| 1–3 days | 4.46 |
| 4–7 days | 4.39 |
| 8–14 days | 4.29 |
| 15–21 days | 4.10 |
| 22–30 days | 3.49 |
| 31+ days | 2.18 |

Orders delivered within 1–3 days had an average review score of approximately **4.46**, compared with approximately **2.18** for orders taking 31+ days.

The difference is approximately **2.28 review points**.

This is a strong observed association and highlights delivery duration as an important customer-experience metric.

---

# Seller Performance

Seller performance varied considerably across:

- Sales value
- Order volume
- Average Order Value
- Delivery time
- Late-delivery rate
- Customer review score

Among sellers with at least **100 delivered orders**, the highest observed late-delivery rate was approximately **19.02%**.

A minimum-order threshold was applied to reduce misleading results from sellers with very small sample sizes.

Seller-level analysis also found a moderate negative Pearson correlation between late-delivery rate and average review score:

**r = -0.446**

This indicates that sellers with higher observed late-delivery rates tended to have lower average review scores within the filtered seller population.

> Correlation does not establish causation.

---

# Geographic & Logistics Analysis

Geographic differences were observed in delivery performance.

Among customer states with at least 1,000 delivered orders:

- Ceará (CE) had an observed late-delivery rate of approximately **13.64%**.
- Paraná (PR) had an observed late-delivery rate of approximately **3.99%**.
- São Paulo (SP), with more than 40,000 delivered orders, had an observed late-delivery rate of approximately **4.44%**.

### Same-State vs Interstate Shipments

| Shipment Type | Avg Delivery | Late Rate |
|---|---:|---:|
| Same State | 7.46 days | 4.45% |
| Interstate | 14.62 days | 7.95% |

Interstate shipments took approximately **7.17 days longer on average** and had a higher observed late-delivery rate than same-state shipments.

These geographic differences describe observed patterns in the dataset and do not establish that location itself causes delivery delays.

---

# Key Visualizations

The project includes visual analysis covering:

1. Monthly Delivered Sales Value
2. Order Delivery Performance
3. Top 10 Product Categories by Sales Value
4. Delivery Time vs Customer Satisfaction
5. Customer Purchase Frequency
6. Customer Geographic Distribution
7. Payment Method Distribution
8. Customer Review Score Distribution
9. Seller Late-Delivery Performance
10. Late Delivery Rate by Customer State

These visualizations are included in the Jupyter Notebook.

---

# Business Recommendations

## 1. Improve Delivery Performance

Late deliveries were associated with substantially lower customer review scores.

Recommended actions:

- Monitor late-delivery rate monthly.
- Identify orders approaching their estimated delivery date.
- Investigate operational bottlenecks during high-volume periods.
- Track delivery performance by seller, region, and route.

---

## 2. Focus on High-Risk Geographic Routes

Interstate shipments showed longer average delivery times and higher observed late-delivery rates.

Recommended actions:

- Identify routes with consistently high late-delivery rates.
- Review logistics capacity on high-risk routes.
- Evaluate regional fulfillment opportunities.
- Monitor geographic delivery KPIs continuously.

---

## 3. Monitor Seller Delivery Performance

Seller delivery performance varied considerably.

Recommended actions:

- Create seller-level delivery dashboards.
- Track late-delivery rate, average delivery time, and order volume together.
- Investigate consistently underperforming sellers.
- Recognize sellers with strong operational performance.

Seller comparisons should use minimum order thresholds to avoid misleading small-sample results.

---

## 4. Improve Customer Retention

Approximately 96.88% of observed unique customers placed only one order.

Recommended actions:

- Develop targeted repeat-purchase campaigns.
- Recommend related products after purchases.
- Offer incentives for subsequent purchases.
- Segment customers based on purchasing behavior.
- Investigate whether delivery experience is associated with repeat purchasing.

---

## 5. Protect Customer Satisfaction

Delivery problems were strongly associated with lower customer review scores.

Recommended actions:

- Prioritize delayed orders for customer communication.
- Provide accurate delivery estimates.
- Notify customers proactively about delays.
- Analyze low-rated orders for recurring problems.
- Monitor customer satisfaction alongside delivery KPIs.

---

## 6. Monitor Category Performance

Category performance should not be evaluated using sales value alone.

Recommended actions:

- Track category sales value.
- Monitor order volume.
- Track category-level AOV.
- Identify high-volume categories.
- Identify high-value categories for targeted merchandising.

---

## 7. Use Multiple KPIs

A single KPI can hide important business patterns.

The recommended performance framework includes:

- Sales value
- Order volume
- Average Order Value
- Delivery time
- Late-delivery rate
- Customer review score
- Repeat-purchase behavior

Using multiple KPIs provides a more complete view of marketplace performance.

---

# Limitations

This analysis has several important limitations:

1. **Historical dataset**  
   The dataset primarily represents orders from 2016–2018 and may not represent current e-commerce behavior.

2. **Revenue and profit are not directly available**  
   Product price is used as a sales-value/GMV proxy. True accounting revenue, costs, margins, and profit cannot be calculated from the available data.

3. **Correlation is not causation**  
   Observed relationships between delivery performance and reviews do not prove that delivery performance alone caused lower ratings.

4. **Repeat purchasing is not formal retention**  
   The repeat-customer calculation is based on observed purchases within the dataset period.

5. **Partial months**  
   Some months at the beginning and end of the dataset contain very few observations and were excluded from meaningful trend comparisons.

6. **Sample-size effects**  
   Minimum observation thresholds were used when comparing sellers, routes, states, and categories.

7. **Unobserved factors**  
   Factors such as promotions, inventory availability, carrier performance, customer demographics, and external events may influence observed outcomes but are not fully captured in the dataset.

---

# Future Analysis

The next stage of this portfolio will extend the analysis into statistical and analytical techniques such as:

- Hypothesis testing
- Confidence intervals
- Statistical comparison of delivery groups
- Correlation analysis
- Regression analysis
- Customer segmentation
- Predictive analysis
- SQL-based business analysis
- ETL pipeline development
- Interactive Power BI dashboard

The statistical analysis will investigate whether important observed patterns are statistically significant rather than relying only on descriptive EDA.

---

# Project Structure

```text
01_EDA_Olist_Ecommerce_Analysis/
│
├── README.md
│
├── 01_EDA_Olist_Ecommerce_Analysis.ipynb
│
├── data/
│   └── Olist dataset files
│
└── visualizations/
    └── exported charts
```

> The raw dataset is not included in the repository if its redistribution conflicts with the dataset license. The source link above can be used to download the original data.

---

# How to Run

### 1. Clone the repository

```bash
git clone <your-github-repository-url>
```

### 2. Install required libraries

```bash
pip install pandas numpy matplotlib jupyter
```

### 3. Download the dataset

Download the Olist dataset from Kaggle:

https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

Place the CSV files inside the project's `data/` directory.

### 4. Open the notebook

```bash
jupyter notebook
```

Open:

```text
01_EDA_Olist_Ecommerce_Analysis.ipynb
```

Update the data paths if required and run the notebook.

---

# Skills Demonstrated

This project demonstrates practical experience in:

- Exploratory Data Analysis
- Data Cleaning
- Data Quality Validation
- Data Transformation
- Business KPI Development
- Customer Analysis
- Sales Analysis
- Product & Category Analysis
- Seller Analysis
- Delivery & Logistics Analysis
- Geographic Analysis
- Customer Satisfaction Analysis
- Correlation Analysis
- Data Visualization
- Business Insight Generation
- Business Recommendations
- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook

---

# Final Business Takeaway

The analysis shows substantial sales activity across the observed period, with sales value influenced substantially by order volume while average order value remained relatively stable across major business months.

The strongest business relationships identified were between:

```text
Delivery Performance
        ↓
Customer Satisfaction
```

and

```text
Seller / Geographic Factors
        ↓
Delivery Performance
```

At the same time, the high proportion of one-time customers highlights an opportunity to investigate repeat purchasing and customer retention.

The next stage of analysis will use statistical methods to test whether the key patterns observed during EDA are statistically significant.

---

## Author

**Shilpa Daji Bele**

Data Analyst Portfolio Project

Skills: Python | SQL | Excel | Power BI | Data Analysis
