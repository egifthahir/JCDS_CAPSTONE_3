# README

## California House Pricing Regression Prediction Model

### Author:
Muhammad Abizar Algiffary Thahir (JCDS 2504-002)

---

## Table of Contents:
1. [Introduction](#introduction)
2. [Understanding the Data](#understanding-the-data)
3. [Data Preprocessing](#data-preprocessing)
4. [Model Building](#model-building)
5. [Model Evaluation](#model-evaluation)
6. [Feature Importance](#feature-importance)
7. [Model Comparison](#model-comparison)
8. [Limitations](#limitations)
9. [Conclusion](#conclusion)
10. [Business Recommendations](#business-recommendations)

---

## 1. Introduction

### 1.1 Background
The California real estate market is dynamic and plays a significant role in the state economy. Predicting property prices based on historical data and key features like location, proximity to the coast, population density, and median income can provide critical insights for stakeholders such as property investors, developers, and regulators.

### 1.2 Problem Statement
The goal is to predict California's median house prices using various features, including geographic location, age of the property, number of rooms, population, and distance to the coastline. A reliable machine learning model is required to forecast these prices and assist decision-making, as current manual calculations are insufficient.

### 1.3 Objectives
- Understand the relationship between house prices and key factors such as proximity to the ocean, income levels, and property age.
- Build a predictive model to estimate house prices based on historical data.
- Identify the most critical factors in determining house prices.

### 1.4 Approach
The approach includes data preprocessing, feature selection, model selection, hyperparameter tuning, and model evaluation using key metrics like RMSE, MAE, MAPE, and R².

---

## 2. Understanding the Data

### 2.1 Data Description
The dataset contains California housing data from 1990, including geographical features (latitude and longitude), property characteristics, and census data. Features include:
- `longitude` and `latitude`
- `housing_median_age`
- `total_rooms`, `total_bedrooms`
- `population`, `households`
- `median_income`
- `ocean_proximity` (categorical)
- `median_house_value` (target variable)

### 2.2 Data Distribution
- A high concentration of properties is located near the coastline.
- Significant variations in population density, number of rooms, and income levels across the state.

---

## 3. Data Preprocessing

### 3.1 Handling Missing Data
- Missing values in `total_bedrooms` were handled using KNNImputer to estimate missing data based on nearby data points.

### 3.2 Outlier Detection
- Outliers were detected using box plots, and data points outside a calculated IQR range were removed to reduce their influence on the model.

### 3.3 Feature Correlation
- High correlations between features like `total_rooms` and `households` were identified, which can lead to multicollinearity in regression models.
- Features like `total_bedrooms` and `households` were excluded due to high correlation.

---

## 4. Model Building

### 4.1 Feature Selection
After feature selection, the key features included `longitude`, `latitude`, `housing_median_age`, `total_rooms`, `population`, and `median_income`.

### 4.2 Model Selection
- Several regression models were tested: **Ridge**, **Lasso**, **Linear Regression**, **KNN**, **Decision Tree**, **SVM**, **Random Forest**, **XGBoost**, **LightGBM**, and **CatBoost**.
- CatBoost Regressor performed the best in initial benchmarks based on RMSE and R².

### 4.3 Hyperparameter Tuning
- Hyperparameter tuning was done using **RandomSearchCV** for CatBoost, LightGBM, and XGBoost to optimize model performance.

---

## 5. Model Evaluation

### 5.1 Metrics
The models were evaluated using the following metrics:
- **RMSE (Root Mean Squared Error)**: Evaluates the standard deviation of the prediction errors.
- **MAE (Mean Absolute Error)**: Measures the average error between predicted and actual values.
- **MAPE (Mean Absolute Percentage Error)**: Shows the error as a percentage.
- **R²**: Indicates how much variance in the target variable is explained by the model.

### 5.2 Performance Comparison
After tuning, the final **CatBoost** model achieved the following metrics:
- **RMSE**: 47,053 USD
- **MAE**: 31,448 USD
- **MAPE**: 17.82%
- **R²**: 0.831

---

## 6. Feature Importance

### 6.1 Key Features
- **Median Income**: Highest impact on house prices.
- **Longitude and Latitude**: Significant geographical influence.
- **Population and Total Rooms**: Moderate impact on prices.

---

## 7. Model Comparison

### 7.1 Comparison with Simple Estimation
The machine learning model was compared to a simple rule-based calculation using median values from nearby houses. The CatBoost model significantly outperformed the rule-based method:

---

## 8. Limitations

- The model is trained on a 1990 dataset and is applicable only to California properties from that time.
- The model's predictions are limited to properties with similar characteristics as the dataset (e.g., room count, property age).
- Model performance is constrained to the features available in the dataset.

---

## 9. Conclusion

- The final CatBoost model performed well, with an R² of 0.831, indicating it can explain 83% of the variance in house prices.
- Median income and location (longitude, latitude) are the most critical factors in determining house prices.
- The machine learning approach provides a more accurate and flexible solution than traditional rule-based estimates.

---

## 10. Business Recommendations

- **Target Coastal Cities**: Focus on developing properties in major coastal cities where property values are high, such as San Francisco, Los Angeles, and San Diego.
- **Develop Smaller Properties**: Given high property prices, smaller units like apartments may cater to a larger market.
- **Monitor Key Features**: Pay attention to median income, population density, and property age when investing.
- **Leverage Predictive Models**: Use advanced machine learning models for more accurate property valuations in a competitive market.

--- 

## How to Use

1. **Data Preprocessing**: Follow the data preprocessing steps (missing value imputation, outlier detection, etc.) before model training.
2. **Model Training**: Use CatBoost Regressor with tuned hyperparameters for the best performance.
3. **Evaluation**: Use RMSE, MAE, MAPE, and R² to evaluate the model's accuracy.
4. **Model Saving**: Save the final model using the provided pipeline and pickle for future use.

