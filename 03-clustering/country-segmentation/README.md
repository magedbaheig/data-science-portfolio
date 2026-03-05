# 🌍 Country Segmentation for Market Expansion

**Clustering Analysis to Identify USA-Similar Countries for Retail Expansion**

![Alteryx](https://img.shields.io/badge/Alteryx-Workflow-orange)
![Tableau](https://img.shields.io/badge/Tableau-Visualization-blue)
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
| **Type** | Unsupervised Learning (Clustering/Segmentation) |
| **Objective** | Identify countries similar to USA for international expansion |
| **Best Method** | Neural Gas (3 clusters) |
| **Validation** | Rand Index, CH Index, Tableau map visualization |

---

## 🛠️ Implementations

| Tool | Status | Description |
|------|--------|-------------|
| **Alteryx** | ✅ Complete | Clustering workflow with PCA and model comparison |
| **Tableau** | ✅ Complete | Geographic visualization for validation |
| **Excel** | ✅ Complete | Variable exploration and analysis |
| **Python** | 🔜 Planned | scikit-learn implementation |
| **KNIME** | 🔜 Planned | Open-source workflow replication |

---

## 🎯 Business Problem

A retail store chain with operations in the United States wants to **expand internationally**. The company needs to identify which countries are most similar to the USA across multiple dimensions:

| Dimension | Description |
|-----------|-------------|
| **Economic** | GDP, income levels, trade |
| **Demographic** | Population, age distribution |
| **Educational** | Literacy, enrollment rates |
| **Environmental** | Climate, resources |

### Goal

Find countries in the **same cluster as the USA** to prioritize for expansion, assuming similar market conditions will lead to similar business success.

---

## 🔧 Technical Approach

### 1. Problem Definition

| Aspect | Definition |
|--------|------------|
| **Problem Type** | Unsupervised Learning |
| **Data Characteristics** | Unlabeled country-level metrics |
| **Model Required** | Clustering Model |

### 2. Data Preparation

| Step | Description |
|------|-------------|
| **Data Collection** | Gathered country-level economic, demographic, educational, environmental data |
| **Data Inspection** | Assessed quality and completeness |
| **Data Cleansing** | Handled missing values and inconsistencies |
| **Data Processing** | Structured data for clustering analysis |

### 3. Dimensionality Reduction

| Technique | Purpose |
|-----------|---------|
| **PCA (Principal Component Analysis)** | Reduce number of variables while preserving variance |
| **Standardization** | Normalize variables to same scale |

### 4. Clustering Methodology

#### Methods Compared

| Method | Description | Evaluation |
|--------|-------------|------------|
| **K-Means** | Centroid-based clustering | Tested |
| **K-Medians** | Median-based clustering | Tested |
| **Neural Gas** | Topology-preserving clustering | ✅ Selected |

#### Cluster Number Determination

| Metric | Purpose |
|--------|---------|
| **Rand Index** | Measure cluster agreement |
| **Calinski-Harabasz (CH) Index** | Evaluate cluster separation |
| **Median and Spread Analysis** | Determine optimal k |

### 5. Final Model Configuration

| Parameter | Value |
|-----------|-------|
| **Method** | Neural Gas |
| **Number of Clusters** | 3 |
| **Validation** | Visual + Statistical |

---

## 📈 Results

### Clustering Output

| Cluster | Characteristics | USA Membership |
|---------|-----------------|----------------|
| Cluster 1 | [Similar to USA profile] | ✅ USA in this cluster |
| Cluster 2 | [Different profile] | — |
| Cluster 3 | [Different profile] | — |

### Model Selection Rationale

| Criterion | Neural Gas Performance |
|-----------|----------------------|
| **Rand Index** | Best median and spread |
| **CH Index** | Strong cluster separation |
| **Visual Validation** | Geographic patterns make sense |

### Expansion Recommendations

Countries in the same cluster as USA are recommended for expansion priority, based on similarity in:
- Economic indicators
- Demographic patterns
- Educational metrics
- Environmental factors

---

## 📊 Validation

### Statistical Validation

| Metric | Purpose | Result |
|--------|---------|--------|
| **Rand Index** | Cluster stability | Evaluated across k values |
| **CH Index** | Cluster quality | Used for k selection |

### Visual Validation (Tableau)

| Validation Step | Description |
|-----------------|-------------|
| **Geographic Map** | Plotted clusters on world map |
| **Sense Check** | Verified geographic patterns align with expectations |
| **Business Logic** | Confirmed similar countries cluster together |

---

## 💡 Key Learnings

| Learning | Details |
|----------|---------|
| **PCA Importance** | Dimensionality reduction essential for high-dimensional clustering |
| **Method Comparison** | Neural Gas outperformed K-Means and K-Medians for this data |
| **Multiple Validation** | Statistical + visual validation ensures robust results |
| **Business Context** | Clustering must align with business logic |
| **Cluster Interpretation** | Understanding what makes clusters different is as important as creating them |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| README.md | This documentation file |
| Practice Project_Segmentation_MagedSolution.yxmd | Alteryx clustering workflow |
| Validating Through Visualization_Maged.twbx | Tableau validation dashboard |
| variables_catalog_MagedExplore.xlsx | Variable exploration analysis |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| Capstone: Store Format Optimization | Clustering + Classification + Time Series | [Link](../../00-capstone-projects/store-format-optimization/) |
| Credit Default Risk | Classification | [Link](../../02-classification/credit-default-risk/) |
| Pet Store Sales (Pawdacity) | Data Prep + Predictor Selection | [Link](../../01-regression/pet-store-sales/) |

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
