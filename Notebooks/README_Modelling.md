# Notebook 02: EDA and Modelling
**Bank Customer Churn Analysis - Analytics in Practise**
**Role: Modelers / Analysts | Slides 4 & 6**

---

## What This Notebook Does

This notebook covers the full analytical layer of the project, from exploring the data to building and evaluating three predictive models.

---

## What's Inside

### Part 1 - EDA
| Section | What It Covers |
|---------|---------------|
| 1.1 | Dataset overview: shape, types, missing values |
| 1.2 | Churn vs retained class distribution |
| 1.3 | Churn by country: the Germany anomaly (32.4%) |
| 1.4 | The product paradox: 3 products = 82.7% churn, 4 products = 100% |
| 1.5 | Age distribution: the 40+ effect |
| 1.6 | High-value segment at risk (age 40-60, balance >€100k) |
| 1.7 | Gender analysis across countries: German women at 37.6% |
| 1.8 | Activity and segment analysis |
| 1.9 | Correlation heatmap |
| 1.10 | Full EDA summary table |

### Part 2 - Modelling
| Section | What It Covers |
|---------|---------------|
| 2.1 | Train/test split setup |
| 2.2 | Three models trained: Logistic Regression, Random Forest, XGBoost |
| 2.3 | Model comparison chart |
| 2.4 | ROC curves |
| 2.5 | Feature importance: Random Forest |
| 2.6 | Feature importance: XGBoost |
| 2.7 | Confusion matrices |
| 2.8 | Classification reports |

### Part 3 - Conclusions
- Business insights written in plain English
- Model recommendation with justification

---

## Model Results

| Model | Accuracy | F1 Score | ROC-AUC |
|-------|----------|----------|---------|
| Logistic Regression | 80.8% | 0.28 | 0.775 |
| Random Forest | 86.3% | 0.58 | **0.851** |
| XGBoost | 84.9% | 0.56 | 0.833 |

**Best model: Random Forest (AUC 0.851)**

---

## Charts Generated (saved to Images/)

| File | What It Shows |
|------|--------------|
| chart1_churn_overview.png | Donut: overall churn split |
| chart2_churn_by_country.png | Germany vs France vs Spain |
| chart3_product_paradox.png | Churn rate by number of products |
| chart4_age_distribution.png | Age KDE: churned vs retained |
| chart5_high_value_scatter.png | Age vs balance scatter coloured by churn |
| chart6_gender_country.png | Gender churn across all 3 countries |
| chart7_segment_analysis.png | Active vs inactive + death zone |
| chart8_correlation_heatmap.png | Feature correlation matrix |
| chart9_model_comparison.png | Accuracy, F1, AUC for all 3 models |
| chart10_roc_curves.png | ROC curves for all 3 models |
| chart11_feature_importance_rf.png | Top features: Random Forest |
| chart12_feature_importance_xgb.png | Top features: XGBoost |
| chart13_confusion_matrices.png | Confusion matrices for all 3 models |

---

*Analytics in Practise | Trinity College Dublin | April 2026*
