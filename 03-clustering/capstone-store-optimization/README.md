# 🏪 Predictive Analytics Capstone: Store Format Optimization & Sales Forecasting

**End-to-End Pipeline: Clustering → Classification → Time Series Forecasting**

![Alteryx](https://img.shields.io/badge/Alteryx-Workflow-orange)
![Tableau](https://img.shields.io/badge/Tableau-Visualization-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Udacity](https://img.shields.io/badge/Udacity-Capstone-brightgreen)

---

## 📋 Project Overview

| Aspect | Details |
|--------|---------|
| **Course** | Udacity Predictive Analytics for Business (Bertelsmann) |
| **Year** | 2021 |
| **Type** | Capstone Project (Clustering + Classification + Time Series) |
| **Objective** | Optimize store formats for existing stores, classify new stores, and forecast produce sales |
| **Review** | ✅ Meets Specifications |

---

## 🎯 Business Problem

A grocery chain needs to:
1. **Segment 85 existing stores** into optimal format categories based on sales patterns
2. **Classify 10 new stores** into the most appropriate format
3. **Forecast produce sales** for inventory and supply chain planning

---

## 🛠️ Technical Pipeline

| Task | Method | Outcome |
|------|--------|---------|
| **Task 1: Clustering** | K-Means (3 Clusters) | 85 stores segmented into 3 formats |
| **Task 2: Classification** | Boosted Model | 10 new stores classified (76% accuracy) |
| **Task 3: Forecasting** | ETS(M,N,M) | Produce sales forecast with 80%/95% CI |

---

## 📊 Task 1: Store Format Clustering

### Clustering Model Comparison

| Model | Clusters | Rand Index | CH Index | Selected |
|-------|----------|------------|----------|----------|
| K-Means | 3 | Tight | Tight | ✅ Best |
| K-Medians | 3 | Good | Good | ❌ |
| Neural Gas | 3 | Higher Mean | Better Compactness | ❌ (per Udacity guidance) |

### Optimal Cluster Selection

| Metric | Decision Rationale |
|--------|---------------------|
| **K-Centroids Diagnostics** | Box-whisker plots show tight indices at 3 clusters |
| **Rand Index** | Compact spread for 3-cluster solution |
| **CH Index** | Calinski-Harabasz validates 3-cluster optimality |

### Store Format Distribution

| Format | Store Count | Key Characteristic |
|--------|-------------|-------------------|
| **Format 1** | 25 stores | Lowest Floral & Produce sales |
| **Format 2** | 35 stores | Highest Floral sales |
| **Format 3** | 25 stores | Highest General Merchandise sales |

### Cluster Differentiation

| Category | Format 1 | Format 2 | Format 3 |
|----------|----------|----------|----------|
| **Floral** | Lowest | Highest | Medium |
| **General Merchandise** | Medium | Medium | Highest |
| **Produce** | Lowest | Higher | Higher |

---

## 🎯 Task 2: New Store Classification

### Classification Model Comparison

| Metric | Decision Tree | Forest Model | Boosted Model |
|--------|---------------|--------------|---------------|
| **Overall Accuracy** | 65.0% | 71.0% | **76.0%** ✅ |
| **F1 Score** | 67.0% | 75.0% | **83.0%** ✅ |
| **Error Rate** | 33.0% | 25.0% | **17.0%** ✅ |
| **Precision Avg** | 66.0% | 70.0% | **79.0%** ✅ |
| **Recall Avg** | 67.0% | 75.0% | **83.0%** ✅ |

### Top 3 Predictive Variables

| Rank | Variable | Description |
|------|----------|-------------|
| 1 | **Age0to9** | Population age 0-9 in area |
| 2 | **Hval750Kplus** | Home values $750K+ |
| 3 | **Age65Plus** | Population age 65+ in area |

### New Store Classifications

| Store | Predicted Format |
|-------|------------------|
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

### Boosted Model Performance by Cluster

| Metric | Cluster 1 | Cluster 2 | Cluster 3 |
|--------|-----------|-----------|-----------|
| **Precision** | 100.0% | 71.0% | 67.0% |
| **Recall** | 50.0% | 100.0% | 100.0% |
| **Error Rate** | 50.0% | 0.0% | 0.0% |

---

## 📈 Task 3: Time Series Forecasting

### Time Series Analysis

| Component | Analysis | Method |
|-----------|----------|--------|
| **Error** | Growing over time | Multiplicative (M) |
| **Trend** | Horizontal/Stationary | None (N) |
| **Seasonality** | Shrinking slightly over time | Multiplicative (M) |

### Final Model: ETS(M,N,M)

| Metric | ETS(M,N,M) | ETS(M,Ad,M) | ARIMA(0,1,1)(0,1,1)[12] |
|--------|------------|-------------|-------------------------|
| **RMSE** | 969,000 | Higher | 935,000 |
| **MASE** | 0.44 | Higher | 0.35 |
| **AIC** | 1,279 | Higher | 849 |
| **Selected** | ✅ Best | ❌ | ❌ |

### Model Selection Rationale

| Criterion | Decision |
|-----------|----------|
| **Holdout Sample Validation** | ETS outperforms ARIMA on holdout |
| **MASE < 1.00** | Both models pass threshold |
| **Forecast Stability** | ETS more stable on validation |

### ARIMA Model Development

| Step | ACF/PACF Observation | Action |
|------|---------------------|--------|
| Initial Series | Slowly decaying correlations | Seasonal differencing needed |
| Seasonal Difference | Still correlated | First difference needed |
| Seasonal First Difference | Most lags removed | d=1, D=1 established |
| Final Model | MA(1) + Seasonal MA(1) | ARIMA(0,1,1)(0,1,1)[12] |

### Forecast Output

| Forecast Type | Confidence Intervals |
|---------------|---------------------|
| **Existing Stores** | 80% and 95% CI |
| **New Stores** | 80% and 95% CI |

---

## 🔧 Technical Approach Summary

### End-to-End Pipeline

┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ CLUSTERING │ → │ CLASSIFICATION │ → │ FORECASTING │
│ (K-Means) │ │ (Boosted Model) │ │ (ETS M,N,M) │
└─────────────────┘ └─────────────────┘ └─────────────────┘
│ │ │
▼ ▼ ▼
85 Stores → 10 New Stores → Produce Sales
3 Formats Format Assignment Forecast


### Validation Strategy

| Task | Validation Method |
|------|-------------------|
| **Clustering** | Rand Index, CH Index, Box-Whisker Diagnostics |
| **Classification** | 20% Holdout (Random Seed = 3) |
| **Time Series** | 6-Month Holdout Sample |

---

## 📁 Project Structure

predictive-analytics-capstone/
├── README.md
├── data/
│ ├── store_data.csv
│ ├── new_stores.csv
│ └── produce_sales.csv
├── workflows/
│ ├── Task1_Clustering.yxmd
│ ├── Task2_Classification.yxmd
│ └── Task3_TimeSeries.yxmd
├── visualizations/
│ └── Store_Locations_Tableau.twbx
├── reports/
│ └── Capstone_Report.pdf
└── submission/
└── Udacity_Review.pdf


---

## 📊 Visualizations

### Tableau Dashboard Components

| Visualization | Purpose |
|---------------|---------|
| **Store Location Map** | Geographic distribution with cluster colors |
| **Cluster by Total Sales** | Size encoding for sales volume |
| **Sales by Category** | Format differentiation analysis |

### Time Series Plots

| Plot | Purpose |
|------|---------|
| **Decomposition Plot** | Error, Trend, Seasonality identification |
| **ACF/PACF** | ARIMA parameter determination |
| **Forecast Plot** | Historical + Predicted with CI bands |

---

## 💡 Key Learnings

| Learning | Details |
|----------|---------|
| **Model Comparison** | Systematic evaluation across 3 clustering + 3 classification + 6 time series models |
| **Validation Rigor** | Multiple validation strategies for each task type |
| **End-to-End Pipeline** | Integration of unsupervised → supervised → forecasting |
| **Business Translation** | Each task directly supports operational decisions |
| **Tool Integration** | Alteryx workflows + Tableau visualizations |

---

## 📈 Results Summary

| Task | Key Outcome | Business Impact |
|------|-------------|-----------------|
| **Clustering** | 3 optimal formats identified | Store categorization framework |
| **Classification** | 76% accuracy on new stores | Confident format assignment |
| **Forecasting** | ETS(M,N,M) with 80%/95% CI | Inventory planning support |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Customer Segmentation (Arvato) | Clustering + PCA | [Link](../arvato-customer-segmentation/) |
| Diamond Price Prediction | Regression | [Link](../diamond-price-prediction/) |
| Video Game Demand Forecasting | Time Series | [Link](../video-game-forecasting/) |

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
