# 🎮 Video Game Sales Forecasting

**Time Series Analysis: ETS vs ARIMA Model Comparison**

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
| **Type** | Time Series Forecasting |
| **Objective** | Forecast video game sales for next 4 months |
| **Tools** | Alteryx Designer |
| **Final Model** | ARIMA(0,1,1)(0,1,0)[12] |

---

## 🎯 Business Problem & Objective

A video game retailer needs to forecast monthly sales for the next 4 periods to support:

| Business Need | Application |
|---------------|-------------|
| **Inventory Planning** | Stock appropriate quantities |
| **Budget Forecasting** | Revenue projections |
| **Supply Chain** | Coordinate with distributors |

**Approach:** Compare ETS and ARIMA models, select best performer on holdout validation, forecast with confidence intervals.

---

## 📊 Dataset Overview

| Attribute | Details |
|-----------|---------|
| **Granularity** | Monthly sales |
| **Time Range** | Multiple years (2013 partial: Jan-Sep) |
| **Missing Values** | None |
| **Holdout Sample** | Last 4 records (2013-06 to 2013-09) |

### Time Series Criteria Validation

| Criterion | Status | Evidence |
|-----------|--------|----------|
| Time dependent | ✅ | Continuous monthly intervals |
| Sequential order | ✅ | Equal spacing between observations |
| Single value per period | ✅ | One sales value per month |
| Sufficient history | ✅ | Multiple years of data |

---

## 🔍 Step 1: Time Series Decomposition

### Component Analysis

| Component | Observed Pattern | Treatment | Rationale |
|-----------|------------------|-----------|-----------|
| **Error** | Growing over time | Multiplicative **(M)** | Peaks and valleys increasing in magnitude |
| **Trend** | Upward linear | Additive **(A)** | Constant linear increase (not exponential) |
| **Seasonality** | Slightly growing peaks | Multiplicative **(M)** | Seasonal amplitude increasing over time |

### Decomposition Insights

| Observation | Implication |
|-------------|-------------|
| Error variance increasing | Multiplicative error handling needed |
| Linear trend (not exponential) | Additive trend appropriate |
| Seasonal peaks growing | Multiplicative seasonality captures pattern |

---

## 🔧 Step 2: Model Development

### ETS Models Evaluated

| Model | Error | Trend | Seasonality | RMSE | MASE | Selected |
|-------|-------|-------|-------------|------|------|----------|
| ETS(M, A, M) | Multiplicative | Additive | Multiplicative | Higher | Higher | No |
| ETS(M, Ad, M) | Multiplicative | Additive Damped | Multiplicative | ~31,000 | 0.35 | Best ETS |
| ETS(Auto) | — | — | — | — | — | Confirmed (M, Ad, M) |

**Best ETS Model:** ETS(M, Ad, M) with Dampened Trend Parameter

**Why Dampened Trend?**

| Reason | Explanation |
|--------|-------------|
| Prevents over-projection | Damping reduces trend impact over forecast horizon |
| Better long-term accuracy | Avoids unrealistic exponential growth |
| Auto-selection confirmed | Alteryx ETS Auto chose same parameters |

### ARIMA Model Development

**ACF/PACF Analysis Process:**

| Step | Analysis | Finding | Action |
|------|----------|---------|--------|
| 1 | Initial ACF/PACF | Slowly decaying correlations with seasonal lags | Seasonal differencing needed |
| 2 | Seasonal Difference | Still correlated, slightly less | First differencing needed |
| 3 | Seasonal First Difference | Most significant lags removed | d=1, D=1 established |
| 4 | Residual ACF | Strong negative correlation at lag 1, cutoff pattern | MA(1) term needed |
| 5 | Seasonal Lags | No significant correlation at 12, 24, etc. | No seasonal AR/MA needed |

**Final ARIMA Model:** ARIMA(0, 1, 1)(0, 1, 0)[12]

| Parameter | Value | Meaning |
|-----------|-------|---------|
| p (AR) | 0 | No autoregressive terms |
| d (Diff) | 1 | First differencing applied |
| q (MA) | 1 | One moving average term |
| P (Seasonal AR) | 0 | No seasonal autoregressive |
| D (Seasonal Diff) | 1 | Seasonal differencing applied |
| Q (Seasonal MA) | 0 | No seasonal moving average |
| m (Period) | 12 | Monthly seasonality |

**ARIMA In-Sample Performance:**

| Metric | Value |
|--------|-------|
| RMSE | ~37,000 |
| MASE | 0.36 |

---

## 📈 Step 3: Model Comparison & Selection

### In-Sample Error Comparison

