# Diabetes Prediction with AI


![app.gif](image/app.gif)


This project demonstrates a machine learning solution for predicting diabetes based on user-provided health data. The application uses **Streamlit** for an interactive web interface and advanced interpretability tools like SHAP and permutation importance to explain model predictions.

## Live Demo

Check out the live application: [Diabetes Prediction App](https://diabetes-prediction-uz.streamlit.app/)

---

## Table of Contents
1. [Overview](#overview)
2. [Dataset](#dataset)
3. [Features](#features)
4. [How It Works](#how-it-works)
5. [Project Structure](#project-structure)
6. [Explanation Methods](#explanation-methods)
7. [Model Performance](#model-performance)


---

## Overview

The **Diabetes Prediction with AI** project leverages a machine learning model to predict diabetes risk. Built with **Streamlit**, the app explains predictions using SHAP and permutation importance while showcasing model performance metrics. This model has not been reviewed by medical professionals; it is developed solely for experimental and testing purposes.
The model was developed based on the ROC AUC metric, while efforts were made to improve the Recall metric when selecting the threshold, as this decision was made due to the medical context.

### Why This Project?

Understanding diabetes risk through data-driven predictions can help identify potential cases early. This project also demonstrates:
- Practical application of machine learning.
- Model interpretability through SHAP and permutation importance.
- Real-world deployment of machine learning models.

---

## Dataset

The dataset is sourced from the **National Institute of Diabetes and Digestive and Kidney Diseases**. It includes:

The dataset contains the following details:

### General Overview
- **Number of rows:** 768
- **Number of columns:** 9
- **Column names and data types:**
  - `Pregnancies` (int64): Number of times pregnant.
  - `Glucose` (int64):  Plasma glucose concentration a 2 hours in an oral glucose tolerance test.
  - `BloodPressure` (int64): Diastolic blood pressure (mm Hg).
  - `SkinThickness` (int64): Triceps skin fold thickness (mm).
  - `Insulin` (int64): 2-Hour serum insulin (mu U/ml).
  - `BMI` (float64): Body mass index (weight in kg/(height in m)^2).
  - `DiabetesPedigreeFunction` (float64): Diabetes pedigree function.
  - `Age` (int64): Age (years).
  - `Outcome` (int64): Class variable (0 or 1).

### Sample Data (First 5 Rows)
| Pregnancies | Glucose | BloodPressure | SkinThickness | Insulin |  BMI  | DiabetesPedigreeFunction | Age | Outcome |
|-------------|---------|---------------|---------------|---------|-------|---------------------------|-----|---------|
| 6           | 148     | 72            | 35            | 0       | 33.6  | 0.627                     | 50  | 1       |
| 1           | 85      | 66            | 29            | 0       | 26.6  | 0.351                     | 31  | 0       |
| 8           | 183     | 64            | 0             | 0       | 23.3  | 0.672                     | 32  | 1       |
| 1           | 89      | 66            | 23            | 94      | 28.1  | 0.167                     | 21  | 0       |
| 0           | 137     | 40            | 35            | 168     | 43.1  | 2.288                     | 33  | 1       |

### Statistical Summary
- **Pregnancies:** Mean = 3.85, Max = 17
- **Glucose:** Mean = 120.89, Min = 0 (possible missing values)
- **BloodPressure:** Mean = 69.11, Min = 0 (possible missing values)
- **SkinThickness:** Mean = 20.54, Min = 0 (possible missing values)
- **Insulin:** Mean = 79.80, Min = 0 (possible missing values)
- **BMI:** Mean = 31.99, Min = 0 (possible missing values)
- **DiabetesPedigreeFunction:** Mean = 0.47, Max = 2.42
- **Age:** Mean = 33.24, Max = 81
- **Outcome:** Proportion of `1` (positive diabetes) = 34.9%


#### We use only `Pregnancies`, `Glucose`, `BMI`, `Insulin`, `Age` for prediction.
---

#### **2. WoEEncoding (Weight of Evidence Encoding)**
Features must help to better explain the `Outcome` after WoE.
The Weight of Evidence (WoE) for a category in a feature is calculated as:

Where:
- `P(Feature = X | Target = 1)`: Proportion of positive cases (`Target = 1`) for the category `X`.
- `P(Feature = X | Target = 0)`: Proportion of negative cases (`Target = 0`) for the category `X`.

##### Example:
If a feature `X` has the following counts:
- For `Target = 1` (Positive): `N1`
- For `Target = 0` (Negative): `N0`

#### **3. ColumnSelector**
Selects specific columns *Pregnancies*, *Glucose*, *BMI*, *PregnancyRatio*,
    *RiskScore*, *InsulinEfficiency*, *Glucose_BMI*, *BMI_Age*,
    *Glucose_woe*, *RiskScore_woe* after `FeatureEngineering`, it helps remove noice columns.

---
## Features

1. **Interactive Input**: Enter health parameters (Pregnancies, Glucose, Insulin, BMI, Age).
2. **Diabetes Prediction**: Real-time risk prediction with probability.
3. **SHAP Explanations**: Visualize individual prediction explanations using:
   - Waterfall Plot
   - Force Plot
4. **Permutation Importance**: Analyze which features most influence the predictions.
5. **Performance Metrics**:
   - Accuracy
   - Precision
   - Recall
   - F1 Score
   - ROC AUC
6. **Informational Section**: Learn about diabetes risk factors in the "About" section.

---

## How It Works

### Application Workflow
1. **User Input**:
   - Enter health data in the sidebar.
   - Features: Pregnancies, Glucose, Insulin, BMI, Age.
2. **Prediction**:
   - The trained model predicts diabetes risk and displays the result.
3. **Explanation**:
   - View SHAP plots (Waterfall and Force) for detailed feature contributions.
   - Explore permutation importance for global feature analysis.
4. **Model Performance**:
   - Metrics such as Accuracy, F1 Score, and ROC AUC are displayed.


# Project Structure
```
Diabetes-Prediction/
├── README.md                 # Project documentation
├── main.py                   # Entry point for the Streamlit app
├── loader.py                 # Data loading and preprocessing
├── training.py               # Script for training the model
├── requirements.txt          # Project dependencies
├── LICENSE                   # License file
├── datasets/
│   ├── diabetes.csv          # Dataset used for training and predictions
├── models/
│   ├── model.pkl             # Trained machine learning model
├── images/
│   ├── page_icon.jpeg        # Application page icon
├── data/
│   ├── config.py             # Configuration variables
│   ├── base.py               # Static HTML/CSS content
├── functions/
│   ├── model.py              # Custom model implementation
│   ├── function.py           # Utility functions
└── app/                      # Application logic and components
    ├── predict.py            # Prediction logic
    ├── explainer.py          # SHAP-based explanations
    ├── perm_importance.py    # Permutation importance analysis
    ├── performance.py        # Visualization of model performance metrics
    ├── input.py              # User input handling for predictions
    ├── about.py              # Informational section on diabetes
```


---

## Explanation Methods

1. **SHAP Waterfall Plot**:
   - Shows how each feature contributes positively or negatively to the prediction.
2. **SHAP Force Plot**:
   - Interactive visualization of feature contributions to individual predictions.
3. **Permutation Importance**:
   - Ranks features by their impact on the model's predictions.

---

## Model Performance

Performance metrics calculated:
- **Accuracy**: Percentage of correct predictions. (0.7857)
- **Precision**: Ratio of true positives to total positive predictions. (0.6296)
- **Recall**: Ratio of true positives to total actual positives. (0.9444)
- **F1 Score**: Harmonic mean of Precision and Recall. (0.7556)
- **ROC AUC**: Area under the ROC curve. (0.8367)

Metrics are displayed as donut charts in the application.


