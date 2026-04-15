# BU7156 Group 10 Project  
## Bank Customer Churn Analysis: Data Engineering, Predictive Modelling, and LLM-Assisted Reflection

This repository contains a master's-level analytics assignment for **BU7156 (Analytics in Practice)**.  
The project develops a reproducible churn-analysis pipeline from raw data to validated model outputs, and critically evaluates Large Language Model (LLM) usage in analytical practice.

---

## 1. Research Objective

The project addresses the following practical question:

> **How can customer churn be modelled reliably using structured banking data while preserving methodological rigor and reproducibility?**

A secondary objective is to assess the usefulness and risk of LLMs for insight synthesis, code support, and critical review.

---

## 2. Dataset Description

- **Source file**: `Data/Raw/Bank Customer Churn Prediction.csv`
- **Observations**: 10,000 customers
- **Variables**: 12 columns
- **Target variable**: `churn` (binary outcome)
- **Identifier field**: `customer_id` (excluded from predictive features)

Core variables include credit score, country, gender, age, tenure, account balance, number of products, card ownership, active membership, and estimated salary.

---

## 3. Methodological Pipeline

### 3.1 Data Engineering and Preprocessing
Implemented in: `Notebooks/01_data_cleaning_preprocessing.ipynb`

The preprocessing workflow follows leakage-aware design:

1. Standardize schema and remove duplicate rows.
2. Handle missing values:
   - Numeric features: median imputation
   - Categorical features: mode imputation
3. Split data into train/test **before** fitting transformers.
4. Build a preprocessing pipeline:
   - Numeric: imputation + standardization
   - Categorical: imputation + one-hot encoding (`drop='first'`, unknown categories ignored)
5. Fit transformers on training data only; apply to both train/test.
6. Export cleaned and feature-engineered artifacts.

### 3.2 Model Validation
Implemented in: `Notebooks/03_validation.ipynb`

Three supervised models are compared under consistent settings:

- Logistic Regression
- Random Forest
- XGBoost

Reported evaluation metrics include **Accuracy**, **F1 Score**, and **ROC-AUC**.

### 3.3 LLM Prompt Evaluation
Implemented in: `LLM/03_llm_prompts.ipynb`

Three iterative prompt experiments assess:

1. Insight synthesis quality
2. Code-generation utility (SHAP workflow)
3. Adversarial critique quality

Each experiment documents V1 prompt/output, error analysis, refined V2 prompt/output, and reflection on reliability.

---

## 4. Design Choices and Rationale

This project makes explicit methodological decisions:

- **Leakage prevention**: split-first preprocessing ensures test information does not influence fitted transforms.
- **Reproducibility**: exported datasets and serialized preprocessor (`joblib`) enable repeatable downstream modelling.
- **Model comparability**: multiple model families are benchmarked under a common metric framework.
- **Interpretability awareness**: SHAP-based analysis is used to challenge impurity-based feature importance narratives.
- **Critical GenAI use**: LLM outputs are treated as drafts requiring verification, not as authoritative evidence.

---

## 5. Key Outputs

- `Data/Processed/bank_customer_churn_cleaned.csv`  
  Cleaned dataset for further exploration and checks.
- `Data/Features/bank_customer_churn_train_features.csv`  
  Leakage-safe feature set for model training.
- `Data/Features/bank_customer_churn_test_features.csv`  
  Leakage-safe feature set for held-out evaluation.
- `Models/bank_customer_churn_preprocessor.joblib`  
  Persisted preprocessing object for consistent transformation and deployment alignment.

---

## 6. Repository Structure

```text
BU7156_group10_project/
├── Data/
│   ├── Raw/
│   ├── Processed/
│   └── Features/
├── Notebooks/
│   ├── 01_data_cleaning_preprocessing.ipynb
│   └── 03_validation.ipynb
├── LLM/
│   ├── 03_llm_prompts.ipynb
│   └── README_LLM.md
├── Models/
│   └── bank_customer_churn_preprocessor.joblib
└── read_me.md
```

---

## 7. Reproducibility and Execution Order

Run notebooks in the following order:

1. `Notebooks/01_data_cleaning_preprocessing.ipynb`
2. `Notebooks/03_validation.ipynb`
3. `LLM/03_llm_prompts.ipynb` (prompt log and critical reflection)

Note: the repository currently does not include a pinned environment file (`requirements.txt` / `environment.yml`).

---

## 8. Limitations

- Notebook-driven workflow rather than a packaged pipeline.
- No pinned dependency versions, which may lead to minor metric variation across environments.
- LLM evaluations are qualitative and context-dependent, though verification steps are documented.

---

## 9. Additional Documentation

- Data engineering detail: `read_me.md`
- LLM prompt experiment detail: `LLM/README_LLM.md`

---

*BU7156 — Analytics in Practice (MSc), Group 10, Trinity College Dublin*
