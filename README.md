# predicting-road-accident-risk-kaggle

![Road Safety Banner](https://raw.githubusercontent.com/ABUALHUSSEIN/predicting-road-accident-risk-kaggle/refs/heads/main/road.png)

This repository contains my complete solution for the **"Predicting Road Accident Risk"** Kaggle competition. The project features a deep exploratory data analysis (EDA) and the development of a high-performance predictive model using LightGBM.

---

## 1. Project Overview

The goal of this competition is to predict a continuous `accident_risk` score for road segments based on a rich dataset of road, environmental, and temporal features. This is a classic regression problem with real-world implications for improving road safety.

This project is structured into two main parts, documented in separate Kaggle notebooks:
1.  **Exploratory Data Analysis (EDA):** A comprehensive investigation of the dataset to uncover patterns, validate data quality, and identify key predictive features. My EDA notebook for this project was awarded a **Bronze Medal** on Kaggle.
    *   **[View the Award-Winning EDA Notebook on Kaggle](https://www.kaggle.com/code/anwarabualhussien/full-eda-understanding-the-data)**
2.  **Predictive Modeling:** The implementation of a robust machine learning pipeline to preprocess the data and train a final, optimized LightGBM model for submission.
    *   **[View the Modeling Notebook on Kaggle](https://www.kaggle.com/code/anwarabualhussien/lightgb-rmse-0-05626-road-risk-prediction)**

---

## 2. Dataset

*   **Source:** [https://www.kaggle.com/competitions/playground-series-s5e10]
*   **Size:** The dataset contains over 500,000 entries.
*   **Features:** A mix of numerical, categorical, and boolean features including `road_type`, `num_lanes`, `curvature`, `speed_limit`, `lighting`, `weather`, and `time_of_day`.
*   **Target:** `accident_risk` (a continuous float value).
*   **Key Characteristic:** The dataset is complete, with no missing values, which streamlined the preprocessing stage.

---

## 3. Methodology & Workflow

The solution follows a structured, data-driven approach.

### a) Exploratory Data Analysis (EDA)
The findings from the EDA were crucial in guiding the modeling strategy:
*   **Target Variable Analysis:** The `accident_risk` distribution was found to be slightly right-skewed but suitable for modeling without transformation.
### b) Data Preprocessing
*   **Categorical Encoding:** `OneHotEncoder` was used to convert categorical features into a numerical format that the model can understand.
*   **Numerical Scaling:** `StandardScaler` was applied to numerical features to normalize their scale.

### c) Modeling
*   **Model Selection:** I experimented with two state-of-the-art gradient boosting frameworks: **LightGBM** and **XGBoost**. After evaluating both using a rigorous cross-validation process, **LightGBM was selected as the final model** due to its superior performance on this specific dataset.
*   **Validation Strategy:** A **5-Fold Cross-Validation** strategy was implemented. This provides a stable and reliable estimate of the model's performance by training 5 separate models on different subsets of the data.
*   **Performance Optimization:** The models were trained using a **GPU accelerator**, which dramatically reduced training time.

---

## 4. Results

The model's performance was evaluated using the **Root Mean Squared Error (RMSE)** metric. The final submission was generated using the LightGBM model, which achieved the best score.

### Model Performance Comparison

| Model | Overall CV RMSE |
| :--- | :---: |
| **LightGBM (Final Model)** | **[0.05626]** |
| XGBoost | [0.056356] |

The feature importance plot from the winning LightGBM model confirms the insights from our EDA, highlighting the most influential factors in predicting accident risk:
*   **Top Predictors:** `curvature`, `speed_limit`, and `lighting` conditions were consistently ranked as the most important features.

---

