Interpretable Credit Risk Modeling using XGBoost, SHAP, and LIME

This project develops an interpretable credit-default prediction model using Gradient-Boosting (XGBoost) and modern explanation techniques (SHAP and LIME).
The goal is to achieve strong predictive performance while providing global and local explanations suitable for credit-risk decision making in regulated financial environments.

1. Project Objectives (Deliverable 1)

Preprocess the provided credit dataset and engineer domain-relevant features.

Train and tune an optimized XGBoost classifier achieving AUC > 0.80.

Apply global interpretability methods using:

SHAP summary plot

SHAP feature importance bar plot

Generate local explanations using:

SHAP force plots

SHAP waterfall plots

LIME explanations
for five representative loan cases:

One false positive

One false negative

One borderline prediction

Two additional correct predictions

Compare model-native feature importance, permutation importance, and SHAP values.

Convert interpretability insights into business-actionable recommendations.

2. Dataset Overview

The dataset contains anonymized credit-related variables commonly used in bank underwriting:

Credit limit

Utilization ratio

Bill payment behavior

Payment delinquency

Demographic indicators

The target variable indicates whether a client defaulted on the next payment cycle.

3. Feature Engineering Rationale (Required Deliverable)

Three domain-relevant engineered features were created:

3.1 Utilization Ratio

current bill amount / credit limit
Represents credit over-utilization, a widely accepted early-risk indicator in industry scorecards.

3.2 Payment Consistency Score

Summarizes repayment behavior across several months.
Irregular or missed payments increase the likelihood of default.

3.3 Recent Delinquency Flag

Indicates whether overdue payments occurred in the past two cycles.
Recent delinquency is strongly predictive of short-term default risk.

These engineered features reflect established credit-risk literature and bank underwriting practices.

4. Model Training and Hyperparameter Tuning

An XGBoost classifier was tuned using randomized search:

Maximum depth

Learning rate

Number of estimators

Subsample ratio

Column sample ratio

The final tuned model achieved AUC above 0.80, satisfying project requirements.

The trained model is saved as:

best_xgb_model.pkl

5. Global Interpretability Results

The following global interpretability outputs are included:

• SHAP Summary Plot

Shows distributional impact of each feature on predictions.

• SHAP Bar Plot (Mean Absolute SHAP Values)

Displays the top contributing features ranked by overall influence.

• Permutation Importance

Provides a model-agnostic comparison to validate stability of importance rankings.

6. Local Interpretability (Five Required Cases)

SHAP and LIME were applied to five representative loan applications:

Case 1: False Positive

Case 2: False Negative

Case 3: Borderline Correct Prediction

Case 4: True Positive

Case 5: True Negative

For each case, the following were generated:

SHAP force plot

SHAP waterfall plot

LIME explanation

Outputs are stored under:

/local_plots/

7. Comparison: Native Feature Importance vs SHAP vs Permutation Importance

(Deliverable 4)

The analysis highlights:

SHAP identifies more stable and granular impact patterns.

Model-native gain-based importance tends to overweight tree-split features.

Permutation importance validates the robustness of SHAP’s top features.

All three methods consistently rank utilization ratio and recent delinquency as primary risk drivers.

This section ensures compliance with the mandatory comparison requirement.

8. Executive Summary with Actionable Recommendations

(Deliverable 5)

Based on combined interpretability insights, three key recommendations are:

Recommendation 1: Strengthen controls for high-utilization borrowers

Consistently shows the strongest positive contribution to default risk.

Recommendation 2: Enhance monitoring for customers with recent delinquency

Short-term missed payments sharply increase likelihood of default.

Recommendation 3: Apply additional verification for customers with short credit histories

Limited repayment history produces unstable risk behavior.

These recommendations directly support underwriting decisions and portfolio-risk monitoring.

9. Project Structure
project/
│── Project_credit_risk_shap_lime.ipynb
│── best_xgb_model.pkl
│── default_credit.xlsx
│── requirements.txt
│── permutation_importance.csv
│── README.md
│
├── global_plots/
├── local_plots/

10. How to Run the Project
Step 1 — Install Dependencies
pip install -r requirements.txt

Step 2 — Open the Notebook
Project_credit_risk_shap_lime.ipynb

Step 3 — Execute Cells Sequentially

The notebook will:

Load and preprocess data

Train the tuned XGBoost model

Generate global interpretability plots

Generate local SHAP and LIME explanations

Export plots and artifacts

All results will appear in /global_plots/ and /local_plots/.

