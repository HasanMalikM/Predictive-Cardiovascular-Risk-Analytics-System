# Predictive Cardiovascular Risk Analytics System
### A Machine Learning–Driven Clinical Decision Support Framework

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![XGBoost](https://img.shields.io/badge/Library-XGBoost-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

## 📌 Executive Summary
Cardiovascular diseases (CVDs) remain the leading cause of global mortality. This project delivers an end-to-end Machine Learning Clinical Decision Support System (CDSS) trained on multi-center patient data from the UCI Machine Learning Repository[cite: 1, 2]. By leveraging advanced data preprocessing, multivariate imputation (MICE), and supervised ensemble learning, the framework stratifies patient cardiac risk to optimize diagnostic workflows, reduce false negatives, and support clinical decision-making[cite: 1, 2].

---

## 👥 Authors & Supervision
* **Project Team:** Muhammad Hassaan Malik, Muhammad Imran, Muhammad Fawad Khan, Zubair Ansari, Abdur Raheem[cite: 1, 2]
* **Academic Supervisor:** Dr. Syed Shafqat Mukarram[cite: 1, 2]

---

## 📊 Dataset Overview
The model is trained on a consolidated dataset of **920 patient records** spanning four clinical institutions[cite: 1, 2]:
1. **Cleveland Clinic Foundation** (USA)[cite: 1, 2]
2. **Hungarian Institute of Cardiology** (Budapest)[cite: 1, 2]
3. **University Hospital of Zurich** (Switzerland)[cite: 1, 2]
4. **VA Medical Center** (Long Beach, CA)[cite: 1, 2]

### Target Variable (`num`)
The original ordinal scale ($0$ = normal; $1\text{--}4$ = progressive heart disease) was binarized for clinical risk screening[cite: 1, 2]:
* **Class 0 (Low Risk / Healthy):** $411$ patients ($44.7\%$)[cite: 2]
* **Class 1 (High Risk / Disease Present):** $509$ patients ($55.3\%$)[cite: 2]

---

## 🛠️ Data Pipeline & Methodology

1. **Feature Engineering & Selection:**
   * **Dropped Features:** `ca` ($66.4\%$ missing) and `thal` ($52.8\%$ missing) were pruned to preserve dataset integrity and prevent severe imputation bias[cite: 1, 2].
   * **MICE Imputation:** Applied to features with moderate missingness (`trestbps`, `chol`, `slope`)[cite: 1, 2].
2. **Standardization & Categorical Encoding:**
   * One-Hot Encoding applied to nominal variables (`sex`, `cp`, `fbs`, `restecg`, `exang`, `slope`)[cite: 1, 2].
   * Z-score Standardization (`StandardScaler`) applied to continuous numerical variables (`age`, `trestbps`, `chol`)[cite: 1, 2].

---

## 📈 Model Performance & Results

Evaluated using Stratified 5-Fold Cross-Validation and an 80/20 Holdout Test Set ($185$ patients)[cite: 1, 2]:

| Model | Accuracy | Recall (Sensitivity) | Precision | ROC-AUC | Primary Strategic Role |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Logistic Regression** | $78.26\%$ | $83.33\%$ | $78.43\%$ | $0.7972$ | Transparent, interpretable baseline[cite: 1, 2] |
| **Random Forest** | $84.78\%$ | **$90.20\%$** ★ | $83.64\%$ | $0.9070$ | **Clinical Recall Champion**[cite: 1, 2] |
| **XGBoost Classifier** | **$85.33\%$** ★ | $87.25\%$ | **$86.41\%$** ★ | **$0.9151$** ★ | **Overall Discriminatory Champion**[cite: 1, 2] |

> ★ *Clinical Priority: Random Forest was selected as the optimal model for screening due to its superior **$90.20\%$ Recall**, minimizing dangerous false negatives[cite: 1, 2].*

---

## 🏥 Clinical Triage Engine & Operational Impact

The continuous risk output is converted into a 3-tier clinical action path[cite: 1, 2]:

* 🟢 **Low Risk ($<35\%$ Probability):** Routine annual check-up; avoids redundant non-invasive testing[cite: 1, 2].
* 🟡 **Medium Risk ($35\%\text{--}70\%$ Probability):** Outpatient follow-up, lifestyle management, continuous BP monitoring, and 90-day re-evaluation[cite: 1, 2].
* 🔴 **High Risk ($>70\%$ Probability):** Immediate clinical escalation, priority cardiologist consultation, and scheduled diagnostic catheterization[cite: 1, 2].

### **Projected ROI & Impact**
* **$30\%\text{--}40\%$ Reduction** in redundant diagnostic imaging/stress tests for low-risk groups[cite: 1].
* **$25\%$ Faster Referral Rate** for high-risk patients requiring early therapeutic intervention[cite: 1].

---

## ⚙️ Installation & Usage

```bash
# Clone the repository
git clone [https://github.com/your-username/cardiovascular-risk-analytics.git](https://github.com/your-username/cardiovascular-risk-analytics.git)
cd cardiovascular-risk-analytics

# Install dependencies
pip install -r requirements.txt

# Run main evaluation script
python main.py
