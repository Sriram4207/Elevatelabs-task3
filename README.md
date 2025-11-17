# Elevatelabs-task3
Insurance Charges Prediction
This project explores a dataset of medical insurance personal costs to build and evaluate linear regression models for predicting individual medical charges.

Project Overview
The goal of this notebook is to demonstrate the process of loading a dataset, performing exploratory data analysis (EDA), and building both simple and multiple linear regression models to predict insurance charges. The analysis highlights the impact of various personal attributes on medical costs.

Dataset
The dataset used is the 'Medical Cost Personal Datasets' from [redacted link], which contains information about individuals including their age, sex, BMI, number of children, smoking status, region, and their medical charges.

Features:
age: Age of primary beneficiary
sex: Insurance contractor gender, female or male
bmi: Body mass index, providing an understanding of body, weights that are too high or too low relative to height, objective index of body weight (kg / m^2) using the ratio of height to weight, ideally 18.5 to 24.9
children: Number of children covered by health insurance / Number of dependents
smoker: Smoking status
region: The beneficiary's residential area in the US, northeast, southeast, southwest, northwest.
charges: Individual medical costs billed by health insurance
Analysis Steps
Data Loading & Preprocessing:

Loaded the insurance.csv dataset from a URL using pandas.
Handled missing values (though the provided dataset had none after the initial check).
Categorical features (sex, smoker, region) were preprocessed using One-Hot Encoding within a ColumnTransformer as part of a Pipeline for the multiple linear regression model.
Exploratory Data Analysis (EDA):

Displayed basic statistics (.head(), .describe(), .isnull().sum()).
Visualized distributions of numerical features using histograms.
Calculated and displayed skewness for numerical columns.
Generated a correlation heatmap to understand relationships between numerical features.
Simple Linear Regression:

A simple linear regression model was built using 'bmi' as the independent variable to predict 'charges'.
Evaluated the model using MAE, MSE, and R² Score.
Visualized the regression line against actual data points.
Multiple Linear Regression:

A more comprehensive model using 'age', 'bmi', 'children', 'sex', 'smoker', and 'region' as independent variables to predict 'charges'.
Utilized a Pipeline with ColumnTransformer for preprocessing and LinearRegression for modeling.
Evaluated the model performance on both training and test data using R² Score, MAE, and MSE.
Plotted residuals to check model assumptions.
Feature Importance:

Extracted and displayed the coefficients of the multiple linear regression model to understand the impact of each feature on the predicted charges.
Key Findings
Simple Linear Regression: The model using only 'bmi' to predict 'charges' showed a very low R² score of 0.0397, indicating that BMI alone explains less than 4% of the variance in medical charges. The MAE was high at 9784.65.

Multiple Linear Regression: By incorporating more features, the multiple linear regression model achieved a significantly higher R² score of 0.7836 on the test set. This means approximately 78.4% of the variance in medical charges can be explained by the combined set of features. The MAE drastically improved to 4181.19.

Feature Importance (Coefficients):

smoker_yes was by far the most significant predictor, with a coefficient of 23651.13. This implies that being a smoker leads to an average increase of over $23,000 in medical charges, holding other factors constant.
children, bmi, and age also showed positive correlations with charges, though their impact was much smaller compared to smoker_yes.
sex_male and the different region categories had comparatively minor (and mostly negative) effects on charges.
Conclusion: The multiple linear regression model is a substantially better predictor of insurance charges than the simple model, with smoking status being the most dominant factor influencing individual medical costs.

Technologies Used
Python 3
pandas
numpy
matplotlib
seaborn
scikit-learn