| Metric | ETS(M, Ad, M) | ARIMA(0,1,1)(0,1,0)[12] | Winner |
|--------|---------------|-------------------------|--------|
| RMSE | ~31,000 | ~37,000 | ETS |
| MASE | 0.35 | 0.36 | ETS |
| MAPE | Higher | Lower | ARIMA |
| ME | Higher | Lower | ARIMA |

**In-Sample Verdict:** Mixed results — ETS better on RMSE/MASE, ARIMA better on MAPE/ME.

### Holdout Sample Validation (Critical Decision Point)

| Metric | ETS(M, Ad, M) | ARIMA(0,1,1)(0,1,0)[12] | Winner |
|--------|---------------|-------------------------|--------|
| Holdout RMSE | Higher | **Better** | ARIMA |
| Holdout MASE | Higher | **Better** | ARIMA |
| Holdout MAPE | Higher | **Better** | ARIMA |
| Overall | — | — | **ARIMA** |

**Final Selection:** ARIMA(0,1,1)(0,1,0)[12]

**Rationale:**

| Reason | Explanation |
|--------|-------------|
| Holdout performance prioritized | Real-world predictive ability matters more than in-sample fit |
| Consistent superiority | ARIMA outperformed on all holdout metrics |
| Avoids overfitting | Better holdout = better generalization |

---

## 🎯 Step 4: Forecast Results

### 4-Period Forecast with Confidence Intervals

| Period | Point Forecast | 80% CI Lower | 80% CI Upper | 95% CI Lower | 95% CI Upper |
|--------|----------------|--------------|--------------|--------------|--------------|
| Month 1 | See Report | See Report | See Report | See Report | See Report |
| Month 2 | See Report | See Report | See Report | See Report | See Report |
| Month 3 | See Report | See Report | See Report | See Report | See Report |
| Month 4 | See Report | See Report | See Report | See Report | See Report |

### Confidence Interval Interpretation

| Interval | Meaning | Use Case |
|----------|---------|----------|
| **80% CI** | Narrower range, higher risk tolerance | Aggressive inventory planning |
| **95% CI** | Wider range, conservative | Risk-averse budgeting |

---

## 💡 Key Learnings

| Learning | Detail |
|----------|--------|
| **Holdout beats In-Sample** | Model with worse in-sample fit (ARIMA) had better holdout performance |
| **Dampened Trend Value** | ETS(M, Ad, M) outperformed ETS(M, A, M) — damping prevents over-projection |
| **Differencing Strategy** | Systematic ACF/PACF analysis guided differencing decisions (d=1, D=1) |
| **No Seasonal ARMA Needed** | Seasonal differencing alone captured seasonality (P=0, Q=0) |
| **Validation is Critical** | Without holdout testing, ETS would have been incorrectly selected |

---

## 🛠️ Tools & Techniques

| Category | Details |
|----------|---------|
| **Platform** | Alteryx Designer |
| **Time Series Methods** | ETS (Exponential Smoothing), ARIMA (Box-Jenkins) |
| **Decomposition** | Error, Trend, Seasonality analysis |
| **Diagnostics** | ACF, PACF, Seasonal Differencing |
| **Validation** | 4-period holdout sample |
| **Metrics** | RMSE, MASE, MAPE, ME |
| **Output** | 80% and 95% Confidence Intervals |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| `README.md` | This documentation file |
| `forecasting-workflow.yxmd` | Alteryx workflow with ETS and ARIMA models |
| `Forecast_VideoGameSales_Report.pdf` | Detailed analysis report with all charts |

---

## 📊 Model Summary Comparison

| Aspect | ETS(M, Ad, M) | ARIMA(0,1,1)(0,1,0)[12] |
|--------|---------------|-------------------------|
| **Error Handling** | Multiplicative | Differencing |
| **Trend Handling** | Additive Damped | Integrated (d=1) |
| **Seasonality** | Multiplicative | Seasonal Diff (D=1) |
| **In-Sample RMSE** | ~31,000 | ~37,000 |
| **In-Sample MASE** | 0.35 | 0.36 |
| **Holdout Performance** | Weaker | Stronger |
| **Selected** | No | **Yes** |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Capstone: Store Optimization | Clustering + Classification + Forecasting | [Link](../../00-capstone-projects/store-format-optimization/) |
| Country Segmentation for Market Expansion | Clustering | [Link](../../03-clustering/country-segmentation) |
| Diamond Price Prediction | Regression | [Link](../../01-regression/diamond-pricing) |
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
| LinkedIn | [Connect](https://www.linkedin.com/in/magedbaheig) |
| Kaggle | [Profile](https://www.kaggle.com/magedbaheig) |
| GitHub | [Follow](https://github.com/magedbaheig) |
| Email | [Reach Out](mailto:magedbaheig@gmail.com) |

📍 Cairo, Egypt

---

*Part of the [Data Science & ML Portfolio](https://github.com/magedbaheig/data-science-portfolio)*
