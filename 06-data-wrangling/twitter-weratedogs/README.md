# 🐦 WeRateDogs Twitter Data Wrangling

**Comprehensive Data Wrangling with Twitter API & Multi-Source Integration**

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-green)
![Twitter API](https://img.shields.io/badge/Twitter-API-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📋 Project Overview

| Aspect | Details |
|--------|---------|
| **Course** | Udacity Data Analysis Professional Nanodegree (FWD) |
| **Year** | 2020 |
| **Type** | Data Wrangling / API Integration / Data Quality |
| **Data Sources** | 3 (CSV, TSV, Twitter API) |
| **Issues Identified** | 30 (22 quality, 6 tidiness, 2 feature engineering) |
| **Research Questions** | 6 |

---

## 🎯 Objective

Gather data from multiple sources, assess data quality and tidiness issues, clean the data programmatically, and analyze the @WeRateDogs Twitter account to answer research questions about dog ratings, engagement patterns, and prediction accuracy.

---

## 📊 Data Sources

| Source | File | Method | Description |
|--------|------|--------|-------------|
| **Archive** | twitter_archive_enhanced.csv | Download | Tweet archive with dog ratings |
| **Images** | image_predictions.tsv | Programmatic Download | Neural network breed predictions |
| **API** | tweet_json.txt | Twitter API (tweepy) | Engagement metrics (retweets, favorites) |

---

## 🔍 Research Questions

| # | Question |
|---|----------|
| Q1 | What are the main devices/apps that WeRateDogs' users use? |
| Q2 | Is there a relationship between dog rates and retweet count? |
| Q3 | Is there a relationship between dog rates and favorite count? |
| Q4 | Is there a relationship between favorite count and retweet counts? |
| Q5 | What time are most tweets posted? |
| Q6 | Do high confidence predictions match reality more than low ones? |

---

## 📈 Data Quality Assessment

### Summary of Issues Found

| Category | Count | Examples |
|----------|-------|----------|
| **Quality Issues** | 22 | Invalid ratings, incorrect data types, missing values |
| **Tidiness Issues** | 6 | Multiple variables in columns, scattered observations |
| **Feature Engineering** | 2 | New columns needed for analysis |
| **Total** | **30** | |

### Tidiness Issues Identified

| # | Issue | Resolution |
|---|-------|------------|
| 1 | Timestamp contains date and time combined | Split into separate columns |
| 2 | Dog stage spread across 4 columns (doggo, floofer, pupper, puppo) | Melt into single column |
| 3 | Prediction results in 3 separate columns (p1, p2, p3) | Restructure with melt |
| 4 | Prediction confidence in 3 columns | Restructure with melt |
| 5 | Prediction validity in 3 columns | Restructure with melt |
| 6 | API data stored separately from archive | Merge into single table |

### Quality Issues Identified

| Type | Count | Examples |
|------|-------|----------|
| **Validity** | 4 | Non-descriptive column names, retweets included |
| **Accuracy** | 5 | Incorrect ratings from regex extraction, aggregated ratings |
| **Consistency** | 11 | Data type mismatches, inconsistent null representations |

---

## 🔧 Technical Approach

### Data Gathering

| Source | Method | Library |
|--------|--------|---------|
| CSV file | HTTP request | requests |
| TSV file | HTTP request | requests |
| Twitter API | OAuth authentication | tweepy |

### Data Cleaning Process

| Group | Issues Addressed | Approach |
|-------|------------------|----------|
| **Original Tweets Filter** | Remove retweets, replies, no-image tweets | Boolean filtering |
| **Dog Stage Cleanup** | Consolidate 4 columns into 1 | Concatenation, category conversion |
| **Rating Extraction** | Fix incorrect ratings from text | Regex extraction, manual correction |
| **Timestamp Processing** | Split datetime, convert types | pd.to_datetime, dt accessor |
| **Image Predictions** | Restructure prediction columns | pd.melt, pd.merge |
| **Table Consolidation** | Merge API data with archive | pd.merge on tweet_id |

### Key Cleaning Operations

| Operation | Code/Method |
|-----------|-------------|
| **Regex Rating Extraction** | Custom regex pattern for rating format |
| **Column Melting** | pd.melt() for prediction restructuring |
| **DateTime Conversion** | pd.to_datetime() with accessor methods |
| **Category Conversion** | .astype('category') for memory efficiency |
| **Table Merging** | pd.merge() on tweet_id |

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| README.md | This documentation file |
| wrangle_act.ipynb | Main Jupyter notebook with all code |
| wrangle_report.pdf | Documentation of wrangling efforts |
| act_report.pdf | Analysis insights and conclusions |
| requirements.txt | Python dependencies |

---

## 📤 Output Datasets

| Dataset | Description | Records |
|---------|-------------|---------|
| twitter_archive_master.csv | Cleaned and merged tweet data | Filtered original tweets |
| image_prediction.csv | Restructured prediction data | Melted prediction results |

---

## 🛠️ Tools & Libraries

| Category | Tools |
|----------|-------|
| **Language** | Python 3.x |
| **Data Processing** | Pandas, NumPy |
| **API Integration** | tweepy, requests |
| **Data Formats** | JSON, CSV, TSV |
| **Visualization** | Matplotlib, Seaborn |
| **Text Processing** | regex (re) |
| **DateTime** | datetime |
| **Environment** | Jupyter Notebook |

### Key Libraries Used

| Library | Purpose |
|---------|---------|
| pandas | Data manipulation, merging, melting |
| numpy | Numerical operations |
| tweepy | Twitter API authentication and queries |
| requests | HTTP file downloads |
| json | JSON parsing |
| re | Regular expression for text extraction |
| matplotlib | Data visualization |
| seaborn | Statistical visualization |
| datetime | DateTime operations |

---

## 🚀 How to Run

### Prerequisites

| Step | Command |
|------|---------|
| Install dependencies | `pip install -r requirements.txt` |

### Twitter API Setup (For Data Gathering)

| Credential | Description |
|------------|-------------|
| consumer_key | Twitter API consumer key |
| consumer_secret | Twitter API consumer secret |
| access_token | Twitter API access token |
| access_secret | Twitter API access secret |

> **Note:** Twitter API credentials required for full data gathering. API data file included for reproducibility.

### Run the Analysis

| Step | Command |
|------|---------|
| Open notebook | `jupyter notebook wrangle_act.ipynb` |
| Run all cells | Kernel → Restart & Run All |

---

## 💡 Key Findings

### Q1: Device/App Usage

| Finding | Details |
|---------|---------|
| Primary source | Twitter for iPhone dominates |

### Q2-Q4: Engagement Relationships

| Relationship | Correlation |
|--------------|-------------|
| Dog Rating vs Retweets | Analyzed in report |
| Dog Rating vs Favorites | Analyzed in report |
| Favorites vs Retweets | Strong positive correlation |

### Q5: Tweet Timing

| Finding | Details |
|---------|---------|
| Peak hours | Identified in analysis report |

### Q6: Prediction Confidence

| Finding | Details |
|---------|---------|
| High confidence predictions | Better match with reality |

---

## 📚 Skills Demonstrated

| Skill | Application |
|-------|-------------|
| ✅ API Integration | Twitter API with OAuth authentication |
| ✅ Multi-Source Data Gathering | CSV, TSV, JSON, API |
| ✅ Data Quality Assessment | Identified 30 issues across 3 datasets |
| ✅ Programmatic Cleaning | Automated cleaning with pandas |
| ✅ Regex Text Extraction | Extracted ratings from tweet text |
| ✅ Data Restructuring | Melting, merging, pivoting |
| ✅ DateTime Processing | Parsing, splitting, type conversion |
| ✅ Data Type Management | Category, datetime, string conversions |
| ✅ Documentation | Two formal reports (wrangling + analysis) |

---

## 📄 Reports Included

| Report | Description |
|--------|-------------|
| **wrangle_report.pdf** | Documents data gathering, assessment, and cleaning process |
| **act_report.pdf** | Presents analysis findings with visualizations |

---

## 🔗 Related Projects

| Project | Type | Link |
|---------|------|------|
| US Bikeshare Explorer | Data Wrangling | [Link](../us-bikeshare/) |
| Main Portfolio | All Projects | [Link](../../) |

---

## 📜 Acknowledgments

| Entity | Contribution |
|--------|--------------|
| **Udacity** | Data Analysis Professional Nanodegree |
| **WeRateDogs** | Twitter data source |
| **FWD (Egypt)** | Scholarship sponsorship |

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
