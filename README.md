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
