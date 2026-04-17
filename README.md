# Machine Learning for Predicting Abnormal CMP Results

## Overview
This project applies machine learning techniques to predict abnormal **Comprehensive Metabolic Panel (CMP)** laboratory results using clinical data from the **MIMIC-IV dataset**. The goal is to identify patterns in patient data that can help anticipate abnormal lab values and support clinical decision-making.

---

## Problem Statement
CMP tests are widely used to evaluate kidney function, liver function, and metabolic status. Abnormal results often drive important clinical decisions. However, predicting these abnormalities is challenging due to:

- Noisy and heterogeneous clinical data.
- Strong class imbalance (abnormal >> normal).
- Complex, nonlinear relationships between variables.

This project explores how machine learning models can address these challenges and improve prediction performance.

---

## Dataset
- **Source:** MIMIC-IV (PhysioNet)  
- **Description:** A large, publicly available dataset containing de-identified ICU patient records  

### Data Used:
- Laboratory events (CMP components)
- Patient demographics
- Admissions data
- Vital signs (blood pressure, BMI)
- Diagnosis codes (ICD)

> Note: Due to data size restrictions, the dataset is not included in this repository.  
> Access MIMIC-IV here: https://physionet.org/content/mimiciv/

---

## Feature Engineering
A major focus of this project was constructing meaningful features from raw clinical data.

### Features Included:
- **Prior lab values** (previous CMP measurements)
- **Delta features** (change between consecutive tests)
- **Time-based features** (hours since last CMP)
- **Diagnosis indicators** (ICD group encoding)
- **Vital signs** (blood pressure, BMI)

---

## Models Evaluated

### 1. Logistic Regression (Baseline)
- Linear model.
- Provides interpretability.
- Limited ability to capture nonlinear relationships.

### 2. Random Forest (Primary Model)
- Ensemble tree-based model.
- Captures nonlinear interactions.
- Robust to noisy clinical data.

## Results

### Model Performance Comparison

| Model                | AUROC |
|---------------------|------|
| Logistic Regression | 0.76 |
| Random Forest       | **0.91** |

### Final Random Forest Metrics

- **AUROC:** 0.9109 
- **Sensitivity:** 0.8387
- **Specificity:** 0.8051  
- **PPV:** 0.9720  
- **NPV:** 0.3823  

### Key Findings
- Nonlinear models significantly outperform linear models.
- Feature engineering (especially severity features) greatly improves performance.
- Temporal patterns in lab values are highly predictive.

## How to Run the Project
1.) Run pre_process_mimic_data.ipynb

2.) Run train_logistic_regression_model.ipynb **and/or** train_random_forests_model.ipynb in no particular order. 

## Presentation

A recorded presentation of this project is available here:

[Video presentation on Youtube](https://youtu.be/orP8kUsl74U)

## Literature Review

This project builds on prior work in clinical machine learning:

- Ayad et al. (2022): Deep learning for ICU lab prediction.
- Luo et al. (2016): Early ML approaches for lab prediction.
- Schober & Vetter (2021): Logistic regression in medical research.

## Limitations
- Class imbalance affects NPV performance.
- Lab reference ranges are generalized.
- Temporal relationships could be modeled more explicitly.

## Future Work
- Implement more temporal features.
- Reduce complexity by consolidating ICD codes.
- Improve severity modeling and clinical thresholds.
- Explore other model architectures.
