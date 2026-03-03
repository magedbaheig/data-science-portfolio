# 🐾 Pawdacity Store Expansion Analysis

**Data Preparation & Outlier Analysis for Location Recommendation**

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
| **Type** | Data Preparation / Analytical Dataset Creation |
| **Objective** | Prepare clean dataset for store location prediction model |
| **Output** | Analysis-ready dataset with outliers handled |

---

## 🛠️ Implementations

| Tool | Status | Description |
|------|--------|-------------|
| **Excel** | ✅ Complete | Outlier analysis and statistical validation |
| **Alteryx** | ✅ Complete | Data wrangling and preparation workflow |
| **Python** | 🔜 Planned | Pandas/scikit-learn implementation |
| **KNIME** | 🔜 Planned | Open-source workflow replication |

---

## 🎯 Business Problem

Pawdacity, a leading pet store chain in Wyoming with **13 stores**, wants to expand by opening a **14th store**. The task is to:
- Prepare a clean analytical dataset
- Handle outliers appropriately
- Enable accurate sales prediction for location recommendation

### Store Selection Criteria

| Criterion | Requirement |
|-----------|-------------|
| Current Stores | No existing Pawdacity store |
| Population | > 4,000 people (2014 Census) |
| Predicted Sales | > $200,000 yearly |
| Competition | Total competitor sales < $500,000 |
| Selection | Highest predicted sales among qualifying cities |

---

## 📊 Dataset

### Original Data

| Dataset | Records | Purpose |
|---------|---------|---------|
| Training Set | 11 cities | Build regression model |
| Prediction Set | Available cities | Recommend new location |

### Features Analyzed

| Feature | Sum | Average |
|---------|-----|---------|
| **Census Population** | 213,862 | 19,442 |
| **Total Pawdacity Sales** | $3,773,304 | $343,028 |
| **Households with Under 18** | 34,064 | 3,097 |
| **Land Area** | 33,071 | 3,006 |
| **Population Density** | 63 | 5.71 |
| **Total Families** | 62,653 | 5,696 |

---

## 🔧 Technical Approach

### 1. Data Quality Assessment

| Check | Result |
|-------|--------|
| Missing Values | ✅ None found |
| Data Completeness | ✅ All records complete |
| Data Types | ✅ Appropriate for analysis |

### 2. Outlier Detection

| City | Total Sales | Status |
|------|-------------|--------|
| **Cheyenne** | $917,892 | ✅ Kept (capital city, valid data) |
| **Gillette** | $543,132 | ❌ Removed (distorts model) |

### 3. Outlier Analysis Summary

| Variable | Outliers Found | Action |
|----------|----------------|--------|
| Census Population | 1 (Cheyenne: 59,466) | Kept |
| Land Area | 1 (6,620) | Kept |
| Population Density | 1 (20.34) | Kept |
| Total Families | 1 (14,613) | Kept |
| **Total Sales** | 2 (Cheyenne, Gillette) | Removed Gillette |

### 4. Why Remove Gillette (Not Cheyenne)?

| Scenario | Best R² Achieved | Recommendation |
|----------|------------------|----------------|
| Keep All | 0.8066 | — |
| Remove Both | 0.4733 | ❌ Worse |
| Remove Cheyenne Only | 0.4655 | ❌ Worse |
| **Remove Gillette Only** | **0.8212** | ✅ Best |

---

## 📈 Predictor Variable Analysis

### After Removing Gillette Outlier

| Variable | Correlation | P-Value | R² | Predictor Quality |
|----------|-------------|---------|-----|-------------------|
| **Population Density** | 0.906 | 3e-04 | 0.8212 | ✅ Excellent |
| **Census Population** | 0.899 | 0.00041 | 0.8078 | ✅ Excellent |
| **Total Families** | 0.875 | 0.00093 | 0.7650 | ✅ Good |
| Households Under 18 | 0.675 | 0.03236 | 0.4552 | ⚠️ Weak |
| Land Area | -0.287 | 0.42126 | 0.0824 | ❌ Not significant |

### Best Predictors for Regression Model

| Rank | Variable | R² | Status |
|------|----------|-----|--------|
| 1 | Population Density | 0.8212 | ✅ Use |
| 2 | Census Population | 0.8078 | ✅ Use |
| 3 | Total Families | 0.7650 | ✅ Use |

---

## 📊 Outlier Scenario Comparison

| Dataset Version | Avg Sales | Median Sales | Variance |
|-----------------|-----------|--------------|----------|
| Original (all data) | $343,028 | $283,824 | $59,204 |
| Without All Outliers | $257,337 | $258,876 | -$1,539 |
| Without Sales Outliers | $256,920 | $253,584 | $3,336 |
| Without Cheyenne | $285,541 | $268,704 | $16,837 |
| **Without Gillette** | **$323,017** | **$268,704** | **$54,313** |

---

## 📤 Output Dataset

### Final Training Set Characteristics

| Metric | Value |
|--------|-------|
| **Records** | 10 cities (removed Gillette) |
| **Target Variable** | Total Pawdacity Sales |
| **Best Predictors** | Population Density, Census Population, Total Families |
| **Model Readiness** | ✅ Ready for regression |

---

## 💡 Key Learnings

| Learning | Details |
|----------|---------|
| **Outlier Strategy** | Don't remove all outliers blindly; test each scenario |
| **Statistical Validation** | Compare R², P-values across scenarios |
| **Business Context** | Cheyenne is state capital — high sales expected and valid |
| **Data Quality** | Clean data enables better predictions |
| **Imputation Testing** | Tested mean/median imputation — removal performed better |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| README.md | This documentation file |
| Pawdacity_Report_1st Submission_Maged.pdf | Detailed analysis report |
| Pawdacity_Analytical Dataset Project_Maged_1st_Submission.yxmd | Alteryx workflow |
| Sales_Avg_Vs_Med_All Scenarios.xlsx | Outlier scenario comparison |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Insurance Claims (Kaggle) | Regression (Python) | [Link](../kaggle-insurance-prediction/) |
| Diamond Pricing | Regression | [Link](../diamond-pricing/) |
| Catalog Demand | Regression | [Link](../catalog-demand/) |
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
| GitHub | [Follow](https://github.com/Maged-Baheig) |
| Email | [Reach Out](mailto:magedbaheig@gmail.com) |

📍 **Location:** Cairo, Egypt

---

*Part of the [Data Science Portfolio](https://github.com/Maged-Baheig/data-science-portfolio/tree/main)*
