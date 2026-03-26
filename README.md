# Credit Risk Modeling in R

## Key Results

- Non-linear models (decision tree, random forest) captured borrower risk structure more effectively than logistic regression, indicating the presence of interaction effects and threshold-based relationships in the feature space  
- Model performance remained stable between cross-validation and holdout evaluation, suggesting limited overfitting and consistent generalization within the dataset  
- Predictive signal was highly concentrated in a small subset of financial and repayment-related variables, rather than distributed across features  
- Evaluation metrics (ROC vs Precision-Recall) highlighted the importance of assessing performance beyond accuracy, particularly in an imbalanced classification setting  
- Strong model performance was partly driven by high-signal variables tied to repayment outcomes, highlighting potential data leakage if applied in a real-world underwriting setting  

---

## Approach

The objective was to classify loan outcomes using historical lending data and evaluate how different modeling approaches capture borrower risk. The dataset combined numeric and categorical financial variables along with operational fields that required removal before modeling.

Preprocessing involved dropping low-signal and non-generalizable columns, converting categorical variables to factors, and applying centering and scaling to numeric features. Consistency across training and validation splits was critical, particularly for factor levels and scaling parameters, to avoid instability in model behavior.

Three models were implemented: decision tree (CART), logistic regression, and random forest. Logistic regression provided a linear baseline but failed to capture interaction effects between borrower attributes. Decision trees modeled non-linear splits directly and produced interpretable decision rules. Random forest introduced additional flexibility through ensembling, but did not materially improve interpretability.

Model evaluation was structured using 4-fold cross-validation on the working dataset, with a separate holdout set reserved for final testing. Cross-validation alone would overstate performance stability; separating the holdout set provided a more reliable estimate of generalization.

---

## Insights & Limitations

Predictive performance was driven by a limited number of high-signal variables, particularly those related to repayment behavior and credit quality. Default risk was not evenly distributed across features, and model performance depended on isolating these concentrated signals.

Several high-importance variables were tied to post-origination repayment outcomes. These variables would not be available at the time of loan approval, introducing a clear data leakage risk in a production setting. Model performance in this project therefore reflects classification of historical outcomes rather than a deployable underwriting model.

The modeling approach applies uniform treatment across variables and thresholds, which simplifies the problem but does not fully capture the differing impact of individual financial features.

Model selection reflects a tradeoff between flexibility and interpretability. Non-linear models improved predictive performance, while the decision tree provided clearer structure for understanding how risk is separated into actionable rules.

---

## Outputs

**Decision Tree (CART Model)**  
![Decision Tree](outputs/tree_plot.png)

**ROC Curve**  
![ROC Curve](outputs/roc_curve.png)

**Precision-Recall Curve**  
![PR Curve](outputs/pr_curve.png)

## Notes

This project prioritizes interpretability and workflow design over model complexity, with an emphasis on understanding how different modeling choices affect both performance and insight.
