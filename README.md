# Price Explains the Wine: An Analysis of Subjective Ratings  
**EDA, Modeling, and Explainability**

This project explores a dataset of Portuguese wines rated by expert judges.  
The target variable is a **subjective rating**, rather than an objective measure of wine quality.

The analysis combines exploratory data analysis, clustering, predictive modeling, and explainability to understand which features actually drive model behavior — and where the limits of the data lie.

The notebook can be found here: https://github.com/m-zhokhova/subjective-wine-ratings-analysis/blob/main/notebooks/portuguese-wines-eda-blog-os-vinhos.ipynb

---

## Dataset

- **Number of wines:** 2,993  
- **Target:** `JudgeRating` (0–20 scale)  
- **Mean rating:** 15.64  
- **Standard deviation:** 1.13  
- **Max observed rating:** 19  

**Feature groups:**

**Numerical**
- year  
- alcohol percentage  
- minimum price  
- maximum price  

**Composition (categorical)**
- grape variety  
- region  
- producer  
- wine color  

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
---

## Modeling Results

### Performance Summary (Real Results)

| Features     | Model              | MAE     | R²       |
|--------------|--------------------|---------|----------|
| Numerical    | Linear Regression  | 0.4473  | 0.6055   |
| Numerical    | Gradient Boosting  | 0.4516  | 0.5758   |
| Numerical    | Random Forest      | 0.5049  | 0.3205   |
| All          | Gradient Boosting  | 0.4535  | 0.3528   |
| All          | Random Forest      | 0.4737  | 0.3085   |
| All          | Linear Regression  | 0.5409  | 0.3028   |
| Composition  | Gradient Boosting  | 0.7031  | 0.0426   |
| Composition  | Random Forest      | 0.6804  | 0.0154   |
| Composition  | Linear Regression  | 0.7277  | -0.1090  |

---

## Results — Interpretation

**1) Numerical features dominate**

- The best model is **Linear Regression (Numerical only)** with  
  **R² = 0.605** and **MAE = 0.447**.
- Adding categorical composition features **reduces performance** in all models.
- This means that:
  - price  
  - alcohol  
  - year  
  explain far more variance than grapes, region, or producer.

---

**2) Categorical features are almost useless alone**

- Composition-only models all have **near-zero or negative R²**.
- This means grape variety, region, and producer:
  - add weak signal  
  - introduce noise  
  - hurt generalization when combined with numeric features.

---

**3) Linear regression beats tree models**

- Linear regression outperforms both random forest and gradient boosting.
- This implies:
  - the signal is mostly linear  
  - the dataset is low-noise for numeric predictors  
  - non-linear models mostly overfit.

---

**4) Error scale is actually reasonable**

- Typical MAE ≈ **0.45–0.50** points.
- On a **0–20 scale**, that’s ~**2–3% absolute error**.
- Given that ratings are subjective, this is a **realistic ceiling**.

---

## Explainability

### Global Explainability (SHAP)

SHAP analysis shows consistent global drivers:

- price (strongest predictor)  
- alcohol percentage  
- year  
- region  
- grape variety  

However:

- price alone does not guarantee high ratings  
- many expensive wines receive only average scores  
- feature contributions are diffuse rather than dominant.

---

### Local Explainability (Per-Wine)

For individual wines:

- predictions are driven by small contributions from multiple features  
- no single variable dominates most predictions  
- categorical features often push predictions in inconsistent directions  

This reinforces that:

> wine ratings are not determined by a single strong factor  
> and are weakly predictable even with market and composition metadata.

---

## Key Findings

- Wine ratings on a 0–20 scale are **moderately predictable** using numeric metadata.  
- Best achievable R² ≈ **0.60** with simple linear regression.  
- Categorical composition features **hurt** rather than help.  
- Price explains only part of the variance.  
- Tree-based models do not outperform linear baselines.  
- Interpretability reveals diffuse, low-signal feature effects.

---

## Limitations

- No chemical composition data.  
- No sensory or tasting notes.  
- No reviewer identity or calibration.  
- Single-country focus (Portugal).  
- Ratings are subjective by nature.

---

## Ethical & Analytical Notes

- Ratings should not be treated as objective quality measures.  
- Price–rating relationships reflect market and reputation effects.  
- Models encode cultural and regional biases.  
- Predictions are intended for analysis, not consumer guidance.

---

## Future Work

- Add chemical composition features.  
- Model reviewer-specific bias.  
- Use ordinal regression instead of standard regression.  
- Predict rating ranges instead of point values.  
- Add uncertainty estimation.  
- Compare against blind-tasting datasets.

---
