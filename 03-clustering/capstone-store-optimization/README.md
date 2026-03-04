# 🏪 Predictive Analytics Capstone: Store Format Optimization & Sales Forecasting

**End-to-End Retail Analytics: Clustering → Classification → Time Series Forecasting**

![Alteryx](https://img.shields.io/badge/Alteryx-Workflow-orange)
![Tableau](https://img.shields.io/badge/Tableau-Visualization-blue)
![Excel](https://img.shields.io/badge/Excel-Analysis-green)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Course](https://img.shields.io/badge/Udacity-Predictive%20Analytics%20for%20Business-blueviolet)

---

## 📋 Project Overview

| Aspect | Details |
|--------|---------|
| **Course** | Udacity Predictive Analytics for Business Nanodegree (Bertelsmann Scholarship) |
| **Year** | 2021 |
| **Type** | Capstone — Multi-method end-to-end retail analytics |
| **Tasks** | Clustering → Classification → Time Series Forecasting |
| **Tools** | Alteryx, Tableau, Excel |
| **Scope** | 85 existing stores + 10 new stores; multi-year daily sales data |

---

## 🎯 Business Problem & Objective

A retail grocery chain needed to solve **three interconnected business problems**:

| Task | Business Question | Method |
|------|-------------------|--------|
| **Task 1** | What are the natural store formats among existing stores? | Unsupervised Clustering |
| **Task 2** | Which format should each new store be assigned to? | Supervised Classification |
| **Task 3** | What are the produce sales forecasts for all stores? | Time Series Forecasting |

The analysis follows an end-to-end decision pipeline: **segment → classify → forecast** — translating model outputs into concrete business recommendations.

---

## 🔄 End-to-End Pipeline

| Stage | Method | Input | Output |
|-------|--------|-------|--------|
| **Stage 1** | K-Means Clustering | 85 existing stores | 3 store formats identified |
| **Stage 2** | Boosted Classification | 10 new stores | Format assignment per store |
| **Stage 3** | ETS(M,N,M) Forecasting | All stores by cluster | Produce sales forecast with CI |

**Pipeline Flow:** Clustering Outputs → Classification Labels → Forecast Groups

### Validation Strategy

| Task | Validation Method |
|------|-------------------|
| **Clustering** | Rand Index, CH Index, Box-Whisker Diagnostics |
| **Classification** | 20% Holdout (Random Seed = 3) |
| **Time Series** | 6-Month Holdout Sample |

---

## 📁 Project Structure

| Folder/File | Description |
|-------------|-------------|
| `README.md` | This documentation file |
| `task1-store-formats/` | Clustering workflows and Tableau map |
| `task1-store-formats/clustering-workflow.yxmd` | Alteryx: K-Means, K-Medians, Neural Gas |
| `task1-store-formats/store-map-tableau.twbx` | Tableau: store locations by cluster + sales |
| `task2-new-store-classification/` | Classification workflows |
| `task2-new-store-classification/classification-workflow.yxmd` | Alteryx: Decision Tree, Forest, Boosted |
| `task3-produce-forecasting/` | Time series workflows and visualizations |
| `task3-produce-forecasting/forecasting-workflow.yxmd` | Alteryx: ETS and ARIMA models |
| `task3-produce-forecasting/forecast-visualization.twbx` | Tableau: historical + forecast chart |
| `Capstone_Report_MagedBaheig.pdf` | Full submission report |

---

## 🔧 Task 1: Determine Store Formats for Existing Stores

### Objective

Identify the optimal number of natural store formats using clustering on 85 existing stores.

### Methodology

**Step 1 — Model Comparison via K-Centroids Diagnostics (Alteryx)**

Three clustering algorithms were evaluated:

| Algorithm | Evaluated | Final Selection |
|-----------|-----------|-----------------|
| K-Means | ✅ | ✅ Selected (per Udacity guidance) |
| K-Medians | ✅ | — |
| Neural Gas | ✅ | Note: Outperformed at Cluster 3 (CH Index) |

**Analyst Note:** Neural Gas demonstrated superior CH Index performance at 3 clusters (higher mean/median, lower range/IQR). K-Means was used per course guidance. In a production context, Neural Gas would be the recommended choice.

**Step 2 — Optimal Cluster Count**

Using Rand Index and Calinski-Harabasz (CH) Index box-whisker plots:

| Metric | Signal |
|--------|--------|
| Rand Index | Tight distribution at k=3 |
| CH Index | Clear separation at k=3 |
| **Decision** | **3 clusters (store formats)** |

### Results

**Store Distribution per Format:**

| Store Format | Number of Stores | Profile Highlight |
|--------------|------------------|-------------------|
| Format 1 | 25 stores | Lowest Produce and Floral sales |
| Format 2 | 35 stores | Highest Floral sales |
| Format 3 | 25 stores | Highest General Merchandise sales |

**Key Cluster Differentiators (by sales category):**

| Category | Winner | Loser |
|----------|--------|-------|
| Floral | Format 2 (highest) | Format 1 (lowest) |
| General Merchandise | Format 3 (highest) | — |
| Produce | Format 2 and 3 (higher) | Format 1 (lowest) |

**Tableau Visualization:** Store locations mapped by cluster (color) and total sales (size).

---

## 🔧 Task 2: Predict Store Formats for 10 New Stores

### Objective

Use supervised classification to assign each of 10 new stores to the optimal format identified in Task 1.

### Methodology

**Problem Type:** Multi-class classification (3 categories: Format 1, 2, 3)

**Models Evaluated** (20% validation split, Random Seed = 3):

| Measure | Decision Tree | Forest | Boosted Model |
|---------|---------------|--------|---------------|
| Overall Accuracy | 65.0% | 71.0% | **76.0%** |
| F1 Score | 67.0% | 75.0% | **83.0%** |
| Error Rate Avg | 33.0% | 25.0% | **17.0%** |
| Precision Avg | 66.0% | 70.0% | **79.0%** |
| Recall Avg | 67.0% | 75.0% | **83.0%** |

**Selected Model:** Boosted Model — outperformed on all 5 evaluation criteria.

**Top 3 Predictor Variables:**

| Rank | Variable | Relevance |
|------|----------|-----------|
| 1 | Age0to9 | Young families — produce/floral preference |
| 2 | Hval750Kplus | High-value homes — premium product mix |
| 3 | Age65Plus | Senior demographics — format behavior patterns |

**Boosted Model Performance by Cluster:**

| Metric | Cluster 1 | Cluster 2 | Cluster 3 |
|--------|-----------|-----------|-----------|
| Precision | 100.0% | 71.0% | 67.0% |
| Recall | 50.0% | 100.0% | 100.0% |
| Error Rate | 50.0% | 0.0% | 0.0% |

### New Store Assignments

| Store | Assigned Format |
|-------|-----------------|
| S0086 | Format 1 |
| S0087 | Format 2 |
| S0088 | Format 3 |
| S0089 | Format 2 |
| S0090 | Format 2 |
| S0091 | Format 3 |
| S0092 | Format 2 |
| S0093 | Format 3 |
| S0094 | Format 2 |
| S0095 | Format 2 |

**New Store Summary:** 1 x Format 1 — 6 x Format 2 — 3 x Format 3

---

## 🔧 Task 3: Predict Produce Sales (ETS Time Series Forecasting)

### Objective

Forecast monthly produce sales for existing stores and new stores (by cluster average).

### Data Preparation

**Existing Stores:**

| Step | Action |
|------|--------|
| 1 | Aggregated daily store-level data to Monthly Produce Total Sales |
| 2 | Group by: Year, Month then Sum(Produce) |
| 3 | 6-month holdout sample (2015-07 to 2015-12) for model validation |

**New Stores:**

| Step | Action |
|------|--------|
| 1 | Aggregated to cluster-level monthly averages |
| 2 | Group by: Store, Cluster, Year, Month then Sum(Produce) |
| 3 | Then Avg by Cluster, scaled by store count per cluster |

### Time Series Decomposition

| Component | Observed Pattern | Treatment |
|-----------|------------------|-----------|
| **Error** | Growing over time | Multiplicative **(M)** |
| **Trend** | Stationary / horizontal | None **(N)** |
| **Seasonality** | Shrinking peaks (Jul highs / Sep-Oct valleys) | Multiplicative **(M)** |

**Final Model:** ETS(M, N, M)

### Model Comparison

**ETS Models Evaluated:**

| Model | MASE | AIC | Notes |
|-------|------|-----|-------|
| ETS(M, N, M) | 0.44 | 1,279 | Selected — best holdout; matches Auto |
| ETS(M, Ad, M) | Higher | Higher | Dampened parameter variant |
| ETS(Auto) | — | — | Confirmed (M, N, M) selection |

**ARIMA Models Evaluated:**

| Model | MASE | AIC | Notes |
|-------|------|-----|-------|
| ARIMA(0,1,1)(0,1,1)12 | 0.35 | 849 | Strong in-sample; weaker holdout |
| ARIMA(0,1,1)(0,2,1)12 | — | 504 | Better AIC but overfitting on holdout |
| ARIMA Auto (1,0,0)(1,1,0)12 | — | — | Auto-selected; not optimal |

**Final Decision — ETS vs ARIMA (Holdout Sample):**

| Metric | ETS(M,N,M) | ARIMA(0,1,1)(0,1,1)12 | Winner |
|--------|------------|------------------------|--------|
| Holdout RMSE | Better | Higher | ETS |
| Holdout MASE | Better | Higher | ETS |
| Holdout MAPE | Better | — | ETS |
| Overfitting Risk | Low | Low-Moderate | ETS |

**ETS(M, N, M) selected for all forecasts** (existing + new stores).

### Forecast Output

Forecasts produced with **80% and 95% confidence intervals** for:

- All existing stores (aggregate monthly produce sales)
- Each new store cluster scaled by store count and summed for total new store forecast

---

## 📈 Results Summary

| Task | Method | Key Outcome |
|------|--------|-------------|
| **Clustering** | K-Means (3 clusters) | 85 stores segmented into 3 formats (25/35/25 split) |
| **Classification** | Boosted Model | 76% accuracy, 83% F1, 10 new stores assigned |
| **Forecasting** | ETS(M,N,M) | MASE 0.44, 80%/95% CI forecasts |

**Models Evaluated:** 3 clustering + 3 classification + 6 time series = **12 total models benchmarked**

---

## 💡 Key Learnings

| Learning | Detail |
|----------|--------|
| **Pipeline Thinking** | Clustering outputs become classification labels; classification outputs determine forecast groups — true end-to-end design |
| **Algorithm Benchmarking** | Neural Gas outperformed K-Means for CH Index at k=3; production recommendation would differ from course guidance |
| **Overfitting vs AIC Trade-off** | ARIMA(0,1,1)(0,2,1)12 had better AIC but overfit the holdout — real-world validation matters more than in-sample fit |
| **Holdout Over In-Sample** | Final model selection based on holdout performance, not in-sample errors alone |
| **Business Framing** | Each task translated directly into a business action: format assignment, merchandising strategy, inventory planning |

---

## 🛠️ Tools & Techniques

| Category | Details |
|----------|---------|
| **Platform** | Alteryx Designer |
| **Visualization** | Tableau Public |
| **Clustering** | K-Means, K-Medians, Neural Gas |
| **Cluster Validation** | Rand Index, Calinski-Harabasz (CH) Index |
| **Classification** | Decision Tree, Random Forest, Gradient Boosted Model |
| **Time Series** | ETS(M,N,M), ARIMA(0,1,1)(0,1,1)12 |
| **TS Analysis** | ACF/PACF, Decomposition (Error/Trend/Seasonality) |
| **Validation Metrics** | F1 Score, Precision, Recall, Accuracy, RMSE, MASE, AIC |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Country Segmentation | Clustering (PCA + Neural Gas) | [Link](../country-segmentation/) |
| Credit Default Risk | Classification (RF, GBM) | [Link](../../02-classification/credit-default-risk/) |
| Video Game Forecasting | Time Series (ETS/ARIMA) | [Link](../../04-time-series/video-game-forecasting/) |
| Insurance Prediction (Kaggle) | Regression (LightGBM) | [Link](../../01-regression/insurance-claims-kaggle/) |

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
| GitHub | [Maged-Baheig](https://github.com/Maged-Baheig) |
| Email | magedbaheig@gmail.com |

📍 Cairo, Egypt

---

*Part of the [Data Science & ML Portfolio](https://github.com/Maged-Baheig/data-science-portfolio)*
