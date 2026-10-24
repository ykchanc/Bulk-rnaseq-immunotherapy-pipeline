# Machine Learning for Immunotherapy Response Prediction
MSc dissertation pipeline

## Overview

This repository implements a scikit-learn based machine learning pipeline for predicting anti-PD-1 immunotherapy response in melanoma patients. Based on the MSc thesis *"Identifying pre-treatment predictive biomarkers for anti-PD-1 therapy response in melanoma by machine learning"* completed at University of Birmingham under the supervision of Dr Andreas Karwath.

**Key Contribution:** We developed a feature selection and classification framework that identifies pre-treatment biomarkers associated with treatment response.

**Clinical Impact:** This work provides oncologists with a data-driven tool to identify patients most likely to benefit from anti-PD-1 therapy, enabling personalized treatment strategies.

---

## Quick Start

### Requirements
- Python 3.12+
- G4 GPU or above recommended

### Analysis Workflow

1. **Data Preprocessing**
    - Align the data in TPM, gene filtering, batch-effect correction
      - 01_data_preprocessing_and_batch_correction.py
2. **Feature selection and model training with whole transcriptome as input**
    - Using boruta for feature selection and logistic regression for classification.
      - 02_allgenes_boruta_standardscaler_logistic_regression.py
      - 03_allgenes_boruta_powertransformer_logistic_regression.py
3. **Feature selection and model training with GSVA features as input**
    - Using GSVA to generate pathway activity matrix first, then the pathways were used as input features for model training. Optuna was used for hyperparameter tuning. XGBoost (xgb) and Recursive Feature Elimination (rfe) were used for feature selection. XGBoost, Logistic Regression (logreg) and Support Vector Classifier (svc) were used for model training.
      - 04_gsva_xgb_withoptuna_survival.py
      - 05_gsva_rfe_logreg_withoptuna_survival.py
      - 06_gsva_rfe_svc_withoptuna_survival.py
4. **Feature selection and model training with xCell features as input**
    - Using xCell for cell deconvolution to generate immune/stromal cells proportions first, then the matrix was used as input for model training. Optuna was used for hyperparameter tuning. XGBoost (xgb) and LASSO were used for feature selection. XGBoost, Logistic Regression (logreg) and Support Vector Classifier (svc) were used for model training.
       - 07_xcell_lasso_svc_withoptuna_survival.py
       - 08_xcell_lasso_logisticregression_withoptuna_survival.py
       - 09_xcell_xgboost_withoptuna_survival.py

---

## Workflow Chart
<img width="1081" height="657" alt="Screenshot 2026-10-24 at 1 41 22 PM" src="https://github.com/user-attachments/assets/317f5443-fcd0-4e57-9cd4-cc77cf0a69a4" />
