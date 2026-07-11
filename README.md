# **Credit Risk Modeling using Logistic Regression, Random Forest, LightGBM, SHAP, and LLM-Based Credit Decisioning**

## Objective

Given a set of borrower and loan attributes, predict the likelihood of loan default and support credit decisioning (approve, reject, or adjust loan terms).

[Google Colab Notebook](https://colab.research.google.com/drive/1mBRIrzCb1y3ZDyoWiEWs14H0P40ie7WJ#scrollTo=vtQfF4YIWK2C)

---

## Dataset

- Large-scale consumer lending dataset
- Binary target: **Default (1)** vs **Fully Paid (0)**
- Significant class imbalance handled explicitly

---

## Modeling Approach

### 1. Logistic Regression (Baseline)

- Used as an interpretable linear baseline
- Applied feature scaling
- Addressed class imbalance using `class_weight='balanced'`
- Performed decision threshold tuning to improve recall

### 2. Random Forest (Intermediate)

- Captured non-linear relationships and feature interactions
- Improved ROC-AUC over Logistic Regression
- Feature importance analysis highlighted interaction-heavy variables such as interest rate and loan structure

### 3. LightGBM (Final Model)

- Gradient-boosted trees for scalable, high-performance modeling
- Achieved the best ranking performance among all models
- **ROC-AUC ≈ 0.73**, outperforming Logistic Regression and Random Forest

---

## Key Results

| Model | ROC-AUC |
|--------|--------:|
| Logistic Regression | ~0.71 |
| Random Forest | ~0.724 |
| LightGBM | **~0.732** |

- Boosting models confirmed the presence of non-linear effects and feature interactions.
- Threshold tuning significantly improved recall for defaulters.
- Time-based (`issue_ordinal`), income, debt, and credit utilization features emerged as dominant risk drivers.

---

## SHAP Interpretation of the LightGBM Credit Risk Model

To better understand how the model predicts loan default risk, **SHAP (SHapley Additive exPlanations)** was used to explain individual predictions and quantify feature contributions. The SHAP summary plot highlights the most influential variables affecting predicted default probability.

### Overall Insight

The SHAP analysis shows that the model primarily relies on economically meaningful credit risk indicators such as borrower credit grade, debt-to-income ratio, interest rate, and credit utilization. These variables are widely used in real-world credit scoring systems, indicating that the model captures realistic borrower risk patterns rather than relying on spurious correlations.

---

## LLM-Based Credit Decisioning Extension

While the predictive models estimate the **probability of loan default**, they do not directly translate predictions into lending decisions or provide policy-aware explanations. As an exploratory extension, an **LLM-based decisioning layer** was investigated to bridge this gap.

The framework combines:

- Predicted default probability
- SHAP feature explanations
- Lending policy rules

to generate **explainable, policy-aware credit recommendations**.

Two prompting strategies were explored:

- **Generation Model (GPT-4o-mini):** Executes predefined lending workflows using structured prompts to produce consistent policy-based decisions such as **Approve, Reject, or Approve with Conditions**.
- **Reasoning Model (o1-mini):** Performs autonomous credit evaluation by reasoning over borrower risk, SHAP explanations, and lending policies to generate explainable credit decisions with supporting justifications.

This extension demonstrates how **Machine Learning**, **Explainable AI (SHAP)**, and **Generative AI** can be integrated into a unified, transparent credit decision support pipeline.

---

## Business Insights

- Borrower risk is driven by a combination of income capacity, debt burden, credit utilization, loan structure, and time effects.
- Linear models underestimate conditional effects such as interest rate and installment interactions.
- Gradient boosting provides a better balance between predictive accuracy and scalability.
- Model outputs can support:
  - Rejecting high-risk applicants
  - Adjusting loan tenure, credit limits, or pricing for medium-risk applicants
  - Approving low-risk applicants under standard terms

---

## Conclusion

A progressive modeling strategy (**Logistic Regression → Random Forest → LightGBM**) demonstrated that credit default risk exhibits strong non-linear and interaction-driven behavior, with **LightGBM** delivering the best predictive performance. **SHAP** enhanced model interpretability by explaining feature contributions, while the exploratory **LLM-based decisioning layer** extended the pipeline by transforming model predictions into explainable, policy-aware lending recommendations. Together, the pipeline illustrates how predictive machine learning, explainable AI, and Generative AI can be combined to support intelligent, transparent credit decisioning.
