# **Credit Risk Modeling using Logistic Regression, Random Forest, and LightGBM**


## **Objective**

Given a set of borrower and loan attributes, predict the likelihood of loan default and support credit decisioning (approve, reject, or adjust loan terms).

[google colab link](https://colab.research.google.com/drive/1mBRIrzCb1y3ZDyoWiEWs14H0P40ie7WJ#scrollTo=vtQfF4YIWK2C) - the link for the project 


## Dataset

1.  Large-scale consumer lending dataset

2.  Binary target: Default (1) vs Fully Paid (0)

3.  Significant class imbalance handled explicitly


## Modeling Approach

## 1. Logistic Regression (Baseline)

  + Used as an interpretable linear baseline
  + Feature scaling applied
  + Class imbalance handled using class_weight='balanced'
  + Decision threshold tuning performed to improve recall

## 2.Random Forest (Intermediate)

  + Introduced to capture non-linear relationships and feature interactions
  + Improved ROC–AUC over logistic regression
  + Feature importance analysis highlighted interaction-heavy variables such as interest rate and loan structure

## 3.LightGBM (Final Model)

  + Gradient-boosted trees for scalable, high-performance modeling
  + Achieved the best ranking performance among all models
  + ROC–AUC ≈ 0.73, outperforming Logistic Regression and Random Forest
    
## Key Results
## Model	          &ensp; &ensp;&ensp;&ensp;&emsp;  &ensp;&ensp;&ensp;&ensp;&ensp;           **ROC–AUC**
**1. Logistic Regression** 	&ensp;&ensp;&ensp;&ensp;&emsp;&ensp; ~0.71


**2. Random Forest**	&ensp;&ensp;&ensp;&ensp;&emsp;&emsp;&ensp;&emsp;~0.724


**3. LightGBM**	&ensp;&ensp;&ensp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;~0.732

+ Bosting models confirmed the presence of non-linear effects and feature interactions
+ Threshold tuning demonstrated significant recall improvement for defaulters
+ Time-based (issue_ordinal), income, debt, and utilization features emerged as dominant risk drivers

## Business Insights

+ Borrower risk is driven by a combination of income capacity, debt burden, utilization, loan structure, and time effects.
+ Linear models underestimate conditional effects such as interest rate and installment interactions
+ Gradient boosting provides a better balance between risk ranking accuracy and scalability
+ Model outputs can be used to:
     + Reject high-risk applicants
     + Adjust loan tenure, limits, or pricing for medium-risk applicants
     +  Approve low-risk applicants under standard terms


## Conclusion

A progressive modeling strategy (Logistic → Random Forest → LightGBM) demonstrated that credit default risk exhibits strong non-linear and interaction-driven behavior. LightGBM delivered the best overall performance and is well-suited for real-world credit risk decisioning.  
