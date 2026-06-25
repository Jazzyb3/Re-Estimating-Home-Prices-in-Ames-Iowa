# Re-Estimating Home Prices in Ames, Iowa

## Overview

This repository contains the code and analysis for predicting residential real estate prices in Ames, Iowa. The project applies advanced data preprocessing, feature engineering, and regularized machine learning techniques to a widely used real estate dataset. By leveraging Ridge, Lasso, and Elastic Net regression models within the R tidymodels pipeline, this project aims to improve price estimation accuracy while enhancing model interpretability and generalizability. This project was developed collaboratively by Jasmine Baldwin, Eric G. Bing, and Sickandar Akhthar.

## Dataset

The analysis utilizes a publicly available dataset consisting of 2,930 residential property sales in Ames, Iowa, occurring between 2002 and 2010. The dataset includes 81 distinct variables capturing a wide range of structural details (e.g., square footage, construction materials, age) and location attributes (e.g., proximity to roads, zoning classification).

## Project Goals

1. **Expand Feature Engineering:** Create new composite variables and interaction terms to better capture complex property characteristics based on hedonic pricing principles.

2. **Apply Regularization Techniques:** Develop and compare Ridge, Lasso, and Elastic Net regression models to identify the most accurate predictor.

3. **Optimize Model Selection:** Implement rigorous cross-validation techniques for hyperparameter tuning and model validation.

4. **Kaggle Evaluation:** Compare final model performance against previous benchmarks and submit results to the Kaggle leaderboard.

## Methodology

- **Data Preprocessing:** Handled missing data using k-nearest neighbors (KNN) imputation, identified and removed disruptive outliers using influence plots, and collapsed low-frequency categorical levels into an "other" category. Features with near-zero variance, such as the Utilities variable, were removed.

- **Handling Non-Linearity:** Addressed non-linear relationships by applying a natural cubic spline with five degrees of freedom to the LotFrontage variable, and stabilized variance in LotArea using a Box-Cox transformation.
  
- **Feature Engineering:** Engineered five new composite variables, including TotalArea, TotalFunctionalArea, TotalBathrooms, and AgeOfHouse. Additionally, 13 interaction terms were introduced to capture the interplay between structural and external factors, such as OverallQual × Neighborhood and LotArea × HouseSize.

- **Modeling & Validation:** Developed Ridge, Lasso, and Elastic Net regression models using the tidymodels framework. Hyperparameters (such as penalty lambda and mixture alpha) were optimized using grid search, and models were rigorously evaluated using 10-fold cross-validation with 5 repeats, stratified by the outcome variable, SalePrice.

## Results
The Elastic Net model provided the best predictive performance, successfully optimizing the balance between feature selection and coefficient shrinkage. The final Elastic Net predictions achieved a Kaggle score of 0.14110.

## Technologies Used

**Language:** R

**Key Packages:** `tidymodels`, `glmnet`, `dplyr`, `ggplot2`, `caret`, `mgcv`, `car`
