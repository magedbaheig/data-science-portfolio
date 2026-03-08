# 📬 Catalog Demand Prediction

**Multiple Linear Regression for Marketing ROI Decision**

![Excel](https://img.shields.io/badge/Excel-Analysis-green)
![Alteryx](https://img.shields.io/badge/Alteryx-Workflow-orange)
![Python](https://img.shields.io/badge/Python-Planned-lightgrey)
![KNIME](https://img.shields.io/badge/KNIME-Planned-lightgrey)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📋 Project Overview

| Aspect | Details |
|--------|---------|
| **Course** | Udacity Predictive Analytics for Business (Bertelsmann) |
| **Year** | 2021 |
| **Type** | Supervised Learning (Regression) |
| **Objective** | Predict expected profit from catalog mailing campaign |
| **Decision** | ✅ Send catalog (profit exceeds threshold) |

---

## 🛠️ Implementations

| Tool | Status | Description |
|------|--------|-------------|
| **Excel** | ✅ Complete | Regression analysis and profit calculation |
| **Alteryx** | ✅ Complete | Visual workflow for modeling |
| **Python** | 🔜 Planned | scikit-learn implementation |
| **KNIME** | 🔜 Planned | Open-source workflow replication |

---

## 🎯 Business Problem

A mail-order catalog company that manufactures and sells high-end home goods needs to decide:
- **Should they send** this year's catalog to 250 new customers?
- **Decision criteria:** Expected profit must exceed **$10,000**

### Business Context

| Factor | Value |
|--------|-------|
| **Gross Margin** | 50% |
| **Catalog Cost** | $6.50 per customer |
| **Total Mailing Cost** | $1,625 (250 × $6.50) |
| **Profit Threshold** | $10,000 |

---

## 📊 Dataset

| Dataset | Records | Purpose |
|---------|---------|---------|
| p1-customers.xlsx | ~2,375 | Train regression model |
| p1-mailinglist.xlsx | 250 | Predict sales for new customers |

### Features Analyzed

| Feature | Type | Initial Assessment |
|---------|------|-------------------|
| **Customer_Segment** | Categorical | ✅ Significant predictor |
| **Avg_Num_Products_Purchased** | Continuous | ✅ Strong predictor (R² = 0.73) |
| **City** | Categorical | ❌ Not significant |
| **Years_as_Customer** | Continuous | ❌ Not significant (P = 14.7%) |

---

## 🔧 Technical Approach

### 1. Exploratory Analysis (Simple Linear Regression)

| Variable | P-Value | R² | Conclusion |
|----------|---------|-----|------------|
| **Avg_Num_Products_Purchased** | 2.2E-16 | 0.73 | ✅ Strong predictor |
| Years_as_Customer | 14.7% | 0.0009 | ❌ Not significant |

### 2. Model Iteration

| Model | Variables | Adjusted R² | Issue |
|-------|-----------|-------------|-------|
| **1st Model** | 4 variables (all) | 0.84 | City & Years_as_Customer had high P-values |
| **2nd Model** | 2 variables | 0.84 | ✅ All variables significant |

### 3. Final Model Equation

 Y (Predicted Sales Amount) = 303.46
 + (-149.36 × Customer_Segment: Loyalty Club Only)
 + (281.84 × Customer_Segment: Loyalty Club and Credit Card)
 + (-245.42 × Customer_Segment: Store Mailing List)
 + (0 × Customer_Segment: Credit Card Only) [Base Case]
 + (66.98 × Avg_Num_Products_Purchased)


### 4. Model Validation

| Metric | Value |
|--------|-------|
| **Adjusted R²** | 0.84 |
| **P-Values** | All < 0.05 (significant) |
| **Predictive Power** | Explains 84% of sales variation |

---

## 📈 Results

### Model Performance

| Metric | Value |
|--------|-------|
| **Adjusted R²** | 0.84 |
| **Significant Predictors** | Customer_Segment, Avg_Num_Products_Purchased |
| **Variables Excluded** | City, Years_as_Customer (not significant) |

### Profit Calculation

| Step | Calculation | Value |
|------|-------------|-------|
| 1. Predicted Sales (per customer) | Apply regression equation | Varies |
| 2. Expected Sales (weighted) | Predicted × Purchase Probability | Per customer |
| 3. **Total Expected Revenue** | Sum of all expected sales | **$47,224.87** |
| 4. Gross Profit (50% margin) | Revenue × 0.50 | $23,612.44 |
| 5. Mailing Cost | 250 × $6.50 | -$1,625.00 |
| 6. **Net Expected Profit** | Gross Profit - Cost | **$21,987.44** |

### Business Recommendation

| Metric | Value | Status |
|--------|-------|--------|
| **Expected Profit** | $21,987.44 | ✅ |
| **Threshold** | $10,000.00 | — |
| **Recommendation** | **SEND CATALOG** | ✅ Exceeds threshold by $11,987 |

---

## 💡 Key Insights

| Insight | Details |
|---------|---------|
| **Best Predictor** | Avg_Num_Products_Purchased (R² = 0.73 alone) |
| **Customer Segment Impact** | "Loyalty Club and Credit Card" adds $281.84 to predicted sales |
| **Worst Segment** | "Store Mailing List" reduces predicted sales by $245.42 |
| **Non-Factors** | City and tenure (Years_as_Customer) don't affect purchase behavior |
| **ROI** | 119.8% profit above threshold ($21,987 vs $10,000 required) |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| README.md | This documentation file |
| Catalog_Report_Submission_Maged.pdf | Detailed analysis report |
| Catalog_AlteryxSolution_Submission_Maged.yxmd | Alteryx visual workflow |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Insurance Claims (Kaggle) | Regression (Python) | [Link](../kaggle-insurance-prediction/) |
| Diamond Pricing | Regression | [Link](../diamond-pricing/) |
| School Cost Prediction | Data Prep + Regression | [Link](../school-cost-prediction/) |

---

## 📜 Acknowledgments

| Entity | Contribution |
|--------|--------------|
| **Udacity** | Predictive Analytics for Business Nanodegree |
| **Bertelsmann** | Scholarship sponsorship |

---

## 👤 Author

**Maged Baheig**

| Platform | Link |
|----------|------|
| LinkedIn | [Connect](https://www.linkedin.com/in/magedbaheig) |
| Kaggle | [Profile](https://www.kaggle.com/magedbaheig) |
| GitHub | [Follow](https://github.com/magedbaheig) |
| Email | [Reach Out](mailto:magedbaheig@gmail.com) |

📍 **Location:** Cairo, Egypt

---

*Part of the [Data Science Portfolio](https://github.com/magedbaheig/data-science-portfolio/tree/main)*

