---
layout: single
title: "Telco Customer Churn Analysis"
excerpt: "Predict churn and surface drivers to support targeted retention."
classes: wide
category: ml
tags: [python, classification, churn, shap, sklearn]
thumbnail: /assets/images/telco-splash.png
weight: 10
---

> **Goal** — Predict churn and explain *why* customers leave so retention can be targeted.  
> **Stack** — Python (pandas, numpy, scikit-learn, matplotlib, seaborn), SHAP; Jupyter.  
> **Data** — Telco Customer Churn (Kaggle), ≈7k customers, 21 features.

---

## At a glance
- Cleaned & encoded mixed tabular data; built a **baseline Random Forest** and compared to **Logistic Regression**.  
- Evaluated with precision/recall and a confusion matrix; tuned for recall on the churn class.  
- Added **explainability** with **SHAP** for global and local drivers.  
- Delivered **clear playbook items** for marketing, billing, and product.

---

## Data & preparation
- Converted text‐encoded numerics (e.g., `TotalCharges`) to numeric; handled missing values.
- One-hot encoded categoricals (contract type, internet service, payment method, etc.).
- Removed identifiers (`customerID`) and scaled continuous features where useful.

---

## Models & evaluation
- Trained **RandomForestClassifier** as the primary model; benchmarked against **Logistic Regression**.
- Measured **precision/recall** per class and reviewed the **confusion matrix** to see trade-offs.
- Tuned the threshold/parameters to keep recall healthy on the churn class without spamming positives.

> Why these two?  
> Logistic Regression gives a strong, interpretable linear baseline. Random Forest captures non-linear splits and interactions that often matter in churn (tenure × contract type × charges).

---

## Explainability
- **Global**: SHAP feature importance highlighted **Contract**, **Tenure**, **MonthlyCharges**, and **PaymentMethod** as top drivers.
- **Local**: Case-level SHAP plots used to show why a specific customer was flagged (useful for ops or success teams).

---

## Business insights
- **Month-to-month contracts** and **short tenure** correlate with churn.  
- **Higher monthly charges** increase churn risk → likely pricing pressure.  
- **Electronic check** users churn more; **autopay/credit card** churn less → friction + trust matter.

**Recommendations**
- Target **month-to-month** and **<12-month tenure** with retention offers; nudge to annual terms.
- Bundle or price-protect **high-charge** customers; message value, not just discount.
- Promote **autopay/credit card** enrollment; reduce billing friction and failed payments.
- Use model scores for **outbound saves** and **win-back** campaigns; review SHAP on edge cases.

---

## Reproduce
1. Download the **Telco Customer Churn** dataset from Kaggle.  
2. Open `telco_churn_analysis.ipynb` in Jupyter.  
3. Run cells top-to-bottom (installs, prep, modeling, SHAP, plots).

**Repo**: <https://github.com/caguirre1378/Data-Analyst-Portfolio>

---

## Next
- Calibrate probabilities (Platt/Isotonic) for campaign thresholds.  
- Add monotonic/XGBoost variant and partial dependence checks.  
- Build a tiny **inference + monitoring** script (drift, class balance, alerting).
