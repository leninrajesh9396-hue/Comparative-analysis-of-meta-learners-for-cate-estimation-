# Heterogeneous Treatment Effect Estimation Using Meta-Learners  
### *S-Learner vs T-Learner Comparison with Uplift & Qini Curves*

---

## 1. **Project Objective**
The goal of this project is to estimate **Conditional Average Treatment Effects (CATE)** using two meta-learning approaches:

- **S-Learner**  
- **T-Learner**

The project evaluates which model better identifies users who benefit from treatment by using **uplift modeling techniques**.

---

## 2. **Dataset Description**
A custom-generated uplift modeling dataset was used:

- **Rows:** 20,000  
- **Columns:**  
  - `x1`, `x2`: Numerical continuous features  
  - `x3`: Categorical (integer)  
  - `x4`: Categorical (A/B/C)  
  - `treatment`: 1 = treated, 0 = control  
  - `target`: Binary outcome (1 = positive response)

This dataset is suitable for uplift modeling because it includes:
- A treatment/control variable  
- Multiple predictive features  
- A clear outcome variable  

---

## 3. **Methodology**

### **3.1 Data Preprocessing**
- Handled categorical features using One-Hot Encoding  
- Created train/test split (70/30 ratio)  
- Ensured treatment was balanced via stratification  

### **3.2 Meta-Learner Models**

#### **S-Learner**
- Trained one model using:  
  `features + treatment`  
- CATE is computed as:  
  `ŷ(T=1) − ŷ(T=0)`

#### **T-Learner**
- Trained **two separate models**:  
  - One for treated samples  
  - One for control samples  
- CATE is computed as:  
  `ŷ1 − ŷ0`

---

## 4. **Evaluation Metrics**

### **4.1 Uplift Curve**  
File: `plots/uplift_curve.png`

The uplift curve measures how well each model distinguishes between customers who benefit from treatment versus those who do not.

**Interpretation:**
- A higher curve indicates a better ability to target the right population.  
- If the S-Learner curve is higher → S-Learner performs better.  
- If the T-Learner curve is higher → T-Learner is superior.

### **4.2 Qini Curve**  
File: `plots/qini_curve.png`

The Qini curve is the standard evaluation metric in uplift modeling.

**Interpretation:**
- Higher Qini curve = larger incremental gain  
- The model with the higher curve is the better CATE estimator  
- The Qini coefficient equals the area between the model curve and the baseline

---

## 5. **Results**

### **5.1 Uplift Curve Results**
- Visual comparison shows how uplift changes across targeted population  
- Model with the steepest rise early on identifies the best subgroup

### **5.2 Qini Curve Results**
- The model with consistently higher Qini gain demonstrates stronger uplift performance  
- Helps determine which learner produces more accurate treatment effect estimates  

---

## 6. **Subgroup Analysis**
Two meaningful subgroups were compared:

### **Subgroup A:** `x1 > 0`  
### **Subgroup B:** `x1 ≤ 0`

**Observations:**
- Subgroup A showed higher average CATE → treatment more effective  
- Subgroup B showed lower or negative uplift → treatment ineffective or harmful  
- Meta-learners successfully differentiated behavior across subgroups

---

## 7. **Conclusion**

- Both S-Learner and T-Learner successfully estimated heterogeneous treatment effects.  
- **Uplift and Qini curves** revealed performance differences:  
  - The model whose curve is consistently above the other provides **better uplift prediction**.  
- Subgroup analysis confirmed that certain user segments benefit more from treatment.  

**Overall:**  
This project demonstrates the effectiveness of meta-learners in personalized treatment assignment and uplift modeling.

---

## 8. **Files Included**
- `simple_uplift_dataset.csv`  
- `plots/uplift_curve.png`  
- `plots/qini_curve.png`  
- `report.md` (this file)

---
