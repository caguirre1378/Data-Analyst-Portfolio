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

> **Goal** — Predict churn and understand *why* customers leave so telecom teams can intervene earlier.  
> **Stack** — Python (pandas, numpy, scikit-learn, matplotlib, seaborn), SHAP; Jupyter Notebook.  
> **Data** — Telco Customer Churn (Kaggle), ~7,000 customers, 21 attributes including contract, tenure, and billing info.

---

## At a glance
- Built a complete **churn prediction pipeline** using supervised learning, with clean preprocessing and model comparison.
- Trained a **Random Forest** classifier and benchmarked it against **Logistic Regression** for interpretability.
- Used **SHAP** to explain model decisions — both globally (feature ranking) and locally (case-specific explanations).
- Extracted business-focused recommendations tailored to **retention**, **pricing strategy**, and **payment behavior**.

---

## Data & preparation
- Cleaned missing values and converted `TotalCharges` from string to float for numerical operations.
- Dropped unique IDs (`customerID`) and encoded categorical features with one-hot encoding.
- Scaled continuous columns like `MonthlyCharges` and `Tenure` to prep for logistic models.
- Created visual summaries (correlation heatmaps, barplots) to understand churn patterns before modeling.

---

## Models & evaluation
- Trained a **Random Forest** as the primary model due to its ability to handle non-linear interactions.
- Logistic Regression was used as a **baseline model** for quick interpretability.
- Evaluation was done using **confusion matrix**, **classification report**, and **precision/recall curves**.
- Focused on optimizing **recall for the churn class**, ensuring fewer at-risk customers were missed.

> **Why these two?**  
> Logistic Regression offers transparency and coefficients; Random Forest finds complex churn patterns like *tenure × contract type*. Together they show accuracy vs explainability tradeoffs.

---

## Explainability
- Applied **SHAP** (SHapley Additive Explanations) to both models for post-hoc interpretability.
- **Top global features**: `Contract`, `Tenure`, `MonthlyCharges`, and `PaymentMethod` emerged as churn signals.
- Local SHAP plots helped explain *why* individual customers were flagged, useful for support teams and marketing segmentation.

---

## Business insights
- **Short-tenure customers on month-to-month contracts** had the highest churn — loyalty risk.
- **Higher billing amounts** correlated with churn, possibly tied to perceived value or pricing concerns.
- Customers paying with **electronic check** churned more than those using **credit cards or autopay**.
- Data suggests that **billing friction** and **lack of contract commitment** are key retention factors.

**Recommendations**
- Incentivize **annual contracts** for new users (<12 months) to improve loyalty.
- Add value to **high-cost plans** through bundled services or promotions.
- Promote **autopay enrollment** to reduce churn tied to billing inconvenience.
- Use the model to trigger **outbound save campaigns** and **early alerts** based on churn scores.

---

## Reproduce
1. Download the **Telco Churn dataset** from Kaggle.  
2. Open `telco_churn_analysis.ipynb` in Jupyter Notebook.  
3. Follow the cells in order — from data cleaning to modeling, SHAP, and insight generation.

🔗 [View the code on GitHub](https://github.com/caguirre1378/Data-Analyst-Portfolio)

---

## Next
- Add **probability calibration** (Platt scaling / Isotonic regression) for marketing thresholds.  
- Incorporate **XGBoost** with monotonic constraints for robust churn modeling.  
- Build an **inference script** to monitor class balance, model drift, and prediction quality over time.
