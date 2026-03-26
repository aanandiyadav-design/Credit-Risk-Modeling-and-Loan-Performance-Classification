# Credit Risk Modeling in R

## Key Results

- Decision trees outperformed logistic regression in capturing non-linear risk patterns  
- Model performance was stable across cross-validation and holdout evaluation  
- Risk signals were concentrated in a small number of financial and repayment-related features  
- Simple additive engagement-style metrics were insufficient for explaining default behavior without feature-level context  

---

## Overview

This project builds a credit risk classification workflow in R to distinguish between higher-risk and lower-risk loans using historical lending data. The focus was on model performance, understanding how different modeling approaches capture borrower risk and how evaluation choices impact reliability.

---

## Data Preprocessing

The dataset contained a mix of numeric and categorical financial variables, along with several low-signal and redundant fields.

- Removed non-informative and operational columns (IDs, URLs, policy flags)  
- Dropped variables with low variance or limited interpretability  
- Converted categorical variables to factors with consistent levels across splits  
- Applied centering and scaling to numeric features to stabilize model behavior  
- Removed missing values to ensure consistent training and evaluation  

One key challenge was ensuring that preprocessing steps were applied consistently across training and validation splits, particularly for factor levels and scaling parameters.

---

## Modeling Approach

Three models were implemented and compared:

- **Decision Tree (CART)**  
  - Controlled depth to avoid overfitting  
  - Provided interpretable splits and feature importance  

- **Logistic Regression**  
  - Served as a linear baseline  
  - Limited in capturing non-linear interactions between borrower attributes  

- **Random Forest**  
  - Introduced non-linearity and ensemble averaging  
  - Used to compare performance against simpler interpretable models  

A 4-fold cross-validation framework was used on the working dataset, with a separate holdout set reserved for final evaluation.

---

## Evaluation

Model performance was evaluated using:

- Accuracy  
- Confusion matrix metrics  
- Cross-validation consistency  
- Holdout set performance  

Separating cross-validation from holdout evaluation was important to avoid optimistic performance estimates and to assess generalization more reliably.

---

## Key Insights

- **Model choice matters:**  
  Decision trees captured non-linear interactions in borrower risk that logistic regression failed to represent effectively  

- **Activity vs risk signal:**  
  Features tied to repayment behavior and financial status were significantly more predictive than simple activity-based metrics  

- **Interpretability vs performance:**  
  While random forest improved flexibility, the decision tree provided clearer insight into how risk decisions are made  

- **Evaluation design matters:**  
  Without a proper holdout set, cross-validation alone would overstate performance stability  

---

## Limitations

- Several high-importance features are related to repayment outcomes, which may not be available at loan origination (potential data leakage if used in production settings)  
- Additive modeling assumptions (e.g., equal weighting of engagement-style metrics) oversimplify how different variables contribute to risk  
- Class imbalance and threshold selection were not explicitly optimized

---

## Notes

This project prioritizes interpretability and workflow design over model complexity, with an emphasis on understanding how different modeling choices affect both performance and insight.
