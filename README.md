# Price Explains the Wine: An Analysis of Subjective Ratings  
**EDA, Modeling, and Explainability**

This project explores a dataset of Portuguese wines rated by expert judges.  
The target variable is a **subjective rating**, rather than an objective measure of wine quality.

The analysis combines exploratory data analysis, clustering, predictive modeling, and explainability to understand which features actually drive model behavior — and where the limits of the data lie.


The notebook can be found here: 
https://github.com/m-zhokhova/subjective-wine-ratings-analysis/blob/main/notebooks/portuguese-wines-eda-blog-os-vinhos.ipynb
---

## Dataset

The dataset contains the following information:
- Alcohol percentage  
- Year of production  
- Minimum and maximum price  
- Grape varieties, region, and producer  

No chemical composition or laboratory measurements are available.

---

## Objectives

The goal of this project is **not** to build a high-accuracy wine rating predictor.  
Instead, it aims to:

- Compare the usefulness of numerical and categorical features  
- Examine whether adding more features improves clustering and prediction  
- Use explainable AI techniques to understand model behavior  
- Illustrate how subjective targets affect modeling outcomes  

---

## Methodology

The analysis is structured as follows:

1. **Exploratory Data Analysis**
   - Data cleaning and preprocessing  
   - Distribution analysis and correlations  

2. **Clustering**
   - Numerical features vs. grape-based features  
   - PCA and KMeans clustering  
   - Comparison of cluster structure and overlap  

3. **Predictive Modeling**
   - Linear Regression, Random Forest, Gradient Boosting  
   - Numerical-only, categorical-only, and combined feature sets  
   - Performance comparison across setups  

4. **Explainability**
   - SHAP-based global and local explanations  
   - Comparison of linear and non-linear models  
   - Interpretation of dominant features  

---

## Key Findings

- Numerical features outperform categorical descriptors in both clustering and prediction  
- Price dominates model behavior, with age and alcohol playing secondary roles  
- Adding grape, region, and producer information does not improve performance  
- More complex models do not recover additional signal  
- Explainability confirms that the data, not the model, is the limiting factor  


