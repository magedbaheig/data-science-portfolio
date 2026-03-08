# 🎯 Data Science & Machine Learning Portfolio

**Maged Baheig | Self-Directed Learning & Practice | 2020–2021**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/magedbaheig)
[![Kaggle](https://img.shields.io/badge/Kaggle-Top%2030%25-gold)](https://www.kaggle.com/magedbaheig)
[![Email](https://img.shields.io/badge/Email-Contact-red)](mailto:magedbaheig@gmail.com)

---

## 🚀 Overview

This portfolio showcases **12 end-to-end data science projects** demonstrating full-stack ML proficiency—from data acquisition to business recommendation:

| Discipline | Projects | Highlights |
|------------|----------|------------|
| 📈 **Supervised Learning (Regression)** | 5 | R² up to 0.92; $8.2M auction bid; Top 30% Kaggle |
| 🎯 **Supervised Learning (Classification)** | 1 | 4 models compared; 79.3% accuracy; 408 creditworthy identified |
| 🔮 **Unsupervised Learning (Clustering)** | 1 | PCA + Neural Gas; Rand/CH Index validation |
| 📊 **Time Series Forecasting** | 1 | ETS vs ARIMA; Holdout-based selection; 80/95% CI |
| 🧪 **A/B Testing & Experimentation** | 1 | 41% lift; P=0.000; $6.9M expected impact |
| 🔧 **Data Wrangling & Engineering** | 2 | API integration; 30 data issues resolved; Interactive CLI |
| 🏆 **Capstone (Multi-Method)** | 1 | Clustering → Classification → Forecasting pipeline |

**Portfolio Highlight:** Built a technical sandbox to master the full data science lifecycle—directly transferred to enterprise projects at Telecom Egypt: customer personas (22M+ customers), churn prediction (74%+ recall), and CX driver analysis (R² 0.45–0.99).

---

## 📊 Portfolio at a Glance

| Metric | Value |
|--------|-------|
| **Total Projects** | 12 end-to-end |
| **Total Records Processed** | 500K+ |
| **Kaggle Ranking** | **Top 30%** (8,040 participants; 60,288 submissions) |
| **Models Built & Compared** | 25+ (including 12 in Capstone alone) |
| **ML Disciplines Covered** | 6 |
| **Tool Stacks Used** | 4 (Python, Alteryx, Tableau, Excel) |

---

## 📁 Repository Structure

| Folder | Description | Projects |
|--------|-------------|----------|
| `00-capstone-projects/` | Multi-method end-to-end projects | Store Format Optimization |
| `01-regression/` | Supervised learning (continuous targets) | Insurance, Diamond, Catalog, School, Pet Store |
| `02-classification/` | Supervised learning (categorical targets) | Credit Default Risk |
| `03-clustering/` | Unsupervised learning | Country Segmentation |
| `04-time-series/` | Forecasting models | Video Game Forecasting |
| `05-experimentation/` | A/B testing and experiments | Coffee Shop Menu Launch |
| `06-data-wrangling/` | Data engineering and cleaning | WeRateDogs, US Bikeshare |
| `07-training-and-capability-building/` | Leadership, Training & Capability Building | Training Programs Overview |

---

## 🏆 Featured Project: Predictive Analytics Capstone

### [Store Format Optimization](./00-capstone-projects/store-format-optimization/)

**End-to-End Pipeline: Clustering → Classification → Time Series**

| Task | Method | Key Outcome |
|------|--------|-------------|
| **Store Segmentation** | K-Means (3 clusters) | 85 stores → 3 formats (25/35/25 split) |
| **New Store Classification** | Boosted Model | 76% accuracy, 83% F1, 10 stores assigned |
| **Sales Forecasting** | ETS(M,N,M) | MASE 0.44, 80%/95% confidence intervals |

**Models Benchmarked:** 3 clustering (K-Means, K-Medians, Neural Gas) + 3 classification (Decision Tree, Random Forest, Boosted) + 6 time series (ETS variants, ARIMA variants) = **12 total**

**Business Impact:** Solved inventory problem—product surpluses and shortages from treating 85 stores identically.

---

## 📈 Regression Projects (5)

### Python-Based

| Project | Model | Scale | Key Results |
|---------|-------|-------|-------------|
| [**Insurance Claims (Kaggle)**](./01-regression/kaggle-insurance-prediction/) | LightGBM | 300K train / 200K test | **Top 30%** of 8,040; RMSE 0.725; 2-fold CV |

### Alteryx/Excel-Based

| Project | Model | Scale | Key Results |
|---------|-------|-------|-------------|
| [**Diamond Pricing**](./01-regression/diamond-pricing/) | MLR (Dummy Variables) | 5K train / 3K predict | **R² 0.92**; Bid: **$8.2M** |
| [**Catalog Demand**](./01-regression/catalog-demand/) | MLR | 2.3K train / 250 predict | **R² 0.84**; Profit: **$21,987** |

### Data Preparation with Statistical Predictor Selection

| Project | Focus | Key Results |
|---------|-------|-------------|
| [**School Cost Prediction**](./01-regression/school-cost-prediction/) | Data Cleaning (messy data) | Regression-ready dataset; validated predictors |
| [**Pet Store Sales**](./01-regression/pet-store-sales/) | Outlier Analysis | Best predictor **R² 0.82**; Gillette outlier removed |

**Note:** Data preparation projects used R², P-Value, and correlation analysis to statistically validate predictor variables—not just cleaning, but ensuring model-readiness.

---

## 🎯 Classification Project (1)

| Project | Models Compared | Best Model | Key Results |
|---------|-----------------|------------|-------------|
| [**Credit Default Risk**](./02-classification/credit-default-risk/) | Logistic Regression, Decision Tree, Random Forest, Boosted | **Random Forest** | **79.3% accuracy**, 73.7% AUC, 408 creditworthy from 500 applicants |

**Selection Criteria:** Best overall accuracy + largest AUC + acceptable bias (6.5%)

---

## 🔮 Clustering Project (1)

| Project | Techniques | Validation | Key Results |
|---------|------------|------------|-------------|
| [**Country Segmentation**](./03-clustering/country-segmentation/) | PCA + Neural Gas | Rand Index, CH Index, Tableau Map | 3 clusters; USA-similar countries identified for market expansion |

**Methods Compared:** K-Means, K-Medians, Neural Gas → Neural Gas selected for superior CH Index performance.

---

## 📊 Time Series Project (1)

| Project | Models Compared | Best Model | Key Results |
|---------|-----------------|------------|-------------|
| [**Video Game Forecasting**](./04-time-series/video-game-forecasting/) | ETS(M,A,M), ETS(M,Ad,M), ARIMA(0,1,1)(0,1,0)[12] | **ARIMA** | RMSE ~37K, MASE 0.36; 4-month forecast |

**Key Insight:** ARIMA selected despite worse in-sample fit—holdout validation revealed better generalization (avoiding overfitting trap).

---

## 🧪 A/B Testing Project (1)

| Project | Design | Test Period | Key Results |
|---------|--------|-------------|-------------|
| [**Coffee Shop Menu Launch**](./05-experimentation/coffee-shop-menu-launch/) | Matched-Pair (10 treatment : 20 control) | 12 weeks | **41% lift**, P=0.000, **$6.9M** expected impact |

**Methodology:** 4 control variables (Trend, Seasonality, AvgMonthSales, Region); multicollinearity handled; regional breakdown (West 36.3%, Central 45.8%).

**Recommendation:** Roll out new menu to all stores—exceeded 18% practical significance threshold.

---

## 🔧 Data Wrangling Projects (2)

| Project | Data Sources | Techniques | Key Results |
|---------|--------------|------------|-------------|
| [**Twitter WeRateDogs**](./06-data-wrangling/twitter-weratedogs/) | 3 (CSV, TSV, Twitter API) | tweepy, requests, regex | **30 issues resolved** (22 quality, 6 tidiness, 2 FE); 6 research questions answered |
| [**US Bikeshare Explorer**](./06-data-wrangling/us-bikeshare/) | 3 cities (CSV) | Pandas, Interactive CLI | **9 modular functions**; 5 statistics categories; error handling |

---

## 🛠️ Technical Stack

| Category | Technologies |
|----------|--------------|
| **Programming** | Python (Pandas, NumPy, scikit-learn, XGBoost, LightGBM, Matplotlib, Seaborn, tweepy, requests) |
| **Analytics Platforms** | Alteryx Designer, Tableau, Jupyter Notebook, Excel |
| **ML Methods** | Linear/Logistic Regression, Decision Tree, Random Forest, Gradient Boosting, K-Means, K-Medians, Neural Gas, PCA, ETS, ARIMA |
| **Experimentation** | A/B Testing, Matched-Pair Design, Hypothesis Testing |
| **Data Engineering** | API Integration, Multi-Format Processing (CSV, JSON, TSV), Data Quality Assessment |

---

## 📚 Skills Demonstrated

| Skill Category | Specific Skills |
|----------------|-----------------|
| **Supervised ML** | Regression (Linear, Boosted), Classification (Logistic, Tree, Forest, GBM) |
| **Unsupervised ML** | Clustering (K-Means, Neural Gas), Dimensionality Reduction (PCA) |
| **Time Series** | ETS, ARIMA, Decomposition (E/T/S), ACF/PACF Analysis |
| **Experimentation** | A/B Testing, Matched-Pair Design, Statistical/Practical Significance |
| **Data Engineering** | API Integration, Multi-Source Wrangling, Quality Assessment |
| **Validation** | Cross-Validation, Holdout Testing, R², AUC-ROC, RMSE, MASE, F1 |
| **Business Translation** | Profit Estimation, Bidding Strategy, Expansion Recommendation, Go/No-Go Decisions |

---

## 📜 Certifications

| Certification | Provider | Year |
|---------------|----------|------|
| Microsoft Certified PL-300: Data Analyst Associate | Microsoft  | 2021 |
| Data Analysis Professional Nanodegree | Udacity (FWD Egypt) | 2020 |
| Predictive Analytics for Business Nanodegree | Udacity (Bertelsmann) | 2021 |

---

## 💼 Corporate Application

This self-directed portfolio directly informed **enterprise applications** at Telecom Egypt:

| Technique | Portfolio Project | Corporate Application |
|-----------|-------------------|----------------------|
| **Clustering** | Country Segmentation, Capstone | Customer Personas (22M+ FBB/Mobile) |
| **Regression** | Diamond, Catalog, Kaggle | CX Driver Analysis (R² 0.45–0.99) |
| **Time Series** | Video Game, Capstone | Demand Forecasting Concepts |
| **A/B Testing** | Coffee Shop | Experiment Design Methodology |
| **Data Wrangling** | WeRateDogs, Bikeshare | VoC Text Analytics (~97% time reduction) |

**Bottom Line:** This portfolio demonstrates not just tool knowledge, but **proven modeling, validation, and business translation capability**—the foundation for my CX Analytics leadership at Telecom Egypt.

---

## 👤 Author

**Maged Baheig**

CX Data Analytics & Insights Manager | Telecom Egypt
Freelance Data Science Trainer | 30+ programs, 540+ hours, 250+ professionals, 98% satisfaction


- 
| Platform | Link |
|----------|------|
| LinkedIn | [Connect](https://www.linkedin.com/in/magedbaheig) |
| Kaggle | [Profile](https://www.kaggle.com/magedbaheig) |
| GitHub | [Follow](https://github.com/magedbaheig) |
| Email | [Reach Out](mailto:magedbaheig@gmail.com) |

📍 **Location:** Cairo, Egypt

---

## 💼 Available for Opportunities

| Opportunity Type | Areas |
|------------------|-------|
| **Full-Time Roles** | Data Analytics Manager, Data Science Manager, CX Analytics/Insights Manager |
| **Freelance** | Data Science & Analytics Projects, Training & Workshops |
| **Training** | Data Science, Data Analytics, Power BI (PL-300) , Excel, Python, SQL, ML, Statistics, Data Visualization, CX Analytics, Customer Experience Management (CXM), Business Analytics (CRISP-DM) |

---

## ⭐ Acknowledgments

| Entity | Contribution |
|--------|--------------|
| **Microsoft** | Power BI Desktop Pl-300 |
| **Udacity** | Nanodegree Programs |
| **Bertelsmann** | Scholarship Sponsorship |
| **FWD Egypt** | Scholarship Sponsorship |
| **Kaggle** | Competition Platform |


---

*⭐ If you find this portfolio useful, please consider giving it a star!*
