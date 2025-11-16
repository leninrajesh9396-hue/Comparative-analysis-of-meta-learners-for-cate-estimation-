# Heterogeneous Treatment Effect Estimation Using Meta-Learners

This project estimates Conditional Average Treatment Effects (CATE) using two meta-learning approaches: S-Learner and T-Learner. Model performance is evaluated using uplift and Qini curves, and subgroup analysis is performed to understand treatment heterogeneity.

---

## Project Overview

The objective of this project is to understand how treatment effects vary across individuals. Using a synthetic dataset with numerical and categorical features, treatment assignments, and binary outcomes, the project includes:

- Data preprocessing  
- Implementation of S-Learner and T-Learner models  
- Estimation of CATE values  
- Evaluation through uplift and Qini curves  
- Subgroup analysis  
- Saving plots for interpretation

This workflow demonstrates core techniques in causal machine learning used in marketing, healthcare, and policy design.

---

## Folder Structure

```plaintext
project/
│
├── README.md
├── report.md
├── simple_uplift_dataset.csv
│
├── notebooks/
│     └── hte_analysis.ipynb
│
└── plots/
      ├── uplift_curve.png
      └── qini_curve.png
Technologies Used

Python 3

Pandas

NumPy

Scikit-Learn

Matplotlib

Methodology
1. Data Preprocessing

Applied one-hot encoding for categorical variables

Performed train-test split with stratification on treatment

Ensured clean structure for uplift modeling

2. Meta-Learners Implemented
S-Learner

Trains a single model using all features and treatment as input

Predicts outcomes for treatment and control

CATE = ŷ(T=1) − ŷ(T=0)

T-Learner

Trains two separate models: one on treated samples and one on control

CATE = ŷ_treated − ŷ_control

Evaluation
Uplift Curve

File: plots/uplift_curve.png
Shows how uplift varies when individuals are ranked by predicted treatment effect.

Qini Curve

File: plots/qini_curve.png
Displays cumulative incremental gain. A higher Qini curve indicates better uplift performance.

Subgroup Analysis

Two groups were analyzed to understand treatment heterogeneity:

Group A: x1 > 0

Group B: x1 ≤ 0

Findings: Group A showed higher CATE values, indicating that treatment is more effective for this subgroup.

Conclusion

Both S-Learner and T-Learner effectively estimate heterogeneous treatment effects.

Uplift and Qini curves provide clear comparison between the models.

Subgroup analysis confirms that treatment effects vary across the population.

This project demonstrates essential causal ML methods and can be extended using X-Learner, R-Learner, or Causal Forests.
