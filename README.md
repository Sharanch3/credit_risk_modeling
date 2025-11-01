# 💳 Credit Risk Modeling - Lauki Finance

A comprehensive machine learning project for predicting loan default risk using logistic regression with advanced feature engineering and hyperparameter optimization.

## 🌐 Live Demo

**Try the app here**: [Credit Risk Calculator](https://credit-risk-modeling-classification.streamlit.app/)


## 🎯 Overview

This project builds a credit risk assessment model that predicts the probability of loan default. The model is deployed as an interactive Streamlit web application where users can input customer information and receive:
- Default probability
- Credit score (300-900 range)
- Credit rating (Poor/Average/Good/Excellent)

The model achieves **98% AUC** and **96% Gini coefficient**, demonstrating excellent discriminatory power.

## ✨ Features

### Machine Learning Pipeline
- **Feature Engineering**: Created domain-specific features like Loan-to-Income ratio, Delinquency ratio, and Average DPD per delinquency
- **Feature Selection**: Used Information Value (IV) and Variance Inflation Factor (VIF) for optimal feature selection
- **Class Imbalance Handling**: Implemented SMOTE-Tomek technique to handle imbalanced data (~8% default rate)
- **Hyperparameter Optimization**: Used Optuna for advanced parameter tuning
- **Model Evaluation**: Comprehensive evaluation using ROC-AUC, KS statistic, Gini coefficient, and rank ordering

### Web Application
- Interactive Streamlit interface
- Real-time credit risk prediction
- User-friendly input forms for customer data
- Instant credit score calculation and rating

## 📊 Dataset

The project uses three datasets:
- **Customers**: Demographics and personal information
- **Loans**: Loan details and disbursement information
- **Bureau Data**: Credit bureau information (accounts, delinquencies, credit utilization)

**Key Statistics:**
- Training samples: ~75% of data
- Test samples: ~25% of data
- Target variable: Default (0 = No, 1 = Yes)
- Class distribution: ~92% non-default, ~8% default



## 📈 Model Performance

| Metric | Value |
|--------|-------|
| **AUC-ROC** | 0.98 |
| **Gini Coefficient** | 0.96 |
| **KS Statistic** | 85.7% |
| **F1 Score (Class 1)** | 0.95 |
| **Precision (Class 1)** | 0.93 |
| **Recall (Class 1)** | 0.97 |

### Model Insights
- **Top 2 deciles capture 98% of all default events**
- **Strong rank ordering** with clear separation between risk segments
- **High discriminatory power** suitable for production deployment

## 🔬 Methodology

### 1. Data Preprocessing
- Handled missing values using mode imputation
- Removed business rule violations (processing fee > 3% of loan amount)
- Fixed data inconsistencies
- Train-test split (75-25) to prevent data leakage

### 2. Feature Engineering
Created three powerful derived features:
- **Loan-to-Income Ratio**: `loan_amount / income`
- **Delinquency Ratio**: `(delinquent_months / total_loan_months) × 100`
- **Avg DPD per Delinquency**: `total_dpd / delinquent_months`

### 3. Feature Selection
- **Numeric features**: Removed multicollinear features using VIF
- **Categorical features**: Selected features with IV > 0.02
- Final feature set: 13 features

### 4. Model Training
- **Algorithm**: Logistic Regression
- **Sampling**: SMOTE-Tomek for class balance
- **Optimization**: Optuna with 50 trials
- **Best Parameters**: `C=0.09`, `solver='saga'`, `class_weight='balanced'`

### 5. Evaluation
- ROC-AUC curve analysis
- KS statistic calculation
- Decile analysis for rank ordering
- Feature importance visualization

## 🛠️ Technologies Used

- **Python 3.8+**
- **Data Analysis**: pandas, numpy
- **Visualization**: matplotlib, seaborn
- **Machine Learning**: scikit-learn, XGBoost
- **Class Imbalance**: imbalanced-learn (SMOTE-Tomek)
- **Hyperparameter Tuning**: Optuna
- **Model Persistence**: joblib
- **Web Framework**: Streamlit
- **Statistical Analysis**: statsmodels



## 📄 License

This project is licensed under the MIT License.


