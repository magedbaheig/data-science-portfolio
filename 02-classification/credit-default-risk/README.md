# 💳 Credit Default Risk Prediction

**Multi-Model Classification Comparison for Loan Approval Decision**

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
| **Type** | Supervised Learning (Binary Classification) |
| **Objective** | Classify 500 loan applicants as creditworthy or non-creditworthy |
| **Models Compared** | 4 (Logistic Regression, Decision Tree, Random Forest, Boosted) |
| **Best Model** | Random Forest (79.3% accuracy, 73.7% AUC) |

---

## 🛠️ Implementations

| Tool | Status | Description |
|------|--------|-------------|
| **Alteryx** | ✅ Complete | Multi-model classification workflow |
| **Excel** | ✅ Complete | Data analysis and visualization |
| **Python** | 🔜 Planned | scikit-learn implementation |
| **KNIME** | 🔜 Planned | Open-source workflow replication |

---

## 🎯 Business Problem

A small bank experienced a sudden influx of **500 loan applications** due to a competitor's financial scandal. The task is to:
- Process all applications within one week
- Identify **creditworthy customers** for loan approval
- Provide recommendations to management within two days

### Decision Framework

| Element | Description |
|---------|-------------|
| **Decision** | Who is creditworthy for a loan? |
| **Analysis Type** | Binary Classification (Creditworthy vs Non-Creditworthy) |
| **Success Metric** | Overall accuracy + balanced precision for both classes |

---

## 📊 Dataset

### Original Data

| Dataset | Records | Purpose |
|---------|---------|---------|
| Training Set | 350 (70%) | Build classification models |
| Validation Set | 150 (30%) | Evaluate model performance |
| New Applicants | 500 | Score for final recommendation |

### Data Cleaning Summary

| Action | Count | Details |
|--------|-------|---------|
| **Fields Removed** | 7 | Low variability, missing data, no correlation |
| **Fields Imputed** | 1 | Age-Year (median = 33, right-skewed data) |
| **Final Features** | 13 | Average Age = 36 |

### Removed Fields

| Field | Reason | Justification |
|-------|--------|---------------|
| Duration-in-Current-address | Missing Data | 69% missing values |
| Concurrent-Credits | Low Variability | Only one value (Other Banks/Depts) |
| Occupation | Low Variability | Only one value (1) |
| Guarantors | Low Variability | Heavily skewed towards "None" |
| Foreign-Worker | Low Variability | Heavily skewed (1.0-1.1) |
| No-of-dependents | Low Variability | Heavily skewed (1.0-1.1) |
| Telephone | No Correlation | Correlation = 0.03, P-Value = 0.71 |

---

## 🔧 Technical Approach

### 1. Model Training Configuration

| Parameter | Value |
|-----------|-------|
| Training Split | 70% |
| Validation Split | 30% |
| Random Seed | 1 |

### 2. Models Developed

| Model | Description |
|-------|-------------|
| **Logistic Regression** | Stepwise adjusted |
| **Decision Tree** | Standard classification tree |
| **Random Forest** | Ensemble of decision trees |
| **Boosted Model** | Gradient boosting (1808 trees via 5-fold CV) |

---

## 📈 Model Comparison Results

### Overall Performance

| Model | Overall Accuracy | AUC | Creditworthy Precision | Non-Creditworthy Precision | Bias |
|-------|-----------------|-----|------------------------|---------------------------|------|
| Logistic Regression | 76.0% | — | 80.0% | 63.0% | 17.0% |
| Decision Tree | 67.0% | — | 75.0% | 44.0% | 31.0% |
| **Random Forest** | **79.3%** | **73.7%** | **78.5%** | **85.0%** | **6.5%** |
| Boosted Model | 79.0% | — | 78.3% | 81.0% | 2.7% |

### Detailed Model Analysis

#### 1. Logistic Regression

| Metric | Creditworthy | Non-Creditworthy |
|--------|--------------|------------------|
| Precision | 80.0% | 63.0% |
| Recall | 87.6% | 49.0% |
| Error Rate | 12.4% | 51.0% |

