# 💳 Credit Risk Modeling - Lauki Finance

A comprehensive machine learning project for predicting loan default risk using logistic regression with advanced feature engineering and hyperparameter optimization.

## 🌐 Live Demo

🚀 **Try the app here**: [Credit Risk Calculator](https://your-app-url.streamlit.app)


## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Model Performance](#model-performance)
- [Methodology](#methodology)
- [Technologies Used](#technologies-used)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)

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

## 📁 Project Structure
```
credit-risk-modeling/
│
├── data/
│   ├── customers.csv
│   ├── loans.csv
│   └── bureau_data.csv
│
├── artifacts/
│   └── model_data.joblib         # Saved model and preprocessing objects
│
├── notebooks/
│   └── analysis.ipynb             # Complete EDA and modeling notebook
│
├── app.py                         # Streamlit web application
├── prediction_helper.py           # Model prediction utilities
├── requirements.txt               # Python dependencies
└── README.md                      # Project documentation
```

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Steps

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/credit-risk-modeling.git
cd credit-risk-modeling
```

2. **Create a virtual environment** (recommended)
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

## 💻 Usage

### Running the Streamlit App
```bash
streamlit run app.py
```

The application will open in your default web browser at `http://localhost:8501`

### Using the Application

1. **Input customer information:**
   - Age, Income, Loan Amount
   - Loan Tenure, Average DPD
   - Delinquency Ratio, Credit Utilization
   - Number of Open Accounts
   - Residence Type, Loan Purpose, Loan Type

2. **Click "Calculate Risk"** to get:
   - Default probability percentage
   - Credit score (300-900)
   - Rating category

### Training the Model

To retrain the model with new data, run the Jupyter notebook:
```bash
jupyter notebook notebooks/analysis.ipynb
```

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

## 🔮 Future Enhancements

- [ ] Add model explainability using SHAP values
- [ ] Implement A/B testing framework
- [ ] Add model monitoring and drift detection
- [ ] Create REST API for production deployment
- [ ] Add batch prediction capability
- [ ] Implement ensemble models (stacking)
- [ ] Add more advanced features (time-series, behavioral)
- [ ] Create automated retraining pipeline

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👤 Author

**Your Name**
- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/yourprofile)

## 🙏 Acknowledgments

- Dataset provided by Lauki Finance
- Inspiration from industry best practices in credit risk modeling
- Open-source community for excellent libraries and tools

---

**Note**: This is a demonstration project. Always validate models thoroughly before using them in production environments.