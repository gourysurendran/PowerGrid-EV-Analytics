# PowerGrid EV Analytics Internship

This repository contains my work for the **PowerGrid EV Analytics Programme**, covering data analytics, machine learning, business intelligence, and predictive modelling tasks.

## Module 1: Telco Customer Churn Prediction & Decision Modeling

### Objective
Predict customers who are likely to churn, identify major churn drivers, and determine an appropriate intervention threshold for customer retention campaigns.

### Tasks Completed

1. **Load & Inspect**
   - Loaded the Telco Customer Churn dataset.
   - Converted `TotalCharges` to numeric format.
   - Imputed missing `TotalCharges` values.

2. **Exploratory Data Analysis**
   - Analyzed churn by contract type.
   - Analyzed churn across tenure groups.
   - Analyzed churn across monthly charge ranges.

3. **Preprocessing & Feature Encoding**
   - Encoded categorical variables using one-hot encoding.
   - Scaled numerical variables.
   - Prepared the dataset for machine learning.

4. **Machine Learning Model Training**
   - Trained Logistic Regression.
   - Trained Random Forest.
   - Compared model accuracy, precision, recall, F1-score, and confusion matrices.

5. **Business Decision Threshold Modeling**
   - Evaluated multiple classification thresholds.
   - Analyzed the precision-recall trade-off.
   - Selected a threshold based on the highest F1-score.

### Key Results

| Model | Accuracy |
|---|---:|
| Logistic Regression | 80.41% |
| Random Forest | 78.64% |

The Logistic Regression model achieved the better accuracy and churn-class F1-score among the two models.

### Decision Threshold

The selected threshold was **0.40**, achieving:

- **Precision:** 0.591
- **Recall:** 0.676
- **F1-score:** 0.631

This threshold provides a balance between identifying potential churners and limiting unnecessary retention interventions.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Jupyter Notebook
- GitHub

## Repository Structure

```text
PowerGrid-EV-Analytics/
│
├── Module_1_Telco_Customer_Churn.ipynb
└── README.md
