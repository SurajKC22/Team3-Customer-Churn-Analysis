# Customer Churn Analysis – Churn Prediction Using an ANN

**ACS Work Integrated Learning – Data Analytics | Team 3**  
**Prepared by:** Zannatul Ferdous (Annie)  
**Role:** Data Analyst – Predictive Modelling

## Objective
Predict which customers are likely to churn using an Artificial Neural Network (ANN), compare it with a simple baseline model, and identify the main drivers of churn.

## Data
- Team-approved processed dataset Version 2 (`Data_Preparation/Final_Files_Both_version/*_v2.csv`)
- 6,741 customers after removing 302 duplicates; 5,392 training / 1,349 test (stratified 80/20 split)
- 10 encoded and scaled features; churn rate about 26.5% in both sets

## Method
1. Load the v2 training and test files in Google Colab.
2. Set aside 20% of the training data as a validation set for decisions (no peeking at the test set).
3. Benchmark: a model that always predicts "No churn".
4. Baseline: logistic regression (`class_weight="balanced"`).
5. ANN: scikit-learn `MLPClassifier` with two hidden layers (16 and 8 neurons, ReLU), trained with early stopping on validation loss.
6. Choose each model's decision cut-off on the validation set to maximise F1.
7. Evaluate on the test set: accuracy, precision, recall, F1, ROC-AUC, confusion matrix, ROC curve.
8. Permutation importance to show which features the ANN relies on.
9. Export the ANN's test-set predictions and result charts.

## Results (test set)
| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|
| Always "No" (benchmark) | 0.735 | 0.000 | 0.000 | 0.000 | 0.500 |
| Logistic Regression | 0.719 | 0.482 | 0.799 | 0.601 | 0.817 |
| ANN | 0.742 | 0.510 | 0.749 | 0.606 | 0.810 |

- The ANN caught 268 of 358 churners (75%), missed 90, and raised 258 false alarms.
- The ANN and logistic regression performed almost the same, suggesting a simple model captures most of the churn patterns with only 10 features.
- Tenure and monthly charges are the strongest drivers of churn. New customers (0–12 months) churned at 48%, compared with 9.6% for customers of more than 4 years.

## Limitations
- Only 10 features describe each customer.
- Some customers have identical details but different churn outcomes, so no model can predict them all correctly.
- ANNs are harder to explain than simpler models; permutation importance gives only a partial explanation.
- The chosen cut-off balances catching churners against false alarms; the business may prefer a different balance.

## Files
- `ANN_Churn_Model.ipynb`: full notebook with code, charts and interpretations
- `ANN_Churn_Predictions.csv`: ANN churn probability and prediction for each test customer
- `ann_learning_curve.png`, `ann_confusion_matrix.png`, `roc_curve.png`, `ann_feature_importance.png`: result charts
