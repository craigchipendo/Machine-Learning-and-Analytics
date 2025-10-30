# Airline Passenger Satisfaction Analysis - Jupyter Notebook

## Overview

This notebook analyzes **airline passenger satisfaction** using a large dataset of flight reviews, ratings, and various trip characteristics. The workflow demonstrates **data preprocessing, exploratory analysis, feature engineering, correlation analysis, and machine learning modeling** (including KNN, Decision Tree, Logistic Regression, SVM, Naive Bayes, ANN, and Random Forest) to predict whether a passenger is satisfied.

## Dataset

- **Input file:** Contains 129,880 records and 23 columns with fields such as `satisfaction`, `gender`, `customer type`, `age`, `type of travel`, `class`, service ratings (seat comfort, inflight wifi, check-in service...), delays, and more.
- **Target variable:** `satisfaction` (binary: satisfied/dissatisfied)

## Workflow

- **Data Cleaning:** Maps categorical variables to numeric codes, handles nulls, previews and summarizes features.
- **EDA & Visualization:**
  - Plots age distributions for Business, Economy, Eco Plus classes.
  - Shows satisfaction breakdown by demographic features and travel types.
  - Summarizes continuous and categorical features via descriptive stats.
  - Visualizes satisfaction composition across categories (gender, travel type, class, etc.).
- **Feature Engineering:**
  - Correlation matrix to rank feature importance.
  - Drops least-important columns based on correlation analysis.
  - Scales numerical features for improved model performance.
- **Modeling & Evaluation:**
  - Splits data into train/test sets.
  - Implements multiple classification models:
    - K-Nearest Neighbors (KNN)
    - Decision Tree
    - Random Forest
    - Logistic Regression
    - Support Vector Machine (SVM)
    - Gaussian Naive Bayes
    - Artificial Neural Network (ANN)
  - Evaluates each model using accuracy, precision, recall, F1-score, Cohen's kappa, AUC, sensitivity, specificity, and confusion matrix.
  - Compares model performance and highlights best predictors.
- **Feature Importance & Interpretation:** Identifies which service aspects (e.g., inflight entertainment, online booking, support, leg room, cleanliness) most strongly relate to satisfaction.

## Outputs

- Statistical and graphical insights into airline passenger satisfaction drivers.
- ML classification reports showing performance for predicting satisfaction.
- Ranked list of feature importances and suggestions for key improvement areas.

## Use Cases

This notebook helps:
- **Airline analysts and data scientists** quantify and improve passenger satisfaction.
- **Business intelligence teams** assess which service aspects most affect customer reviews.
- **Researchers and students** learn practical workflows for end-to-end classification modeling on real-world service data.

---


