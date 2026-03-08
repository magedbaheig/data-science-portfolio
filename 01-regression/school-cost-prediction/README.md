# 🏫 School Data Preparation

**Data Cleaning & Statistical Predictor Selection for Per-Pupil Cost Prediction**

![Alteryx](https://img.shields.io/badge/Alteryx-Workflow-orange)
![Excel](https://img.shields.io/badge/Excel-Analysis-green)
![Python](https://img.shields.io/badge/Python-Planned-lightgrey)
![KNIME](https://img.shields.io/badge/KNIME-Planned-lightgrey)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📋 Project Overview

| Aspect | Details |
|--------|---------|
| **Course** | Udacity Predictive Analytics for Business (Bertelsmann) |
| **Year** | 2021 |
| **Type** | Data Preparation / Statistical Predictor Selection |
| **Objective** | Clean messy school data and identify optimal predictors for per-pupil cost prediction |
| **Output** | Analysis-ready dataset with statistically validated predictor variables |

---

## 🛠️ Implementations

| Tool | Status | Description |
|------|--------|-------------|
| **Alteryx** | ✅ Complete | Data cleansing and preparation workflow |
| **Excel** | ✅ Complete | Statistical analysis and charts |
| **Python** | 🔜 Planned | Pandas implementation |
| **KNIME** | 🔜 Planned | Open-source workflow replication |

---

## 🎯 Business Problem

A school district wants to **predict the per-pupil costs** of schools based on high-level summary data. However, the dataset has significant quality issues that must be resolved before building a prediction model.

### Problem Statement

| Challenge | Description |
|-----------|-------------|
| **Data Quality** | Dataset is messy with many quality issues |
| **Goal** | Clean data AND identify best predictors for regression |
| **Target Variable** | Per-pupil cost |
| **Model Type** | Linear Regression (supervised learning) |

---

## 🔧 Technical Approach

### 1. Problem Definition

| Aspect | Definition |
|--------|------------|
| **Problem Type** | Supervised Learning (Regression) |
| **Target Variable** | Per-pupil cost (continuous) |
| **Model Required** | Linear Regression |

### 2. Data Quality Issues Addressed

| Issue Type | Actions Taken |
|------------|---------------|
| **Missing Values** | Detected and imputed using distribution-appropriate methods |
| **Invalid Values** | Identified and corrected |
| **Inaccurate Values** | Validated and fixed |
| **Inconsistent Values** | Standardized across dataset |

### 3. Data Processing Steps

| Step | Description |
|------|-------------|
| **Inspection** | Assessed data quality and structure |
| **Merging** | Combined multiple datasets |
| **Appending** | Added supplementary data sources |
| **Transformation** | Restructured data for analysis |
| **Aggregation** | Summarized data at appropriate level |

### 4. Statistical Predictor Selection

> 🔬 **This project employed advanced statistical techniques to identify optimal predictor variables for downstream linear regression modeling.**

| Analysis | Purpose |
|----------|---------|
| **Distribution Check** | Determine best imputation method (mean vs median) |
| **Correlation Analysis** | Identify strength of predictor relationships |
| **R² Evaluation** | Assess explanatory power of each variable |
| **P-Value Testing** | Validate statistical significance |

### 5. Predictor Validation Process

| Step | Method | Outcome |
|------|--------|---------|
| 1 | Calculate correlation with target | Rank predictors |
| 2 | Run Simple Linear Regression | Get individual R² |
| 3 | Check P-Values | Confirm significance |
| 4 | Select best predictors | Build regression-ready dataset |

---

## 📊 Data Cleaning Operations

### Missing Value Handling

| Step | Method |
|------|--------|
| Detection | Identified null/missing values per variable |
| Distribution Analysis | Checked skewness to choose imputation |
| Imputation | Applied mean/median based on distribution |
| Validation | Verified imputation didn't distort data |

### Outlier Treatment

| Step | Method |
|------|--------|
| Detection | Used IQR/statistical methods |
| Analysis | Assessed impact on model |
| Decision | Statistically justified removal/retention |
| Documentation | Recorded all decisions |

### Data Integration

| Operation | Details |
|-----------|---------|
| **Merge** | Combined related datasets on key fields |
| **Append** | Stacked similar datasets vertically |
| **Transform** | Reshaped data structure as needed |
| **Aggregate** | Created summary statistics |

---

## 📈 Output

### Final Dataset Characteristics

| Attribute | Status |
|-----------|--------|
| **Missing Values** | ✅ Handled |
| **Invalid Values** | ✅ Corrected |
| **Inconsistencies** | ✅ Resolved |
| **Structure** | ✅ Ready for regression |
| **Predictor Variables** | ✅ Statistically validated (R², P-Value) |

### Ready for Next Steps

| Next Step | Description |
|-----------|-------------|
| Build Linear Regression | Using cleaned dataset with validated predictors |
| Predict Per-Pupil Cost | Based on statistically significant school attributes |
| Validate Model | Using appropriate metrics |

---

## 💡 Key Learnings

| Learning | Details |
|----------|---------|
| **Data Quality First** | Clean data is prerequisite for accurate models |
| **Statistical Predictor Selection** | Use R² and P-Values to choose best predictors |
| **Distribution Awareness** | Imputation method depends on data distribution |
| **Documentation** | Record all cleaning decisions for reproducibility |
| **Iterative Process** | Data cleaning requires multiple passes |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| README.md | This documentation file |
| Preparing School Data_Maged_Solution.yxmd | Alteryx data preparation workflow |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Pet Store Sales (Pawdacity) | Data Prep + Predictor Selection | [Link](../pet-store-sales/) |
| Diamond Pricing | Regression | [Link](../diamond-pricing/) |
| Catalog Demand | Regression | [Link](../catalog-demand/) |
| Insurance Claims (Kaggle) | Regression (Python) | [Link](../kaggle-insurance-prediction/) |

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
