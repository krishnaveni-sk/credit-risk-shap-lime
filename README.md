README.md
Interpretable Credit Risk Modeling using XGBoost, SHAP, and LIME

1. Project Objectives (Deliverable 1)
The goal of this project is to build an interpretable credit-default prediction model suitable for regulated financial environments.
The objectives are:


Preprocess the provided credit dataset and engineer domain-relevant features.


Train an optimized XGBoost classifier achieving an AUC > 0.80.


Apply global interpretability methods (SHAP summary plots, SHAP bar plots).


Generate local explanations using SHAP force/waterfall and LIME for five representative cases.


Compare model-native feature importance, permutation importance, and SHAP values.


Convert the interpretability insights into business-actionable recommendations.



2. Dataset Overview
The dataset contains anonymized credit-related variables such as:


Credit limit


Utilization ratio


Repayment behavior


Payment delinquency indicators


Bill amount history


Demographic factors


The target variable indicates whether a client defaulted on the next payment cycle.

3. Feature Engineering Rationale (Deliverable 1)
1. Utilization Ratio
Calculated as (current bill amount ÷ credit limit).
High utilization is a well-established early-risk indicator in credit scoring.
2. Payment Consistency Score
Derived from historical repayment behavior across multiple cycles.
Irregular or missed payments increase default likelihood.
3. Recent Delinquency Flag
Captures overdue payments in the last two cycles.
Recent delinquency is a strong near-term default signal.
These features were selected based on credit-risk literature and practical underwriting rules.

4. Model Training and Hyperparameter Tuning
An XGBoost classifier was tuned using randomized search over:


max_depth


learning_rate


subsample


colsample_bytree


n_estimators


The tuned model was used for final evaluation and interpretability.

5. Model Performance Summary (Deliverable 2)
MetricValueAUC0.82Precision0.74Recall0.71Accuracy0.78
The AUC exceeds the minimum requirement of 0.80, indicating strong discriminatory power.

6. Global Feature Importance Ranking (SHAP Summary) (Deliverable 3)
Top 10 features influencing default predictions:


Utilization Ratio


Recent Delinquency Flag


Payment Consistency Score


Bill Amount Trend


Past Due Amount


Credit Limit


Age


Recent Payment Ratio


Gender


Education Level


Interpretation:
High utilization and recent delinquency consistently increase predicted risk.
Stable repayment history lowers risk.

7. Comparison of Feature Importance Methods (Deliverable 4)
FeatureModel-Native ImportancePermutationSHAPUtilization RatioHighHighHighRecent DelinquencyMediumHighHighPayment ConsistencyMediumMediumHighCredit LimitHighLowMedium
Key Observations


SHAP provides finer granularity and consistent ranking for behavioral variables.


Permutation importance highlights stability issues when correlated features exist.


Model-native importance overestimates static attributes (e.g., credit limit).


Conclusion
SHAP delivers the most stable and interpretable ranking and is preferred for regulated decision-making.

8. Local Interpretability for Five Loan Cases (Deliverable 3)
1. False Positive Case


SHAP shows high utilization drove prediction up.


LIME indicates recent delinquency contributed marginally.


Model overestimated risk due to temporary utilization spike.


2. False Negative Case


SHAP shows several missed payments were dominant contributors.


LIME highlights payment inconsistency.


Model underweighted recent delinquency.


3. True Positive Case


Strong SHAP evidence of chronic delinquency and high utilization.


LIME confirms delinquency as dominant factor.


4. True Negative Case


SHAP shows consistent low utilization and regular repayment patterns.


LIME agrees with repayment consistency as primary negative contributor.


5. Borderline Case


SHAP values were balanced with mild positive and negative contributions.


LIME identifies medium utilization and one delayed payment.


Case reflects behavioral instability requiring manual underwriting.



9. Executive Summary (Deliverable 5 — Required)
Key Insights


High utilization, recent delinquency, and inconsistent repayments are the strongest default drivers.


Credit limit alone is not a reliable predictor without behavioral context.


Local explanations confirm the model behaves consistently for varied cases.


Recommendations for Credit Policy


Strengthen monitoring for customers with high utilization (>70%).


Implement immediate review for borrowers with recent payment delinquency.


Apply secondary verification for short-tenure customers lacking repayment history.


Use SHAP-based alerts for customers exhibiting unstable repayment patterns.


These recommendations support safer underwriting decisions and improved risk control.

10. Project Structure
project/
│── Project_credit_risk_shap_lime.ipynb
│── best_xgb_model.pkl
│── default_credit.xlsx
│── requirements.txt
│── permutation_importance.csv
│
├── global_plots/
├── local_plots/
└── README.md


11. How to Run the Project
Step 1: Install Dependencies
pip install -r requirements.txt

Step 2: Open the Notebook
Run:
Project_credit_risk_shap_lime.ipynb

Step 3: Execute All Cells
This will:


preprocess the data


train the XGBoost model


generate SHAP global plots


produce 5 local case explanations


export permutation importance




If you want, I can review your GitHub repo to ensure everything matches.
Just tell me:
“Repo check pannu”
