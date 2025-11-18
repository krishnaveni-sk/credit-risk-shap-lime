Interpretable Machine Learning – Credit Default Prediction (SHAP + LIME)
1. Project Overview

Dataset: UCI Default of Credit Card Clients

Goal: Predict credit default

Model used: Gradient Boosting (XGBoost)

Performance achieved: AUC ≈ 0.80+

2. Preprocessing & Feature Engineering

Removed ID

Cleaned column names

Added domain features:

TOTAL_BILL

TOTAL_PAY

PAYMENT_RATIO

AVG_BILL

TOTAL_PAY_DELAY

SMOTE applied on training set

StandardScaler + OneHotEncoder via ColumnTransformer

3. Model Training & Hyperparameter Tuning

Used RandomizedSearchCV

Best parameters stored

Final metrics:

AUC: 0.8+

Precision, Recall, Accuracy (insert values)

4. Global Interpretability (Task 2)

Top 10 features from SHAP summary plot:
(Insert your top 10 list)

Interpretation of top drivers of default risk.

Also include your SHAP summary.png and bar plot (GitHub will show image preview).

5. Local Interpretability – 5 Cases (Task 3)

1 False Positive

1 False Negative

1 Correct Default

1 Correct Non-Default

1 Borderline

Explain each using Waterfall plot + force plot.

6. Comparison of Model-Feature Importance vs SHAP vs Permutation (Task 4)

Compare:

XGBoost’s native feature importance

SHAP mean absolute values

Permutation importance ranking

Discuss:

Where do rankings match?

Where do they differ?

Possible reasons (correlations, tree splitting behavior, etc.)

7. Executive Summary (Task 5)

Clear non-technical insights for bank loan officers.
Example statements:

Customers with high payment delays and consistently high bill amounts have the greatest risk.

Recent repayment behavior (PAY_0) is the strongest short-term signal.

LIME/SHAP local decisions help justify approvals/rejections.
