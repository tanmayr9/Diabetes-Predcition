The Diabetes Prediction with AI project leverages a machine learning model to predict diabetes risk. Built with Streamlit, the app explains predictions using SHAP and permutation importance while showcasing model performance metrics. This model has not been reviewed by medical professionals; it is developed solely for experimental and testing purposes. The model was developed based on the ROC AUC metric, while efforts were made to improve the Recall metric when selecting the threshold, as this decision was made due to the medical context.

The dataset is sourced from the National Institute of Diabetes and Digestive and Kidney Diseases. It includes:

The dataset contains the following details:

General Overview
Number of rows: 768
Number of columns: 9
Column names and data types:
Pregnancies (int64): Number of times pregnant.
Glucose (int64): Plasma glucose concentration a 2 hours in an oral glucose tolerance test.
BloodPressure (int64): Diastolic blood pressure (mm Hg).
SkinThickness (int64): Triceps skin fold thickness (mm).
Insulin (int64): 2-Hour serum insulin (mu U/ml).
BMI (float64): Body mass index (weight in kg/(height in m)^2).
DiabetesPedigreeFunction (float64): Diabetes pedigree function.
Age (int64): Age (years).
Outcome (int64): Class variable (0 or 1).

About tarnsformers
1. FeatureEngineering
Transforms raw data into a format suitable for machine learning. This includes scaling, encoding, creating new features, or handling missing data.

2. WoEEncoding (Weight of Evidence Encoding)
Features must help to better explain the Outcome after WoE. The Weight of Evidence (WoE) for a category in a feature is calculated as:

Where:

P(Feature = X | Target = 1): Proportion of positive cases (Target = 1) for the category X.
P(Feature = X | Target = 0): Proportion of negative cases (Target = 0) for the category X.
Example:
If a feature X has the following counts:

For Target = 1 (Positive): N1
For Target = 0 (Negative): N0
3. ColumnSelector
Selects specific columns Pregnancies, Glucose, BMI, PregnancyRatio, RiskScore, InsulinEfficiency, Glucose_BMI, BMI_Age, Glucose_woe, RiskScore_woe after FeatureEngineering, it helps remove noice columns.

Features
Interactive Input: Enter health parameters (Pregnancies, Glucose, Insulin, BMI, Age).
Diabetes Prediction: Real-time risk prediction with probability.
SHAP Explanations: Visualize individual prediction explanations using:
Waterfall Plot
Force Plot
Permutation Importance: Analyze which features most influence the predictions.
Performance Metrics:
Accuracy
Precision
Recall
F1 Score
ROC AUC
Informational Section: Learn about diabetes risk factors in the "About" section.
