🏆 Kaggle 30 Days of ML: Insurance Claims Prediction
Top 30% Ranking | Regression with LightGBM

Kaggle
Python
LightGBM
Status
Ranking

📋 Project Overview
Aspect	Details
Competition	Kaggle 30 Days of ML
Year	2021
Type	Supervised Learning (Regression)
Objective	Predict continuous insurance claim amounts
Ranking	Top 30% (outperforming ~70% of participants)
🎯 Problem Statement
Predict a continuous target variable (insurance claim amount) based on a mix of categorical and numerical features using a synthetic dataset created with CTGAN (based on real data).

📊 Dataset
Metric	Value
Training Records	300,000
Test Records	200,000
Total Records	500,000
Categorical Features	10 (cat0 - cat9)
Numerical Features	14 (cont0 - cont13)
Target Variable	Continuous (claim amount)
Missing Values	None
🔧 Technical Approach
1. Exploratory Data Analysis
Analyzed feature distributions and correlations
Identified low-correlation features for removal
Examined categorical variable cardinality
2. Feature Engineering
Dropped low-correlation columns: cont1, cont8, cat0, cat1, cat2, cat9
Final features used: 19 (7 categorical + 12 numerical)
3. Categorical Encoding
Label Encoding for all categorical variables
Cardinality analysis (all ≤ 16 unique values)
4. Model Selection & Training
Model	Description
LGBMRegressor	Final model (LightGBM gradient boosting)
K-Fold CV	2-fold cross-validation
Early Stopping	50 rounds
5. Hyperparameter Configuration
Python

lgbm_parameters = {
    'max_depth': 43,
    'subsample': 0.52,
    'colsample_bytree': 0.20,
    'learning_rate': 0.0095,
    'reg_lambda': 21.86,
    'reg_alpha': 15.43,
    'min_child_samples': 24,
    'num_leaves': 10,
    'max_bin': 839,
    'cat_smooth': 86,
    'n_estimators': 2000,
    'metric': 'rmse'
}
📈 Results
Metric	Value
Best RMSE	0.7249
Max RMSE	0.7261
Average RMSE (CV)	0.7255
Competition Ranking	Top 30%
Cross-Validation Performance
text

Fold 1 RMSE: 0.7249
Fold 2 RMSE: 0.7261
Average RMSE: 0.7255
🛠️ Tools & Libraries
Category	Tools
Language	Python 3.x
Data Processing	Pandas, NumPy
Visualization	Matplotlib, Seaborn
ML Framework	scikit-learn, LightGBM, XGBoost
Validation	K-Fold Cross-Validation
Environment	Kaggle Notebooks
Key Libraries Used
Python

# Core
import pandas as pd
import numpy as np

# Visualization
import matplotlib.pyplot as plt
import seaborn as sns

# Preprocessing
from sklearn.model_selection import train_test_split, KFold
from sklearn.preprocessing import LabelEncoder

# Model
from lightgbm import LGBMRegressor

# Evaluation
from sklearn.metrics import mean_squared_error
📁 Project Structure
text

kaggle-insurance-prediction/
├── README.md                           # This file
├── 30-days-of-ml-competition.ipynb     # Main notebook
└── requirements.txt                    # Dependencies
🚀 How to Run
Option 1: Kaggle (Recommended)
Visit the competition page
Fork this notebook
Run all cells
Option 2: Local
text

pip install -r requirements.txt
jupyter notebook 30-days-of-ml-competition.ipynb
Note: Dataset is available only through Kaggle competition.

💡 Key Learnings
Feature Selection Matters: Removing low-correlation features improved model performance
LightGBM Efficiency: Faster training than XGBoost with comparable results
Regularization: High reg_lambda and reg_alpha helped prevent overfitting
Cross-Validation: K-Fold CV provided stable performance estimates
📊 Feature Importance (Top Features)
Based on analysis, the most impactful features were:

Numerical continuous features (cont0, cont2-cont7, cont9-cont13)
Categorical features with moderate cardinality (cat3-cat8)
🔗 Related Projects
Diamond Pricing – Linear regression approach
Catalog Demand – Profit estimation model
Credit Default Risk – Classification comparison
📜 Competition Details
Host: Kaggle
Duration: 30 days
Participants: 7,000+
Evaluation: RMSE (Root Mean Squared Error)
Dataset: Synthetic (CTGAN-generated from real data)
👤 Author
Maged Baheig

LinkedIn: https://www.linkedin.com/in/magedbaheig
GitHub: https://github.com/Maged-Baheig
Kaggle: https://www.kaggle.com/magedbaheig
Email: magedbaheig@gmail.com
Location: Cairo, Egypt

Part of the Data Science Portfolio

