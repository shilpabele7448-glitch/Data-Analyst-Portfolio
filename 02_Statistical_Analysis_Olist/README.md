# Olist E-Commerce Statistical Analysis

## 📌 Project Overview

This project performs statistical analysis on the Brazilian E-Commerce Public Dataset by Olist to understand the relationship between delivery performance, delivery time, and customer review scores.

The analysis focuses on identifying whether differences in delivery performance are statistically associated with customer satisfaction.

The project was completed in **Microsoft Excel** using statistical analysis techniques rather than Python-based exploratory analysis.

---

## 🎯 Business Problem

For an e-commerce company, delivery experience can strongly influence customer satisfaction.

This analysis investigates:

1. Do customers give different review scores for early and late deliveries?
2. Is delivery time related to customer review scores?
3. Do average review scores differ across delivery-performance groups?
4. What statistical evidence can help identify areas for operational improvement?

---

## 📊 Dataset

**Dataset:** Brazilian E-Commerce Public Dataset by Olist

The dataset contains information about orders, customers, sellers, products, payments, reviews, and deliveries from the Brazilian e-commerce marketplace Olist.

### Key variables used

| Variable | Description |
|---|---|
| `delivery_days` | Number of days taken to deliver an order |
| `delivery_performance` | Delivery classification such as Early, On Time, or Late |
| `review_score` | Customer review score from 1 to 5 |

The analysis focuses on order-level delivery and customer review information.

---

## 🛠️ Tools & Skills

- Microsoft Excel
- Data Analysis ToolPak
- Descriptive Statistics
- Hypothesis Testing
- Welch's Two-Sample t-Test
- Correlation Analysis
- One-Way ANOVA
- Statistical Interpretation
- Business Analysis
- Data Visualization
- Business Recommendations

---

# 🔬 Statistical Analysis

## 1. Descriptive Statistics

Descriptive statistics were calculated for customer review scores.

| Metric | Result |
|---|---:|
| Mean Review Score | 4.1557 |
| Median Review Score | 5 |
| Standard Deviation | 1.2850 |
| Minimum | 1 |
| Maximum | 5 |
| Number of Reviews | 96,361 |

### Interpretation

The average review score is approximately **4.16**, while the median score is **5**.

This indicates that a large proportion of customers gave high ratings, although lower ratings contribute to the variation in scores.

---

## 2. Welch's Two-Sample t-Test

### Business Question

**Do Early and Late deliveries have different average customer review scores?**

### Hypotheses

**Null Hypothesis (H₀):**

There is no difference between the average review scores of Early and Late deliveries.

**Alternative Hypothesis (H₁):**

There is a difference between the average review scores of Early and Late deliveries.

### Significance Level

`α = 0.05`

### Results

| Metric | Early | Late |
|---|---:|---:|
| Average Review Score | 4.2731 | 2.2181 |

**p-value < 0.001**

### Conclusion

The Welch's two-sample t-test indicates a statistically significant difference in average review scores between Early and Late deliveries.

Early deliveries had a higher average review score than Late deliveries.

### Business Interpretation

Late deliveries are associated with substantially lower customer review scores.

This suggests that delivery performance is an important factor to monitor when evaluating customer experience.

> Statistical significance indicates an observed difference between the groups; it does not by itself prove that late delivery causes lower ratings.

---

# 3. Correlation Analysis

### Business Question

**Is delivery time related to customer review score?**

The Pearson correlation coefficient was calculated between:

- `delivery_days`
- `review_score`

### Result

**Correlation coefficient (r) = -0.33362**

### Interpretation

The relationship is:

- **Direction:** Negative
- **Strength:** Moderate

This means that longer delivery times tend to be associated with lower customer review scores.

However, correlation does not establish causation.

Other factors may also influence customer satisfaction.

---

# 4. One-Way ANOVA

### Business Question

**Do average customer review scores differ across Early, On Time, and Late delivery groups?**

The **Not Delivered** group was excluded from this ANOVA because it contained only a very small number of observations compared with the other groups.

### Hypotheses

**Null Hypothesis (H₀):**

The average review scores are equal across the delivery-performance groups.

**Alternative Hypothesis (H₁):**

At least one delivery-performance group has a different average review score.

### Significance Level

`α = 0.05`

### Result

**p-value < 0.001**

### Conclusion

The one-way ANOVA indicates that average review scores differ significantly across the Early, On Time, and Late delivery groups.

ANOVA establishes that a statistically significant difference exists among the group means, but it does not by itself identify every specific pair of groups that differs.

---

# 📈 Key Business Findings

### 1. Late deliveries and lower ratings

Late deliveries were associated with substantially lower average customer review scores compared with Early deliveries.

### 2. Delivery time and customer satisfaction

The negative correlation indicates that longer delivery times tend to be associated with lower review scores.

### 3. Delivery performance matters

The ANOVA result provides statistical evidence that review-score averages are not the same across the Early, On Time, and Late groups.

### 4. Customer experience monitoring

Delivery performance can be monitored alongside customer review scores as an important customer-experience KPI.

---

# 💡 Business Recommendations

Based on the statistical findings:

1. **Monitor late deliveries closely** because they are associated with substantially lower review scores.

2. **Identify delivery bottlenecks** across the fulfillment and logistics process to reduce delays.

3. **Track delivery time as a customer-experience KPI** alongside customer review scores.

4. **Investigate operational areas with higher delivery delays** to identify potential opportunities for improvement.

5. **Monitor delivery performance and customer reviews over time** to evaluate whether operational changes are associated with improvements in customer experience.

These recommendations are based on observed statistical associations and should not be interpreted as proof of causation.

---

# ⚠️ Limitations

- The analysis identifies associations and statistical differences but does not establish causation.
- The dataset represents historical Olist marketplace activity and may not represent current e-commerce behavior.
- Customer satisfaction may be influenced by factors other than delivery performance.
- The Not Delivered group was excluded from the ANOVA because of its very small sample size relative to the other groups.
- The analysis uses review scores as the customer-satisfaction measure.
- Additional factors such as product category, seller performance, payment method, freight cost, and location could be investigated in future analysis.

---

# 📁 Project Structure

```text
02_Statistical_Analysis_Olist/
│
├── Olist_Statistical_Analysis.xlsx
└── README.md
