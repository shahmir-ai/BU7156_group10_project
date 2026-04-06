# Analytics in Practise: Data Engineering and Feature Pipeline

## 1. What Has Been Done (Data Engineering Steps)

The workflow has been implemented in [Notebooks/01_data_cleaning_preprocessing.ipynb](Notebooks/01_data_cleaning_preprocessing.ipynb).

The following steps were completed:

1. Path and folder setup
- Located project root dynamically.
- Connected to raw dataset in [Data/Raw/Bank Customer Churn Prediction.csv](Data/Raw/Bank%20Customer%20Churn%20Prediction.csv).
- Ensured output folders exist: [Data/Processed](Data/Processed), [Data/Features](Data/Features), [Models](Models).

2. Data loading and initial inspection
- Loaded the raw churn CSV.
- Checked shape, sample records, data types, and null presence.

3. Basic cleaning
- Standardized column names (lowercase, trimmed, underscore format).
- Removed exact duplicate rows.

4. Missing value handling
- Generated missing value report.
- Numeric columns: median imputation.
- Categorical columns: most-frequent (mode) imputation.

5. Leakage-safe feature engineering
- Identified target column (for this dataset: churn).
- Removed identifier-like columns from features (for this dataset: customer_id).
- Split data into train/test before fitting preprocessing to avoid leakage.
- Built preprocessing pipeline:
  - Numeric: impute median + standard scale.
  - Categorical: impute mode + one-hot encoding (drop first, ignore unknown).
- Fit preprocessing on train data only.
- Transformed train and test features with the fitted transformer.

6. Class balance check
- Compared churn rate in train and test sets.

7. Artifact export
- Cleaned dataset export.
- Train/test engineered feature exports.
- Persisted fitted preprocessor artifact for reuse.

## 2. Project Structure

- [Data](Data): Data lifecycle folders.
- [Data/Raw](Data/Raw): Original source data.
- [Data/Processed](Data/Processed): Cleaned but not necessarily model-split outputs.
- [Data/Features](Data/Features): Feature-engineered datasets for modeling.
- [Notebooks](Notebooks): Notebook workflows.
- [Models](Models): Saved preprocessing/model artifacts.
- [Images](Images): Visual outputs (currently empty).
- [.venv](.venv): Local Python environment.

## 3. File-by-File Understanding

### Notebook
- [Notebooks/01_data_cleaning_preprocessing.ipynb](Notebooks/01_data_cleaning_preprocessing.ipynb)
  - Main data engineering notebook.
  - Runs cleaning, preprocessing pipeline, train/test feature generation, and export.

### Raw Data
- [Data/Raw/Bank Customer Churn Prediction.csv](Data/Raw/Bank%20Customer%20Churn%20Prediction.csv)
  - Original unprocessed source dataset.

### Processed Data
- [Data/Processed/bank_customer_churn_cleaned.csv](Data/Processed/bank_customer_churn_cleaned.csv)
  - Cleaned dataset after standardization, deduplication, and missing value handling.
  - Useful for EDA and validation checks.

### Feature Data
- [Data/Features/bank_customer_churn_train_features.csv](Data/Features/bank_customer_churn_train_features.csv)
  - Engineered training set.
  - Includes transformed features and churn target.
  - Use this file to fit models.

- [Data/Features/bank_customer_churn_test_features.csv](Data/Features/bank_customer_churn_test_features.csv)
  - Engineered test set.
  - Same schema as train features.
  - Use this file to evaluate models.

- [Data/Features/bank_customer_churn_features.csv](Data/Features/bank_customer_churn_features.csv)
  - Legacy combined feature output from earlier notebook iteration.
  - Not the preferred file for current train/test modeling workflow.

### Model Artifact
- [Models/bank_customer_churn_preprocessor.joblib](Models/bank_customer_churn_preprocessor.joblib)
  - Saved fitted preprocessing transformer.
  - Reuse this for consistent transformation during inference/deployment.

## 4. Which File Should Be Used Specifically for Feature Engineering?

Use these two files as the primary engineered datasets:

1. [Data/Features/bank_customer_churn_train_features.csv](Data/Features/bank_customer_churn_train_features.csv)
2. [Data/Features/bank_customer_churn_test_features.csv](Data/Features/bank_customer_churn_test_features.csv)

Why these are the correct files:
- They are leakage-safe (split before fit-transform).
- They share consistent engineered schema.
- They are intended directly for training and evaluation.

Use [Data/Features/bank_customer_churn_features.csv](Data/Features/bank_customer_churn_features.csv) only as a historical/legacy output reference.

## 5. Quick Usage Guidance

1. Train model on [Data/Features/bank_customer_churn_train_features.csv](Data/Features/bank_customer_churn_train_features.csv).
2. Evaluate on [Data/Features/bank_customer_churn_test_features.csv](Data/Features/bank_customer_churn_test_features.csv).
3. Keep [Models/bank_customer_churn_preprocessor.joblib](Models/bank_customer_churn_preprocessor.joblib) alongside your trained model for reproducible prediction pipelines.
