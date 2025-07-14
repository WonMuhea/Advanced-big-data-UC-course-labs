# Project Summary

## Overview
This project applied machine learning to two datasets: **UR3_CobotOps** (robot operational sensor data) and **AmesHousing** (real estate transaction data). The main goals were to explore predictive modeling through **regression**, **classification**, and **clustering**, and evaluate their effectiveness—particularly focusing on AmesHousing due to the temporal complexity of the UR3 data.

## Summary of Datasets
- **UR3_CobotOps**: Collected from collaborative robots with features like joint temperature, speed, and current. Suited for anomaly detection and predictive maintenance, but complex due to real-time dependencies and time-series structure.
- **AmesHousing**: Structured housing dataset with 80+ features capturing property attributes (area, quality, amenities) and sale prices. Ideal for regression and classification.

## Project Steps
1. **Data Preparation**: Extensive cleaning, imputation, transformation, and EDA for both datasets.
2. **Feature Engineering**: Generated meaningful composite features such as interaction terms, binary indicators, and age metrics.
3. **Modeling**:
   - **Regression**: Linear, multiple linear, and Ridge regression applied to predict house prices.
   - **Classification**: Decision Tree and K-Nearest Neighbors used to categorize houses into price tiers.
   - **Clustering**: K-Means and Hierarchical Clustering segmented homes based on quality indicators.
4. **Evaluation**: Used R², MSE, accuracy, and confusion matrices to assess performance.
5. **Ethical Considerations**: Addressed risks of bias, fairness, and model transparency.

## Major Findings
- **Regression**: Ridge regression achieved highest accuracy (R² ≈ 0.95) with best generalization.
- **Classification**: KNN slightly outperformed Decision Trees but both struggled with medium price category.
- **Clustering**: Both K-Means and Hierarchical Clustering aligned well, distinguishing premium vs. standard homes based on quality.
- **UR3_CobotOps**: Deferred modeling; EDA showed clear nonlinear and multimodal relationships, suggesting need for temporal models.

## Challenges Encountered

Several challenges were encountered during this research, particularly concerning data characteristics and model performance:

- The **UR3_CobotOps dataset** exhibited significant **multicollinearity** and a **time-series structure**, which required advanced modeling techniques (e.g., sequence modeling or temporal aggregation) not covered in this initial study.
- For the **AmesHousing dataset**, both **Decision Tree and KNN classifiers** struggled with accurately predicting the **"Medium_Price" category**.
- The **"Medium_Price" tier boundaries** appeared **less distinct**, with properties sharing traits from both lower and higher price classes, resulting in model confusion.
- These classification difficulties highlight the need for **refined segmentation**, possibly involving more granular price bins or advanced classification algorithms.
