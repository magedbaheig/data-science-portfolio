# 🏆 Kaggle 30 Days of ML: Insurance Claims Prediction

**Top 30% Ranking | Regression with LightGBM**

![Kaggle](https://img.shields.io/badge/Kaggle-Competition-blue)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![LightGBM](https://img.shields.io/badge/LightGBM-Gradient%20Boosting-green)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Ranking](https://img.shields.io/badge/Ranking-Top%2030%25-gold)

---

## 📋 Project Overview

| Aspect | Details |
|--------|---------|
| **Competition** | Kaggle 30 Days of ML |
| **Year** | 2021 |
| **Type** | Supervised Learning (Regression) |
| **Objective** | Predict continuous insurance claim amounts |
| **Ranking** | **Top 30%** (outperforming ~70% of participants) |

---

## 🎯 Problem Statement

Predict a continuous target variable (insurance claim amount) based on a mix of categorical and numerical features using a synthetic dataset created with CTGAN (based on real data).

---

## 📊 Dataset

| Metric | Value |
|--------|-------|
| Training Records | 300,000 |
| Test Records | 200,000 |
| Total Records | **500,000** |
| Categorical Features | 10 (cat0 - cat9) |
| Numerical Features | 14 (cont0 - cont13) |
| Target Variable | Continuous (claim amount) |
| Missing Values | None |

---

## 🔧 Technical Approach

### 1. Exploratory Data Analysis
- Analyzed feature distributions and correlations
- Identified low-correlation features for removal
- Examined categorical variable cardinality

### 2. Feature Engineering
- **Dropped low-correlation columns:** cont1, cont8, cat0, cat1, cat2, cat9
- **Final features used:** 19 (7 categorical + 12 numerical)

### 3. Categorical Encoding
- **Label Encoding** for all categorical variables
- Cardinality analysis (all ≤ 16 unique values)

### 4. Model Selection & Training

| Model | Description |
|-------|-------------|
| **LGBMRegressor** | Final model (LightGBM gradient boosting) |
| K-Fold CV | 2-fold cross-validation |
| Early Stopping | 50 rounds |

### 5. Hyperparameter Configuration

| Parameter | Value |
|-----------|-------|
| max_depth | 43 |
| subsample | 0.52 |
| colsample_bytree | 0.20 |
| learning_rate | 0.0095 |
| reg_lambda | 21.86 |
| reg_alpha | 15.43 |
| min_child_samples | 24 |
| num_leaves | 10 |
| max_bin | 839 |
| cat_smooth | 86 |
| n_estimators | 2000 |
| metric | rmse |

---

## 📈 Results

| Metric | Value |
|--------|-------|
| **Best RMSE** | 0.7249 |
| **Max RMSE** | 0.7261 |
| **Average RMSE (CV)** | 0.7255 |
| **Competition Ranking** | **Top 30%** |

### Cross-Validation Performance

| Fold | RMSE |
|------|------|
| Fold 1 | 0.7249 |
| Fold 2 | 0.7261 |
| **Average** | **0.7255** |

---

## 🛠️ Tools & Libraries

| Category | Tools |
|----------|-------|
| **Language** | Python 3.x |
| **Data Processing** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **ML Framework** | scikit-learn, LightGBM, XGBoost |
| **Validation** | K-Fold Cross-Validation |
| **Environment** | Kaggle Notebooks |

### Key Libraries Used

| Library | Purpose |
|---------|---------|
| pandas | Data manipulation |
| numpy | Numerical operations |
| matplotlib | Visualization |
| seaborn | Statistical visualization |
| scikit-learn | Preprocessing, model selection |
| lightgbm | LGBMRegressor model |
| xgboost | Alternative model exploration |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| README.md | This documentation file |
| 30-days-of-ml-competition.ipynb | Main Jupyter notebook |
| requirements.txt | Python dependencies |

---

## 🚀 How to Run

### Option 1: Kaggle (Recommended)
1. Visit the competition page
2. Fork this notebook
3. Run all cells

### Option 2: Local
1. Install dependencies: `pip install -r requirements.txt`
2. Open notebook: `jupyter notebook 30-days-of-ml-competition.ipynb`

> **Note:** Dataset is available only through Kaggle competition.

---

## 💡 Key Learnings

| Learning | Details |
|----------|---------|
| **Feature Selection** | Removing low-correlation features improved model performance |
| **LightGBM Efficiency** | Faster training than XGBoost with comparable results |
| **Regularization** | High reg_lambda and reg_alpha helped prevent overfitting |
| **Cross-Validation** | K-Fold CV provided stable performance estimates |

---

## 📊 Feature Importance

Based on analysis, the most impactful features were:

| Feature Type | Features |
|--------------|----------|
| **Numerical** | cont0, cont2-cont7, cont9-cont13 |
| **Categorical** | cat3-cat8 (moderate cardinality) |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Diamond Pricing | Regression | [Link](../diamond-pricing/) |
| Catalog Demand | Regression | [Link](../catalog-demand/) |
| Credit Default Risk | Classification | [Link](../../02-classification/credit-default-risk/) |

---

## 📜 Competition Details

| Detail | Value |
|--------|-------|
| **Host** | Kaggle |
| **Duration** | 30 days |
| **Participants** | 7,000+ |
| **Evaluation** | RMSE (Root Mean Squared Error) |
| **Dataset** | Synthetic (CTGAN-generated from real data) |

---

## 👤 Author

**Maged Baheig**

| Platform | Link |
|----------|------|
| LinkedIn | [Connect](https://www.linkedin.com/in/magedbaheig) |
| Kaggle | [Profile](https://www.kaggle.com/magedbaheig) |
| GitHub | [Follow](https://github.com/Maged-Baheig) |
| Email | [Email Me](mailto:magedbaheig@gmail.com) |
- **Location:** Cairo, Egypt
---

*Part of the [Data Science Portfolio](../../)*
