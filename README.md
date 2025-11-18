# Interpretable Credit Risk Modeling using XGBoost, SHAP, and LIME

This project builds an interpretable credit-default prediction model using Gradient Boosting Machines (XGBoost) along with SHAP and LIME to provide global and local explanations suitable for regulated financial environments.

---

## 1. Project Objectives (Deliverable 1)

The key objectives are:

1. Preprocess the provided credit dataset and engineer domain-relevant features.
2. Train and tune an optimized XGBoost classifier achieving an AUC score greater than 0.80.
3. Apply global interpretability techniques including:
   - SHAP summary plot  
   - SHAP feature-importance bar plot
4. Generate local explanations for five representative loan cases using:
   - SHAP force plots  
   - SHAP waterfall plots  
   - LIME explanations
5. Compare model-native feature importance, permutation importance, and SHAP values.
6. Convert interpretability findings into business-actionable recommendations.

---

## 2. Dataset Overview

The dataset contains anonymized credit-related variables commonly used in lending and underwriting. Key attributes include:

- Credit limit  
- Utilization ratio  
- Bill payment behavior  
- Payment delinquency indicators  
- Demographic attributes  

The target variable indicates whether a client defaulted in the next payment cycle.

---

## 3. Feature Engineering Rationale (Deliverable 1 Requirement)

Three domain-relevant engineered features were added:

### 3.1 Utilization Ratio
`current bill amount / credit limit`  
A widely recognized early-risk indicator used in credit scorecards.

### 3.2 Payment Consistency Score
Summarizes monthly repayment behavior. Irregular or missed payments increase default likelihood.

### 3.3 Recent Delinquency Flag
Indicates whether overdue payments occurred in the last two billing cycles. Short-term delinquency strongly increases default risk.

These engineered features are consistent with credit-risk literature and common underwriting practices.

---

## 4. Model Training and Hyperparameter Tuning

An XGBoost classifier was tuned using randomized search over the following parameters:

- Maximum depth  
- Learning rate  
- Number of estimators  
- Subsample ratio  
- Column sample ratio  

The final tuned model achieved an AUC score exceeding 0.80, meeting project requirements.

The trained model is saved as:
`best_xgb_model.pkl`

---

## 5. Global Interpretability Results

The following global interpretability outputs are included:

### SHAP Summary Plot
Displays distribution and directionality of feature effects.

### SHAP Bar Plot (Mean Absolute SHAP Values)
Ranks the top contributing features by overall influence.

### Permutation Importance
Provides a model-agnostic baseline to validate importance ordering.

These analyses highlight utilization ratio and recent delinquency as the most influential default predictors.

---

## 6. Local Interpretability (Five Required Cases)

Five representative loan applications were selected:

1. False Positive  
2. False Negative  
3. Borderline Correct Prediction  
4. True Positive  
5. True Negative  

For each case, the following explanations were generated:

- SHAP force plot  
- SHAP waterfall plot  
- LIME explanation  

All outputs are saved in:

```
/local_plots/
```

---

## 7. Comparison: Feature Importance vs SHAP vs Permutation (Deliverable 4)

The comparative analysis demonstrates:

- Model-native gain-based importance tends to favor tree-split features.
- SHAP identifies more stable and granular feature effects.
- Permutation importance confirms stability of the top-ranked features.

All three methods consistently identify high utilization and recent delinquency as primary predictors.

---

## 8. Executive Summary and Actionable Recommendations (Deliverable 5)

Based on interpretability findings, the following recommendations are proposed:

### Recommendation 1: Strengthen controls for high-utilization borrowers
High utilization consistently shows strong positive contribution toward default.

### Recommendation 2: Increase monitoring of recently delinquent customers
Short-term missed payments sharply elevate default likelihood.

### Recommendation 3: Apply secondary verification for customers with short credit histories
Limited repayment history introduces instability in risk evaluation.

These recommendations directly support underwriting decisions and portfolio risk management.

---

## 9. Project Structure

```
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
```

---

## 10. How to Run the Project

### Step 1 — Install Dependencies
```
pip install -r requirements.txt
```

### Step 2 — Open the Notebook
```
Project_credit_risk_shap_lime.ipynb
```

### Step 3 — Execute Cells Sequentially

Running the notebook will:

- Load and preprocess the dataset  
- Train the tuned XGBoost model  
- Generate global SHAP visualizations  
- Produce local SHAP and LIME explanations  
- Export all figures and artifacts  

Outputs are generated under:

```
/global_plots/
/local_plots/
```

---

This README provides a complete, structured description of the project and fulfills all Cultus assessment deliverables.
