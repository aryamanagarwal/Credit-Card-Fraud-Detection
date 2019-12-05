# Credit-Card-Fraud-Detection
Credit card fraud detection using Isolation Forest and Local Outlier Factor.

###Dataset
The datasets contains transactions made by credit cards in September 2013 by european cardholders. This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions.

It contains only numerical input variables which are the result of a PCA transformation. Unfortunately, due to confidentiality issues, we cannot provide the original features and more background information about the data. Features V1, V2, ... V28 are the principal components obtained with PCA, the only features which have not been transformed with PCA are 'Time' and 'Amount'. Feature 'Time' contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature 'Amount' is the transaction Amount, this feature can be used for example-dependant cost-senstive learning. Feature 'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise.

The dataset could not be uploaded as the size exceeds the maximum allowed size, the link for the dataset : https://www.kaggle.com/mlg-ulb/creditcardfraud

###Flow
After importing the dataset we divide the dataframe into x and y. x containing the 30 attributes taken into consideration and y containg the Class value. We have used only 1/10 fraction of the dataset as training on 284,807 was not computaionally feasible.

After this we fit and predict on the data. The results obtained are as follows : 
```
Isolation Forest 
No. of error :  71
Accuracy :  0.99750711000316
              precision    recall  f1-score   support

           0       1.00      1.00      1.00     28429
           1       0.32      0.33      0.32        52

    accuracy                           1.00     28481
   macro avg       0.66      0.66      0.66     28481
weighted avg       1.00      1.00      1.00     28481
```
The precision value of 0.32 tells us that out of the total fraud predictions made only 32% were true.

```
Local Outlier 
No. of error :  105
Accuracy :  0.9963133316948141
              precision    recall  f1-score   support

           0       1.00      1.00      1.00     28429
           1       0.00      0.00      0.00        52

    accuracy                           1.00     28481
   macro avg       0.50      0.50      0.50     28481
weighted avg       1.00      1.00      1.00     28481
```
Local outlier failed miserably as it was not able to predict even a single fraud transaction.

Despite the fact that our Isolation Forest model classified some valid transactions as fraud, but it was sucessfull in predicting all the fraudulent transactions.
