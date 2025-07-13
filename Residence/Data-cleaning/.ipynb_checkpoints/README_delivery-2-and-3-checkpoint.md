# 🏡 Ames Housing ML Project

## 📊 Dataset Summary

The **Ames Housing Dataset** contains detailed information on 2,930 house sales in Ames, Iowa. Features span:

- **Numerical Attributes** (e.g., Lot Area, Garage Area, Gr Liv Area)
- **Categorical/Ordinal Attributes** (e.g., Neighborhood, Exter Qual, Overall Qual)
- **Target Variables**:
  - For **regression**: `SalePrice` (continuous)
  - For **classification**: Categorized `SalePrice` into `Low`, `Mid`, `High`
  - For **clustering**: No labels; unsupervised grouping by physical/quality features

## 🔧 Modeling Process

### 1. Data Cleaning & Preprocessing
- Removed or imputed missing values (e.g., numeric columns with median, categorical with 'None')
- Converted ordinal variables into numerical ranks
- Scaled numeric variables and one-hot encoded categorical features
- Split data into **training/test** sets

### 2. Regression Modeling
- **Models Used**:
  - Linear Regression
  - Ridge and Lasso Regression (to address multicollinearity)
- **Evaluation**:
  - **R²** score, RMSE
  - Checked **VIF** (Variance Inflation Factor) to detect multicollinearity
- **Key Predictors**:
  - `Overall Qual`, `Gr Liv Area`, `Total Bsmt SF`, and `Garage Cars`

### 3. Classification Modeling
- **Objective**: Predict housing segment (Low, Mid, High)
- **Models Compared**:
  - **Decision Tree**: Accuracy ~75.7%, F1 ~75.8%
  - **k-Nearest Neighbors (k-NN)**: Accuracy ~81.4%, F1 ~81.3%
- **Evaluation**:
  - Confusion Matrix
  - ROC Curves (per class)
  - Accuracy and Macro-F1 Scores
- **Key Features**:
  - `Overall Qual`, `Gr Liv Area`, `Garage Cars`, `Total Bsmt SF`

### 4. Clustering
- **Goal**: Discover natural groupings of homes
- **Models Used**:
  - K-Means (k=3)
  - Hierarchical Clustering (Ward method, k=3)
- **Evaluation**:
  - Silhouette Scores:  
    - K-Means: 0.073  
    - Hierarchical: 0.060
- **Cluster Profiles**:
  - Cluster 0: Mid-size homes with average quality and price  
  - Cluster 1: Small homes, low price, minimal garage  
  - Cluster 2: Large, high-quality homes with high sale prices

## 💡 Key Insights & Observations

- **Classification**:
  - k-NN outperformed Decision Trees in both accuracy and class-wise ROC.
  - Models most easily distinguish `High` and `Low` price segments; `Mid` was harder to classify.
- **Regression**:
  - Ridge and Lasso slightly improved generalization over basic linear regression.
  - Regularization helped reduce overfitting due to highly correlated variables.
- **Clustering**:
  - Despite low silhouette scores, clusters aligned well with quality and size—enabling segmentation.
  - K-Means gave tighter and slightly more interpretable groupings than Hierarchical.

## ⚠️ Challenges & Mitigation

| Challenge | How It Was Addressed |
|----------|-----------------------|
| High multicollinearity in features | Applied **Ridge/Lasso** regression; checked **VIF** to diagnose |
| Many missing values | Used **interpolation** and **median imputation** based on variable type |
| Ordinal categorical data | Carefully mapped with **custom rankings** (e.g., Poor < Fair < Avg < Good < Ex) |
| k-NN classification errors with string labels | Applied **Label Encoding** to support distance metrics |
| Poor cluster separation | Performed **PCA** before clustering; experimented with **k** values to maximize silhouette score |