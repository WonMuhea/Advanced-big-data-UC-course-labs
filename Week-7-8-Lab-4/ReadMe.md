### Purpose of the work
The goal of this lab is to analyze the Diabetes dataset using various regression models to:
- Predict disease progression based on physiological and medical features.
- Compare different linear and regularized regression techniques (Simple, Polynomial, Ridge, Lasso).
- Understand which features contribute most to model performance.
- Gain insights into model interpretability, and performace comparison

### Key Insights
- Multiple Linear Regression performed best overall with an R² of ~0.45, leveraging all features.
- Ridge Regression offered slightly reduced accuracy but better generalization and stability under multicollinearity.
- Lasso Regression identified key predictive features (bmi, s5, bp) by shrinking irrelevant coefficients to zero
- Simple and Polynomial BMI-only models underperformed, confirming that disease progression depends on multiple factors in addition to BMI.
- The target variable is slightly right-skewed. And transformations like log(target) can be considered for models that assume normality.
- The features are already standardized, making the dataset model-ready and compatible with regularization techniques.