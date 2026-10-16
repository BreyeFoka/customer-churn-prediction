# Customer churn prediction

[Open in Colab](https://colab.research.google.com/github/BreyeFoka/customer-churn-prediction/blob/main/Customer_Churn_Prediction.ipynb)

Predicts which telecom customers are likely to leave, using the IBM Telco Customer Churn dataset (about 7,000 customers with their contract, services, charges and whether they churned).

## What the notebook does

1. Explores the data: churn rate, and how tenure, contract type and monthly charges relate to churn
2. Cleans and encodes the features, then splits into training and test sets
3. Trains and compares several models, then tunes the strongest ones
4. Saves the chosen model with joblib

## Results (test set)

| Model | Accuracy | Precision | Recall | F1 |
| --- | --- | --- | --- | --- |
| Logistic regression | 0.814 | 0.691 | 0.570 | 0.625 |
| Logistic regression, tuned | **0.815** | 0.690 | 0.577 | 0.628 |
| Random forest | 0.791 | 0.663 | 0.472 | 0.551 |
| Gradient boosting | 0.804 | 0.674 | 0.540 | 0.600 |
| LightGBM, tuned | 0.760 | 0.538 | **0.821** | **0.650** |

Tuned logistic regression has the best accuracy. Tuned LightGBM catches far more of the customers who actually leave (82% recall) at the cost of more false alarms, so it's the better choice if missing a churner costs more than contacting a loyal customer.

## Run it

Open the notebook in Colab, or run it locally with pandas, scikit-learn, LightGBM, matplotlib and seaborn. Download `WA_Fn-UseC_-Telco-Customer-Churn.csv` from [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) and update the path in the first cells.

## Checks

GitHub Actions checks that the notebook is valid and every code cell compiles. It doesn't re-run the training, which needs the dataset.
