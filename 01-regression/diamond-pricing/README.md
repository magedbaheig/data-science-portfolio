# 💎 Diamond Price Prediction

**Multiple Linear Regression for Auction Bidding Recommendations**

![Excel](https://img.shields.io/badge/Excel-Regression-green)
![Alteryx](https://img.shields.io/badge/Alteryx-Workflow-orange)
![Python](https://img.shields.io/badge/Python-Planned-lightgrey)
![KNIME](https://img.shields.io/badge/KNIME-Planned-lightgrey)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Udacity](https://img.shields.io/badge/Udacity-Meets%20Specifications-brightgreen)

---

## 📋 Project Overview

| Aspect | Details |
|--------|---------|
| **Course** | Udacity Predictive Analytics for Business (Bertelsmann) |
| **Year** | 2021 |
| **Type** | Supervised Learning (Regression) |
| **Objective** | Predict diamond prices for auction bidding recommendation |
| **Review** | ✅ Meets Specifications |

---

## 🛠️ Implementations

| Tool | Status | Description |
|------|--------|-------------|
| **Excel** | ✅ Complete | Regression with Data Analysis ToolPak |
| **Alteryx** | ✅ Complete | Visual workflow (Ordinal + Categorical approaches) |
| **KNIME** |  🔜 Planned | Open-source workflow replication |
| **Python** | 🔜 Planned | scikit-learn implementation |

---

## 🎯 Business Problem

A jewelry company wants to bid on 3,000 diamonds at auction. The company needs to determine:
- **How much to bid** for the entire lot
- **Ensure 30% profit margin** (company purchases at 70% of retail)

---

## 📊 Dataset

| Dataset | Records | Purpose |
|---------|---------|---------|
| Training (diamonds.csv) | ~5,000 | Build regression model |
| Prediction (new-diamonds.csv) | 3,000 | Predict prices for bidding |

### Features

| Feature | Type | Description |
|---------|------|-------------|
| **Carat** | Continuous | Weight of diamond |
| **Cut** | Categorical | Quality of cut (Fair, Good, Very Good, Premium, Ideal) |
| **Color** | Categorical | Diamond color (D-J) |
| **Clarity** | Categorical | Clarity rating (I1, SI2, SI1, VS2, VS1, VVS2, VVS1, IF) |
| **Price** | Continuous | Target variable (retail price) |

---

## 🔧 Technical Approach

### 1. Exploratory Analysis (Simple Linear Regression)

| Variable | P-Value | R² | Conclusion |
|----------|---------|-----|------------|
| **Carat** | 0 | 0.85 | Excellent predictor |
| Cut (Ordinal) | 2.21E-33 | 0.003 | Weak alone, useful in MLR |
| Clarity (Ordinal) | 5.54E-224 | 0.020 | Weak alone, useful in MLR |

### 2. Model Comparison

| Model Type | Adjusted R² | P-Values | Selected |
|------------|-------------|----------|----------|
| **Ordinal MLR** | 0.90 | All low | ❌ |
| **Categorical (Dummy) MLR** | 0.92 | All very low | ✅ Best |

### 3. Final Model Equation

**Best Linear Regression Equation (Dummy Variables):**

Price = -7,382.30
 + (8,887.40 × Carat)
 + (682.20 × cutGood) + (1,017.10 × cutIdeal) + (889.30 × cutPremium) + (867.10 × cutVery Good)
 + (-205.20 × colorE) + (-298.70 × colorF) + (-498.60 × colorG) + (-966.20 × colorH) + (-1,441.40 × colorI) + (-2,321.40 × colorJ)
 + (5,421.80 × clarityIF) + (3,570.60 × claritySI1) + (2,616.90 × claritySI2) + (4,534.70 × clarityVS1) + (4,217.10 × clarityVS2) + (5,057.80 × clarityVVS1) + (4,953.70 × clarityVVS2)


**Simplified Model (Course Provided):**

Price = -5,269 + 8,413 × Carat + 158.1 × Cut + 454 × Clarity


---

## 📈 Results

### Model Performance

| Metric | Value |
|--------|-------|
| **Adjusted R²** | 0.92 |
| **Carat Coefficient** | $8,413 per carat |
| **Model Significance** | All P-values < 0.05 |

### Business Recommendation

| Metric | Value |
|--------|-------|
| **Total Predicted Price** | $11,733,522.76 |
| **Recommended Bid (70%)** | **$8,213,465.93** |
| **Profit Margin** | 30% |

### Key Insights

| Insight | Details |
|---------|---------|
| **Strongest Predictor** | Carat weight (R² = 0.85 alone) |
| **Each Additional Carat** | Increases price by ~$8,413 |
| **Best Model** | Dummy variable MLR outperforms Ordinal MLR |
| **Negative Predictions** | 291 records had negative predictions (handled in analysis) |

---

## 📊 Visualizations

### Analysis Performed

| Visualization | Purpose |
|---------------|---------|
| Carat vs Price Scatter Plot | Identify linear relationship |
| Predicted vs Actual Prices | Model validation |
| Residual Analysis | Model diagnostics |

### Key Observations

| Observation | Implication |
|-------------|-------------|
| Predicted prices more compact than actual | Model doesn't capture all variation |
| Negative predictions exist | Need handling strategy for edge cases |
| Price variation at same carat | Lurking variables present (color, etc.) |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| README.md | This documentation file |
| P1_Predicting Diamonds Price_Maged Solution.xlsx | Excel analysis workbook |
| P1_Predicting Diamonds Price_Maged Solution.yxmd | Alteryx visual workflow |
| Predicting Diamond Prices Report_Maged Baheig.pdf | Detailed analysis report |
| Submission_Meet Specifications Review.pdf | Udacity review (Meets Specifications) |

---

## 💡 Key Learnings

| Learning | Details |
|----------|---------|
| **Dummy vs Ordinal** | Categorical dummy variables (R²=0.92) outperform ordinal encoding (R²=0.90) |
| **Feature Importance** | Carat dominates; Cut, Color, Clarity contribute incrementally |
| **Business Translation** | Statistical model directly informs bidding strategy |
| **Model Limitations** | Single model may not capture all price variation |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Insurance Claims (Kaggle) | Regression (Python) | [Link](../kaggle-insurance-prediction/) |
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
