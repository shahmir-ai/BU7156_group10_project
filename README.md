# BU7156 Group 10 Project — Bank Customer Churn Analysis

This repository contains the Group 10 BU7156 project on **bank customer churn analysis**, including data engineering, feature preparation, model validation, and LLM prompt evaluation.

## Project Overview

The project is organized as an end-to-end analytics workflow:

1. **Data cleaning and preprocessing**  
   Build leakage-safe training and testing features from raw churn data.
2. **Model validation**  
   Compare baseline and tree-based models (Logistic Regression, Random Forest, XGBoost).
3. **LLM prompt experiments**  
   Evaluate how LLM outputs can support (and mislead) analytical storytelling and interpretation.

## Repository Structure

```text
BU7156_group10_project/
├── Data/
│   ├── Raw/                     # Original dataset
│   ├── Processed/               # Cleaned dataset outputs
│   └── Features/                # Train/test feature-engineered datasets
├── Notebooks/
│   ├── 01_data_cleaning_preprocessing.ipynb
│   └── 03_validation.ipynb
├── LLM/
│   ├── 03_llm_prompts.ipynb
│   └── README_LLM.md
├── Models/
│   └── bank_customer_churn_preprocessor.joblib
└── read_me.md                   # Existing detailed data-engineering readme
```

## Data

- **Raw dataset**: `Data/Raw/Bank Customer Churn Prediction.csv`
- **Rows/columns**: 10,000 rows, 12 columns
- **Target**: `churn`

## Main Artifacts

- `Data/Processed/bank_customer_churn_cleaned.csv`  
  Cleaned dataset after standardization and missing-value handling.
- `Data/Features/bank_customer_churn_train_features.csv`  
  Feature-engineered training data (recommended for model fitting).
- `Data/Features/bank_customer_churn_test_features.csv`  
  Feature-engineered test data (recommended for model evaluation).
- `Models/bank_customer_churn_preprocessor.joblib`  
  Saved preprocessing transformer for reproducible transformations.

## Notebooks

- `Notebooks/01_data_cleaning_preprocessing.ipynb`  
  Data loading, cleaning, leakage-safe preprocessing, and artifact export.
- `Notebooks/03_validation.ipynb`  
  Validation workflow comparing Logistic Regression, Random Forest, and XGBoost.
- `LLM/03_llm_prompts.ipynb`  
  Structured LLM prompt experiments with critique and prompt iteration.

## Quick Start

1. Clone the repository.
2. Open notebooks in Jupyter or VS Code.
3. Run the workflow in order:
   - `Notebooks/01_data_cleaning_preprocessing.ipynb`
   - `Notebooks/03_validation.ipynb`
   - `LLM/03_llm_prompts.ipynb` (documentation/prompt analysis)

## Dependencies

This repo does not currently include a pinned dependency file (`requirements.txt` or `environment.yml`).  
Based on notebook content, typical packages include:

- `numpy`
- `scikit-learn`
- `xgboost`
- `matplotlib`
- `shap` (for explainability work referenced in LLM analysis)

## Additional Documentation

- Root workflow notes: `read_me.md`
- LLM-specific documentation: `LLM/README_LLM.md`

---

*BU7156 — Analytics in Practice, Group 10*
