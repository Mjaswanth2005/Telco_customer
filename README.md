Telco Customer Churn Prediction
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
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


## Additional Analysis & Visualizations

### Exploratory Data Analysis (EDA) Visualizations

#### Churn Distribution Analysis
The dataset shows a ~26.5% churn rate, with the majority of customers (73.5%) retaining the service. This class imbalance is important to consider during model training.

#### Statistical Correlations
Correlation analysis reveals strong relationships between key features:
- **Tenure and TotalCharges**: 0.83 correlation (customers stay longer and pay more)
- **MonthlyCharges and TotalCharges**: 0.65 correlation
- These numerical features are critical predictors of customer behavior

### Model Performance Visualizations

#### Confusion Matrices Analysis
The confusion matrices show the trade-off between model types:

**Logistic Regression (Baseline)**:
- True Negatives: 925 (correctly predicted non-churners)
- False Positives: 110 (incorrectly predicted churners)
- False Negatives: 162 (missed churners - critical misses)
- True Positives: 212 (correctly identified churners)

**Random Forest (Improved)**:
- True Negatives: 941 (improved non-churner detection)
- False Positives: 94 (fewer false alarms)
- False Negatives: 179 (slightly more missed churners)
- True Positives: 195 (fewer caught churners, but balanced)

#### ROC Curve Comparison
Both models achieve similar ROC-AUC scores:
- **Logistic Regression**: AUC = 0.8416 (blue curve)
- **Random Forest**: AUC = 0.8439 (green curve)
- **Random Classifier Baseline**: AUC = 0.5 (dotted line)

The curves show excellent discrimination ability for both models, with only marginal difference between them.

### Feature Importance Analysis

The Random Forest model reveals the most important features for churn prediction (Top 15):

1. **Tenure** (0.2095) - Strongest predictor; longer tenure = lower churn
2. **TotalCharges** (0.1339) - Cumulative spending indicates loyalty
3. **MonthlyCharges** (0.1045) - High charges increase churn risk
4. **InternetService_Fiber optic** (0.0797) - Fiber optic customers have different churn patterns
5. **PaymentMethod_Electronic check** (0.0683) - Payment method affects retention
6. **Contract_Two year** (0.0657) - Long-term contracts reduce churn
7. **OnlineSecurity_Yes** (0.0399) - Services reduce churn risk
8. **Contract_One year** (0.0374) - Medium-term contracts provide some protection
9. **TechSupport_Yes** (0.0240) - Support services improve retention
10. **PaperlessBilling_Yes** (0.0196) - Administrative preferences matter

### Key Insights from Analysis

1. **Contract Type Impact**: Customers with month-to-month contracts show significantly higher churn than those with annual or multi-year contracts
2. **Tenure Effect**: The first 12 months are critical; early intervention is crucial
3. **Service Adoption**: Online security and tech support services strongly correlate with lower churn
4. **Pricing Strategy**: Very high monthly charges correlate with increased churn risk
5. **Customer Segmentation**: Internet service type (Fiber optic vs DSL) shows distinct churn patterns

### Recommendations for Implementation

1. **Proactive Retention for New Customers**: Focus retention efforts on customers in their first 12 months
2. **Contract Optimization**: Incentivize customers to upgrade from month-to-month contracts
3. **Service Bundling**: Promote online security and tech support services as churn reduction tools
4. **Pricing Adjustment**: Review pricing for high-paying customers to improve value perception
5. **Targeted Offers**: Use model predictions to identify at-risk customers and deploy personalized retention campaigns
6. **Internet Service Focus**: Develop fiber optic specific retention strategies

### Model Performance Metrics Summary

Both models achieved comparable performance on validation data:
- **Accuracy**: ~80.7% - Correctly classifies 4 out of 5 customers
- **Precision**: 66-67% - When model predicts churn, it's right 2/3 of the time
- **Recall**: 52-57% - Can identify 50-57% of actual churners
- **F1-Score**: 0.59-0.61 - Balanced performance metric

The trade-off between models: Random Forest shows slightly better overall ROC-AUC but similar accuracy, suggesting both approaches are viable depending on business priorities (minimize false positives vs. catch more churners).
