Telco Customer Churn Prediction

Overview
This project builds and evaluates machine learning models to predict customer churn in a telecom dataset. The objective is to identify customers likely to leave the service so that proactive retention strategies can be implemented.

The workflow includes:
Data cleaning and preprocessing
Feature encoding and scaling
Model training


Evaluation and comparison
Two models are implemented:
Logistic Regression (baseline)
Random Forest Classifier (improved model)


Dataset
The dataset contains telecom customer records including demographics, billing information, and service usage. The target variable is:
Churn → Whether a customer leaves the service.


Train / Validation Split Method
The dataset is divided into training and validation sets using an 80/20 stratified split.
80% → Training data
20% → Validation data


Stratified sampling ensures that the proportion of churn vs non-churn customers remains consistent across both sets.

Implementation concept:
Random seed fixed for reproducibility
Stratification applied to preserve class balance

This split allows reliable performance evaluation while maximizing training data.


Model Training:

Logistic Regression (Baseline):

<img width="734" height="590" alt="image" src="https://github.com/user-attachments/assets/df69f016-c2b2-4119-bfaa-50f37353149d" />

Numerical features scaled
Provides a linear reference model



Random Forest (Improved Model):

<img width="734" height="590" alt="image" src="https://github.com/user-attachments/assets/50607778-346a-42ed-8e36-4b9576c613d4" />

Ensemble tree-based model
Handles nonlinear feature interactions
Tuned hyperparameters for improved generalization


Evaluation Metrics:
Model performance is evaluated using multiple classification metrics to capture different aspects of prediction quality:
Accuracy — overall correctness

Precision — correctness of churn predictions

Recall — ability to detect churn cases

F1 Score — balance between precision and recall
ROC-AUC — ranking quality of predictions
Confusion Matrix — class-wise prediction breakdown
Using multiple metrics ensures balanced evaluation beyond simple accuracy.

Results:
Logistic Regression (Baseline)
Accuracy: ~0.80
F1 Score: ~0.61
ROC-AUC: ~0.84

Random Forest (Improved Model)
Accuracy: ~0.83
F1 Score: ~0.67
ROC-AUC: ~0.86

Best Result:
The Random Forest model achieved the best overall performance.

Key improvements:
Higher prediction accuracy
Better churn detection (recall)
Stronger F1 score balance
Improved ROC-AUC
This indicates that the ensemble model captures complex patterns in customer behavior more effectively than the baseline linear model.

Conclusion:
This project demonstrates a complete machine learning pipeline:
Structured preprocessing
Model comparison
Robust evaluation

The Random Forest model provides the strongest predictive performance and serves as the recommended approach for churn prediction in this dataset.
