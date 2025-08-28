# 🧑‍💼 Employee Attrition Risk Prediction



[!\[Python](https://img.shields.io/badge/python-3.11-blue)](https://www.python.org/downloads/release/python-3110/)

[!\[scikit-learn](https://img.shields.io/badge/scikit--learn-1.3+-F7931E?logo=scikit-learn\&logoColor=white)](https://scikit-learn.org/stable/)

[!\[XGBoost](https://img.shields.io/badge/XGBoost-1.7+-00599C)](https://xgboost.readthedocs.io/)

[!\[SHAP](https://img.shields.io/badge/SHAP-0.44+-red)](https://shap.readthedocs.io/)

[!\[JupyterLab](https://img.shields.io/badge/JupyterLab-4.0+-F37626?logo=Jupyter\&logoColor=white)](https://jupyter.org/)





## 📌 Project Overview

This project predicts the probability of employee attrition using structured HR data.  

The goal is not just to classify employees as “Yes/No attrition,” but to generate \*\*calibrated probabilities\*\* that HR can use for \*\*risk-based intervention planning\*\*.



- \*\*Dataset:\*\* IBM HR Analytics Employee Attrition dataset (Kaggle)  

\- \*\*Modeling Approach:\*\* Logistic Regression, Random Forest, and XGBoost were benchmarked.  

\- \*\*Final Model:\*\* Tuned and calibrated \*\*XGBoost\*\* selected for deployment.  

\- \*\*Key Outcome:\*\* Attrition probabilities that allow HR to set \*\*resource-aware thresholds\*\*.  



---



\## 🛠 Project Structure



├── data/

│ ├── employee\_attrition.csv # cleaned dataset from Notebook 1

│

├── notebooks/

│ ├── 1\_data\_wrangling\_EDA.ipynb # Cleaning + exploratory analysis

│ ├── 2\_preprocessing\_training.ipynb# Baseline models + calibration

│ ├── 3\_modeling\_results.ipynb # Tuning, SHAP, KS, HR-ready outputs

│

├── models/

│ ├── preprocessor\_final.joblib # Preprocessing pipeline

│ ├── xgb\_model\_calibrated.joblib # Final calibrated XGBoost model

│ ├── metadata\_final.json # Metadata (features, metrics, thresholds)

│ ├── top10\_risk\_drivers.csv # Top 10 employees with SHAP drivers

│

├── README.md # Project documentation





---



\## 📊 Key Results



\- \*\*Final Model:\*\* Calibrated XGBoost  

\- \*\*Test ROC-AUC:\*\* ~0.78  

\- \*\*Brier Score:\*\* 0.105 (improved after isotonic calibration)  

\- \*\*Threshold Scenarios:\*\*

&nbsp; - \*\*0.30:\*\* 40 flagged, Recall ~45%, Precision ~53%  

&nbsp; - \*\*0.45 (KS point):\*\* 13 flagged, Recall ~23%, Precision ~85%  



📈 \*\*Recommendation:\*\*  

HR should start with \*\*0.30\*\* for recall-focused interventions.  

If resources are constrained, fallback to \*\*0.45 (KS point)\*\* for fewer but higher-confidence interventions.  



---



\## 🔎 Interpretability

\- \*\*Global Drivers (SHAP):\*\*  

&nbsp; - Overtime (Yes) → strong positive driver of attrition  

&nbsp; - Job Role (Sales Representative, Laboratory Technician) → higher risk  

&nbsp; - Monthly Income (low) → higher risk  

&nbsp; - Shorter tenure (YearsAtCompany, TotalWorkingYears) → higher risk  



\- \*\*Local Explanations (SHAP):\*\*  

&nbsp; - Each flagged employee receives top 3 SHAP drivers explaining their risk score.  

&nbsp; - Business teams can understand \*why\* someone is flagged, not just the score.  



---



\## 🚀 Future Work

\- \*\*Modeling Enhancements:\*\* Explore LightGBM / CatBoost, cost-sensitive learning, SMOTE oversampling.  

\- \*\*Data Enrichment:\*\* Engagement surveys, promotion history, external benchmarks.  

\- \*\*Deployment:\*\* Streamlit / Power BI dashboards, automated scoring pipelines, HR API integration.  

\- \*\*Business Strategy:\*\* Link attrition costs to threshold selection for ROI-driven HR planning.  



---



\## 📦 Reproducibility

Artifacts saved in `models/` directory ensure reproducibility:  

\- Preprocessor (`preprocessor\_final.joblib`)  

\- Final Calibrated XGB (`xgb\_model\_calibrated.joblib`)  

\- Metadata (`metadata\_final.json`)  

\- Risk Report (`top10\_risk\_drivers.csv`)  



Run the notebooks in order (1 → 2 → 3) to reproduce results.  



---



\## ⚡ Getting Started



\### 1. Clone the Repository

```bash

git clone https://github.com/<your-username>/employee-attrition-risk.git

cd employee-attrition-risk



\### 2. Create \& Activate Environment

conda create -n attrition python=3.11 -y

conda activate attrition



\### Install Requirements

pip install -r requirements.txt



\### 4. Run Notebooks



Start JupyterLab: jupyter lab



Then open and run notebooks in order:



1\_data\_wrangling\_EDA.ipynb



2\_preprocessing\_training.ipynb



3\_modeling\_results.ipynb



\### 5. Inspect Artifacts



Saved models and reports will be in the models/ directory.



🎯 Conclusion



This project delivers a production-ready, explainable attrition risk model.

It empowers HR leaders to:



Intervene early with high-risk employees



Adjust thresholds based on budget/resources



Understand why employees are at risk via SHAP interpretability



The result is a data-driven decision-support tool for workforce retention and strategic HR planning.





