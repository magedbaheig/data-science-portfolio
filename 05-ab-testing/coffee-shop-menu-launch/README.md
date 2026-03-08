# ☕ Coffee Shop A/B Test: New Menu Launch Analysis

**Matched-Pair Experimental Design for Menu Rollout Decision**

![Alteryx](https://img.shields.io/badge/Alteryx-Workflow-orange)
![Python](https://img.shields.io/badge/Python-Planned-lightgrey)
![KNIME](https://img.shields.io/badge/KNIME-Planned-lightgrey)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Course](https://img.shields.io/badge/Udacity-Predictive%20Analytics%20for%20Business-blueviolet)

---

## 📋 Project Overview

| Aspect | Details |
|--------|---------|
| **Course** | Udacity Predictive Analytics for Business Nanodegree (Bertelsmann Scholarship) |
| **Year** | 2021 |
| **Type** | A/B Testing - Matched-Pair Experimental Design |
| **Objective** | Determine whether to roll out updated menu with TV advertising to all stores |
| **Tools** | Alteryx Designer |
| **Recommendation** | Roll out new menu — 41% lift, statistically significant |

---

## 🎯 Business Problem & Objective

**Company:** Round Roasters (Coffee Shop Chain)

**Proposed Change:** Launch updated menu with television advertising campaign

**Business Question:** Should the company roll out the updated menu to all stores?

**Success Criteria:**

| Criterion | Threshold | Actual Result |
|-----------|-----------|---------------|
| **Practical Significance** | At least 18% increase in profit growth | 41% increase |
| **Statistical Significance** | P-value < 0.05 | P-value = 0.000 |

---

## 📊 Experimental Design

### Test Configuration

| Element | Details |
|---------|---------|
| **Performance Metric** | Weekly Gross Margin (Sum) |
| **Test Period** | 12 weeks (April 29 - July 21, 2016) |
| **Aggregation Level** | Weekly |
| **Treatment Stores** | 10 stores |
| **Control Stores** | 20 stores (2 per treatment) |
| **Matching Method** | Matched-Pair Design |

### Hypothesis Framework

| Hypothesis | Statement |
|------------|-----------|
| **NULL (H0)** | New menu has no significant impact on gross margin |
| **ALTERNATIVE (H1)** | New menu increases gross margin by at least 18% |

---

## 🔧 Step 1: Data Preparation

### Outlier Removal

Two outlier control stores removed based on AvgMonthSales and AvgMonthTrafficCount:

| Store ID | Outlier Type | AvgMonthSale | AvgMonthTrafficCount |
|----------|--------------|--------------|----------------------|
| 11518 | High Value | $52,119 | 3,238 |
| 9338 | Low Value | $2,661 | 291 |

### Data Aggregation

| Attribute | Value |
|-----------|-------|
| Aggregation Level | Weekly |
| Time Span | 76 weeks per store |
| Metric | Sum of Gross Margin |

---

## 🔧 Step 2: Control Variable Selection

### Potential Control Variables Evaluated

| Variable | Correlation with Gross Margin | Included |
|----------|-------------------------------|----------|
| AvgMonthSales | 0.999 (Highest) | Yes |
| AvgMonthTrafficCount | Strong | No (multicollinear) |
| AvgMonthQTY | Strong | No (multicollinear) |
| Region | Strong | Yes |
| Sq_Ft | Weak/None | No |

### Multicollinearity Handling

| Finding | Action |
|---------|--------|
| AvgMonthSales, AvgMonthTrafficCount, and AvgMonthQTY are highly correlated | Selected only AvgMonthSales (highest correlation: 0.999356) |

### Trend and Seasonality Analysis

| Component | Finding | Action |
|-----------|---------|--------|
| Trend | Present in weekly traffic | Added as control variable |
| Seasonality | Clear seasonal pattern | Added as control variable |

### Final Control Variables (4 Total)

| Variable | Type | Purpose |
|----------|------|---------|
| Trend | Time-based | Account for temporal patterns |
| Seasonality | Time-based | Account for cyclical patterns |
| AvgMonthSales | Store characteristic | Match similar-performing stores |
| Region | Store characteristic | Account for geographic differences |

---

## 🔧 Step 3: Treatment-Control Matching

### Matching Results (10 Treatment Stores to 20 Control Stores)

| Treatment Store | Control Store 1 | Control Store 2 |
|-----------------|-----------------|-----------------|
| 2288 | 9081 | 2568 |
| 2293 | 12219 | 9524 |
| 2301 | 3102 | 9238 |
| 2322 | 2409 | 12786 |
| 2341 | 3185 | 12536 |
| 1664 | 7162 | 7484 |
| 1675 | 8162 | 7434 |
| 1696 | 1964 | 1863 |
| 1700 | 1630 | 2014 |
| 1712 | 2114 | 8312 |

---

## 📈 Step 4: Results & Analysis

### Overall Results

| Metric | Value | Interpretation |
|--------|-------|----------------|
| **Lift** | 41% | Exceeds 18% threshold |
| **P-Value** | 0.000 | 100% statistically significant |
| **Expected Total Lift** | $6,898,441 | Projected annual increase |

### Regional Breakdown

**Western Region:**

| Metric | Value |
|--------|-------|
| Lift | 36.3% |
| P-Value | 0.006% (99.4% confident) |
| Weekly Lift per Store | $502.30 |
| Expected Total Lift | $4,879,403 |

**Central Region:**

| Metric | Value |
|--------|-------|
| Lift | 45.8% |
| P-Value | 0.004% (99.6% confident) |
| Weekly Lift per Store | $881.40 |
| Expected Total Lift | $2,019,039 |

### Regional Comparison

| Region | Lift | P-Value | Confidence | Weekly Lift/Store |
|--------|------|---------|------------|-------------------|
| Western | 36.3% | 0.006% | 99.4% | $502.30 |
| Central | 45.8% | 0.004% | 99.6% | $881.40 |
| **Overall** | **41.0%** | **0.000%** | **100%** | — |

---

## ✅ Recommendation

**Strongly recommend launching the new menu to all stores.**

| Criterion | Threshold | Result | Status |
|-----------|-----------|--------|--------|
| Practical Significance | 18% lift | 41% lift | Passed |
| Statistical Significance | P < 0.05 | P = 0.000 | Passed |
| Regional Consistency | Both regions positive | West 36.3%, Central 45.8% | Passed |

### Business Impact Summary

| Impact Area | Value |
|-------------|-------|
| Overall Expected Lift | $6,898,441 |
| Western Region Contribution | $4,879,403 (71%) |
| Central Region Contribution | $2,019,039 (29%) |

---

## 💡 Key Learnings

| Learning | Detail |
|----------|--------|
| **Matched-Pair Design** | Matching treatment to similar control stores improves causal inference validity |
| **Multicollinearity Handling** | Identified and resolved highly correlated control variables by selecting strongest predictor |
| **Trend/Seasonality** | Time-based control variables essential for retail/restaurant experiments |
| **Practical vs Statistical** | Both significance types required for actionable business decisions |
| **Regional Analysis** | Breaking results by region reveals implementation priorities (Central shows higher lift) |

---

## 🛠️ Tools & Techniques

| Category | Details |
|----------|---------|
| **Platform** | Alteryx Designer |
| **Experimental Design** | Matched-Pair A/B Test |
| **Matching Tool** | AB Trend Tool (Alteryx) |
| **Control Variables** | Trend, Seasonality, AvgMonthSales, Region |
| **Correlation Analysis** | Association measures, multicollinearity detection |
| **Statistical Tests** | T-test for significance, P-value evaluation |
| **Metrics** | Gross Margin (Sum), Lift percentage |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| `README.md` | This documentation file |
| `ab-test-workflow.yxmd` | Alteryx workflow with matching and analysis |
| `New_Menu_Launch_Report.pdf` | Detailed analysis report with visualizations |

---

## 📊 Experimental Design Summary

| Phase | Activity | Output |
|-------|----------|--------|
| **1. Planning** | Define metric, test period, aggregation | Weekly Gross Margin, 12 weeks |
| **2. Data Prep** | Clean data, remove outliers, aggregate | 76 weeks x all stores |
| **3. Variable Selection** | Correlation analysis, multicollinearity check | 4 control variables |
| **4. Matching** | Match treatment to control stores | 10 treatment : 20 control |
| **5. Analysis** | Calculate lift, test significance | 41% lift, P=0.000 |
| **6. Recommendation** | Business decision | Roll out to all stores |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Capstone: Store Optimization | Clustering + Classification + Forecasting | [Link](../../00-capstone-projects/store-format-optimization/) |
| Video Game Forecasting | Time Series | [Link](../video-game-forecasting/) |
| Credit Default Risk | Classification | [Link](../../02-classification/credit-default-risk/) |

---

## 📜 Acknowledgments

| Entity | Contribution |
|--------|--------------|
| **Udacity** | Predictive Analytics for Business Nanodegree program |
| **Bertelsmann** | Scholarship sponsorship |

---

## 👤 Author

**Maged Baheig**

| Platform | Link |
|----------|------|
| LinkedIn | [magedbaheig](https://www.linkedin.com/in/magedbaheig) |
| Kaggle | [magedbaheig](https://www.kaggle.com/magedbaheig) |
| GitHub | [magedbaheig](https://github.com/magedbaheig) |
| Email | magedbaheig@gmail.com |

📍 Cairo, Egypt

---

*Part of the [Data Science & ML Portfolio](https://github.com/magedbaheig/data-science-portfolio)*
