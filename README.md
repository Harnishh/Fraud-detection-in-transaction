#  IEEE-CIS Fraud Detection using Machine Learning

##  Project Overview
This project focuses on detecting fraudulent online transactions using the **IEEE-CIS Fraud Detection dataset**.  
A complete end-to-end machine learning pipeline was built, addressing challenges such as **class imbalance**, **high-dimensional data**, and **time-based data leakage**.

The project was developed for a **university-level machine learning competition**.

---

##  Problem Statement
Online transaction fraud is rare but highly impactful.  
The dataset is **severely imbalanced** (~3.5% fraud), making accuracy alone unreliable.

**Objective:** Detect fraudulent transactions while minimizing missed fraud cases and controlling false positives.

---

##  Dataset
- **Dataset:** IEEE-CIS Fraud Detection (Kaggle)
- **Files:** `train_transaction.csv`, `train_identity.csv`
- **Target:** `isFraud`

>  Dataset files are not included due to GitHub size limits.

---

##  Methodology

###  Preprocessing
- Merged transaction and identity data using `TransactionID`
- Dropped extremely sparse features
- Encoded categorical variables numerically
- Applied **time-based train–validation split** to prevent leakage

###  Model
- **LightGBM (Gradient Boosting Trees)**
- Chosen for efficiency, scalability, and strong performance on tabular data
- Feature importance used for interpretability

###  Class Imbalance
- Trained baseline and class-weighted models (`scale_pos_weight`)
- Final model selected based on validation performance and metric trade-offs

---

##  Evaluation

### Metrics
- ROC-AUC
- Accuracy (for reference)
- Precision
- Recall
- Confusion Matrix
- Threshold tuning for recall improvement

### Final Validation Results
| Metric | Value |
|------|------|
| Accuracy | ~97.5% |
| Precision | ~64.4% |
| Recall | ~46.4% |

> Recall is emphasized due to the high cost of missed fraud cases.

---

##  Feature Importance
The model relied primarily on:
- Anonymized engineered features (`V*`)
- Count-based behavioral features (`C*`)
- Time-based features (`TransactionDT`, `D*`)
- Card and identity attributes

---

##  Threshold Tuning
- Default threshold (0.5) was suboptimal
- Lower thresholds were evaluated to improve recall
- A balanced threshold was chosen to trade precision for higher fraud detection

---


---

##  How to Run
1. Download the dataset from Kaggle
2. Place CSV files locally (not tracked by Git)
3. Run `creating_base_line_model.ipynb` step by step

---

##  Key Learnings
- Accuracy is misleading for imbalanced data
- Recall is critical in fraud detection
- Time-based splitting prevents data leakage
- Threshold tuning significantly affects results

---

##  Future Work
- Advanced feature engineering
- Hyperparameter tuning
- Cost-sensitive evaluation
- Model deployment and monitoring

---

##  References
- Kaggle IEEE-CIS Fraud Detection
- LightGBM & Scikit-learn documentation
