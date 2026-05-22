# When Machine Learning Fails  
## Diagnosing and Repairing Failure Modes in a Non-Linear Model

Mini-project realized at **Ecole Centrale Casablanca** for the course **Introduction to AI & Machine Learning**.

## Project Overview

This project investigates a common Machine Learning failure mode:  
a model achieving high global accuracy while completely failing on the minority class.

Using the **Online Shoppers Purchasing Intention Dataset**, we study how a baseline **Random Forest** behaves under strong class imbalance and evaluate correction strategies to improve minority-class detection.

The project focuses on:

- Failure diagnosis
- Class imbalance analysis
- Model evaluation beyond accuracy
- Recall optimization for business-critical classes
- Controlled experimentation and validation

---

## Research Question

Can a baseline Random Forest trained without imbalance correction achieve high overall accuracy while producing near-zero recall on the minority class, and can class weighting significantly improve recall without substantially degrading macro-F1?

---

## Dataset

### Online Shoppers Purchasing Intention Dataset
Source: UCI Machine Learning Repository

The dataset contains:
- **12,330 e-commerce sessions**
- **17 features**
- Binary target variable:
  - `True` → purchase completed
  - `False` → no purchase

### Dataset Characteristics

| Property | Value |
|---|---|
| Total sessions | 12,330 |
| Buyers | 1,908 (15.5%) |
| Non-buyers | 10,422 (84.5%) |
| Imbalance ratio | 5.5 : 1 |
| Missing values | 0 |

---

## Features

The dataset includes:

### Behavioral Features
- Administrative pages visited
- Informational pages visited
- Product pages visited
- Bounce rates
- Exit rates
- Page values

### Temporal Features
- Month
- Weekend indicator
- Special day proximity

### Technical Features
- Browser
- Operating system
- Region
- Traffic type
- Visitor type

---

## Baseline Model

The reference model is a **Random Forest Classifier** trained without any imbalance correction.

### Hyperparameters

| Parameter | Value |
|---|---|
| n_estimators | 100 |
| class_weight | None |
| random_state | 42 |
| train/test split | 80/20 stratified |

---

## Main Failure Observed

The model reaches approximately:

- **85% accuracy**
- **~0.2% recall on buyers**
- **ROC-AUC ≈ 0.58**

This demonstrates that:
- Accuracy alone is misleading
- The model predicts almost exclusively the majority class
- Minority-class detection completely collapses

---

## Objectives

- Diagnose the root cause of the failure mode
- Study the impact of class imbalance
- Improve minority-class recall
- Compare baseline and corrected models
- Analyze temporal drift effects

---

## Project Structure

```bash
project/
│
├── README.md
├── requirements.txt
└── when_ml_fails.ipynb
