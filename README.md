# Responsible Machine Learning Individual Assignment 5: COMPAS End-to-End Audit

## The Purpose of the Analysis

This project presents a unified, end-to-end responsible machine learning audit of the COMPAS risk assessment system across Assignments 1–5. The analysis evaluates the model from multiple perspectives including **fairness, explainability, predictive performance, generalization, distribution drift, robustness, and adversarial vulnerability**.

The goal of this final stage is to assess not only whether the model is fair and accurate, but also whether it is **secure against attacks, stable under distribution shift, robust to perturbations, and resilient to privacy and poisoning risks**.

Across the full pipeline, the analysis progresses from fairness diagnostics and explainability (early assignments) to robustness, security, and adversarial evaluation (final assignment).

---

## Methods Used Across the Full Pipeline (Assignments 1–5)

### Predictive Modeling & Performance Evaluation
- Logistic Regression (LR): Linear baseline model used for prediction and interpretability analysis.
- Gradient Boosted Trees (GBT): Nonlinear benchmark model used to compare predictive performance and robustness.
- Evaluation Metrics:
  - AUC (Area Under the Curve)
  - Accuracy
  - Log Loss
- Train vs Test comparisons used to evaluate generalization and overfitting.

---

### Fairness, Disparity, and Harm Analysis
- Adverse Impact Ratio (AIR): Measured disparities in favorable outcomes across demographic groups.
- Error Rate Parity:
  - False Positive Rate (FPR)
  - False Negative Rate (FNR)
- Intersectional Analysis: Evaluated compounded disparities across overlapping demographic attributes.
- Standardized Mean Difference (SMD) and Mean Difference (ME): Quantified magnitude of disparities across groups.

---

### Explainability and Interpretability
- SHAP (Shapley Additive Explanations):
  - Global feature importance
  - Local explanations
- LIME (Local Interpretable Model-Agnostic Explanations):
  - Individual-level prediction explanations
- DiCE (Counterfactual Explanations):
  - Identified minimal feature changes needed to flip predictions

---

### Model Robustness & Confidence Analysis (NEW)
- Confidence Gap Analysis (LR vs GBT):
  - Compared prediction confidence distributions between Logistic Regression and Gradient Boosted Trees
  - Evaluated calibration and overconfidence behavior
- Regularization Testing (Logistic Regression):
  - Applied L2 regularization (C tuning) to evaluate stability and overfitting mitigation
  - Examined impact on performance and fairness

---

### Adversarial Machine Learning Attacks (NEW)

- PGD Evasion Attack (Projected Gradient Descent):
  - Tested model vulnerability to adversarial perturbations at inference time
  - Evaluated sensitivity to small input changes

- Poisoning Looping Attack:
  - Simulated iterative data poisoning during training
  - Measured degradation in performance and fairness under corrupted training data

- Membership Inference Attack (MIA):
  - Evaluated whether the model leaks information about training membership
  - Used MI-AUC as a privacy leakage metric

---

### Distribution Drift & Stability
- Population Stability Index (PSI)
- Kolmogorov–Smirnov (KS) Test
- Maximum Mean Discrepancy (MMD²)

Used to detect distribution shift between training and test environments.

---

### Stress Testing & Sensitivity
- Counterfactual perturbations (e.g., priors_count changes)
- Individual Conditional Expectation (ICE) curves
- Feature sensitivity analysis under controlled perturbations

---

### Slice-Based Evaluation
Model performance evaluated across:
- Race groups
- Gender groups
- Age groups

Used to identify subgroup-level performance degradation and fairness disparities.

---

## Python Libraries Used

- pandas
- numpy
- matplotlib
- scikit-learn
- lifelines
- shap
- lime
- dice-ml
- solas-ai
- statsmodels
- scipy

---

## Instructions for Reproducing Results

Install dependencies:

```bash
pip install pandas numpy matplotlib scikit-learn lifelines lime shap dice-ml solas-ai statsmodels scipy
```

Run the Notebook: ```Botti_Nick_RML_Assignment_5_Robustness_and_Security.ipynb```

## A Statement on the Use of AI
Google Gemini (via Google Colab) was used to assist with debugging adversarial attack implementations (PGD, poisoning loop logic, and membership inference evaluation) and to support interpretation of robustness results, particularly when comparing Logistic Regression and Gradient Boosted Trees confidence behavior. All outputs were validated under responsible machine learning analysis standards consistent with course guidelines.
