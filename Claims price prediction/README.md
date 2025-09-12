# Insurance Claim Price Prediction
## Project Description
A comprehensive analysis and predictive modeling project that uses machine learning to estimate insurance claim costs based on policyholder demographics, health metrics, and coverage details.

## Dataset
insurance_dataset.csv (1M records, 12 features)

## Key Features:

Demographics: age, gender, region

Health indicators: bmi, smoker status, medical history, exercise frequency

Policy details: children/dependents, occupation, coverage_level

Target: charges (insurance claim costs)

## Project Workflow
### Exploratory Data Analysis

Statistical analysis of numerical and categorical features

Visualization of distributions and relationships

Correlation analysis between features and target

### Feature Engineering

Encoding of categorical variables

Creation of new features (age groups, BMI categories)

Handling outliers and feature scaling

### Model Development

Implemented and compared multiple regression models:

Linear Regression

Random Forest Regressor

Gradient Boosting Regressor

XGBoost Regressor

Support Vector Regressor

### Model Evaluation & Optimization

Performance metrics: MAE, MSE, RMSE, R²

Hyperparameter tuning with Grid Search

Feature importance analysis

## Key Findings
Smoking status is the strongest predictor of claim costs

Age and BMI show significant positive correlation with charges

Dataset is well-balanced with no missing values

Tree-based models (especially XGBoost) delivered best performance

## Technical Stack
Python, Jupyter Notebook

Libraries: pandas, numpy, matplotlib, seaborn, scikit-learn, XGBoost

Modeling: Multiple regression algorithms with hyperparameter optimization