| Most Important Predictors | P-Value |
|--------------------------|---------|
| Account.Balance (Some Balance) | 1.65e-07 |
| Credit.Amount | 0.00296 |
| Purpose (New car) | 0.00566 |
| Payment.Status.of.Previous.Credit | 0.0183 |
| Instalment.per.cent | 0.02549 |
| Length.of.current.employment (<1yr) | 0.03596 |

**Decision:** ❌ Not Accepted (Low precision, high bias)

---

#### 2. Decision Tree

| Metric | Creditworthy | Non-Creditworthy |
|--------|--------------|------------------|
| Precision | 75.0% | 44.0% |
| Recall | 79.0% | 38.0% |
| Error Rate | 21.0% | 62.2% |

| Top 5 Predictors | Importance |
|------------------|------------|
| Account.Balance | 16.4% |
| Duration.of.Credit.Month | 12.7% |
| Credit.Amount | 11.8% |
| Value.Savings.Stocks | 9.1% |
| Age.Years | 9.0% |

**Decision:** ❌ Not Accepted (Low precision, high bias, low accuracy)

---

#### 3. Random Forest ⭐ SELECTED

| Metric | Creditworthy | Non-Creditworthy |
|--------|--------------|------------------|
| Precision | 78.5% | 85.0% |
| Recall | 97.0% | 38.0% |
| Error Rate | 3.0% | 62.2% |

| Top 4 Predictors |
|------------------|
| Credit.Amount |
| Age.Years |
| Duration.of.Credit.Month |
| Account.Balance |

**Decision:** ✅ Accepted (Best accuracy, good precision balance)

---

#### 4. Boosted Model

| Metric | Creditworthy | Non-Creditworthy |
|--------|--------------|------------------|
| Precision | 78.3% | 81.0% |
| Recall | 96.2% | 38.0% |
| Error Rate | 3.8% | 62.2% |

| Top 2 Predictors |
|------------------|
| Account.Balance |
| Credit.Amount |

**Configuration:** Best trees = 1808 (5-fold cross validation)

**Decision:** ✅ Accepted (Good accuracy, lowest bias)

---

## 🏆 Model Selection: Random Forest

### Why Random Forest?

| Criterion | Random Forest Performance | Justification |
|-----------|--------------------------|---------------|
| **Overall Accuracy** | 79.3% (Best) | Highest among all models |
| **AUC** | 73.7% (Best) | Largest area under ROC curve |
| **Precision Balance** | 78.5% vs 85.0% | Good balance between classes |
| **Prediction Bias** | 6.5% | Reasonable and acceptable |

### Selection Criteria Applied

| Priority | Metric | Forest Result |
|----------|--------|---------------|
| 1 | Best Overall Accuracy | ✅ 79.3% |
| 2 | Best Class Accuracies | ✅ 97.1% + 38.0% |
| 3 | Largest ROC AUC | ✅ 73.7% |
| 4 | Acceptable Bias | ✅ 6.5% |

---

## 📤 Final Results

### Creditworthiness Classification

| Classification | Count |
|----------------|-------|
| **Creditworthy** | 408 |
| **Non-Creditworthy** | 92 |
| **Total Applicants** | 500 |

### Business Recommendation

| Recommendation | Details |
|----------------|---------|
| **Approve Loans For** | 408 applicants classified as Creditworthy |
| **Model Confidence** | 79.3% overall accuracy |
| **Risk Note** | 38% recall for Non-Creditworthy (some may be misclassified) |

---

## 💡 Key Learnings

| Learning | Details |
|----------|---------|
| **Multi-Model Comparison** | Always compare multiple algorithms before selection |
| **Accuracy vs Bias Trade-off** | Highest accuracy doesn't always mean lowest bias |
| **Data Cleaning Impact** | Removing 7 low-quality fields improved model performance |
| **Business Context** | Selection criteria should align with business priorities |
| **Ensemble Methods** | Random Forest outperformed single tree and regression |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| README.md | This documentation file |
| Creditworthiness_Report_Submission_Maged.pdf | Detailed analysis report |
| Creditworthiness_Submission_Maged.yxmd | Alteryx multi-model workflow |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Insurance Claims (Kaggle) | Regression (Python) | [Link](../01-regression/kaggle-insurance-prediction/) |
| Diamond Pricing | Regression | [Link](../01-regression/diamond-pricing/) |
| Country Segmentation | Clustering | [Link](../03-clustering/country-segmentation/) |

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
