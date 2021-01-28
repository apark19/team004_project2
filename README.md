# team004_project2

![](fraud.png)

## Dependencies

- xgboost</br>

- pandas</br>

- sklearn</br>

- numpy</br>

- matplotlib</br>

- imblearn</br><br>

## Installation Guides

https://pypi.org/project/imblearn/</br>

https://xgboost.readthedocs.io/en/latest/build.html</br>

https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html</br>

https://sklearn.org/install.html</br>

https://numpy.org/install/</br>

https://matplotlib.org/3.3.3/users/installing.html</br><br>

## Project Proposal: Fraud Detection in Credit Card Transactions

"Fraud detection today involves a comprehensive approach to match data points with activities to find what is abnormal and to learn from complex data patterns using sophicasted decision models to better manage false positives."<sup>1</sup>

In 2019, Credit Card Fraud was ranked as the #1 identity theft across the U.S. accounting for approximately $135 million according to the U.S. Federal Trade Commission 2019 data book.<sup>2</sup><br>

For the purposes of this project, we used different machine learning methods and a credit card transactions dataset to to predict if transactions were correctly classified as valid or fraudulent and trained different models to detect fraudulent activity.  A model was selected based on the best performance using the AUC and F-1 Score.<br>

## Dataset

**Data Source: Kaggle**<br>

A credit card transactions dataset was downloaded from the data source site, Kaggle.  The dataset includes 284,807 credit card transactions made by European cardholders over approximately 2 days in September 2013.<br>

## Data Preparation & Model Training

The dataset includes 31 features of which 28 features are PCA-decomposed and anonymized to protect customers' identities.  In addition, there is a Time feature that shows transactions recorded in Seconds and an Amount feature that shows the transactions in Euros.  A Class feature was also included in the dataset to categorize the transaction as 0 for a  Non-Fraudulent transaction or 1 for a Fraudulent transaction.<br>

The dataset is highly imbalanced with .17% of the transactions categorized as Fraudulent.<br>

The approach used to address the issue of an imbalanced dataset was to resample the training dataset using randomly selected models including a combination of sampling techniques that included SMOTE, SMOTEENN, and Cluster Centroids.<br><br>

## Model Evaluation

### Classification Models

- Balanced Random Forest<br>

- Multi-Layer Perceptron Classifier<br>

- XGBoost<br>

- Decision Tree<br>

- Logistic Regression<br>

- Isolation Forest<br><br>

Undersampling techniques randomly eliminates transactions from the non-fraudulent class to reduce the number of training samples to make the dataset balanced; however, a disadvantage of undersampling techniques is the loss of transactions. <br> 

Oversampling techniques duplicate random fraudulent transactions and replicate the training samples to balance the dataset; however, a disadvantage of oversampling techniques is overfitting the model due to the duplication of data points. <br>

The confusion matrix and imbalanced classification report were used to evaluate the overall performance for each model.  For this project, we focused on the Area Under the Curve (AUC) Receiver Operating Characteristic (ROC) and F1-Score to evaluate and select the best model(s) for detecting fraudulent activity. The closer the AUC-ROC and F1-Score are to 1.0 the better the model would be at predicting fradulent transaction on a different dataset.<br>


## Conclusion

The resampled dataset included 71,202 transactions with 111 fraudulent transactions and 71,091 non-fraudulent transactions. The MLPC model combined with SMOTE sampling yielded the highest AUC score of .9393 and the Balanced Random Forest model combined with SMOTE yielded the highest F1-Score.of .8169.  


### **MLPC/SMOTE Model**

![](/data/BRF_SMOTE.png)

### **Balanced Random Forest/SMOTE Model**

![](/data/BRF_SMOTE.png)


It is worth noting that the Cluster Centroids, an undersampling technique, performed the worst overall in correctly predicting fraudulent transactions as fraudulent as shown by the "True Positive" count and accuracy with the exception of combining Cluster Centroids with Logistic Regression which had a higher count of True Positives, a higher AUC, and a higher accuracy score when compared to other models that were combined with Cluster Centroids.

![](/data/auc_scores_final.png)
![](/data/f1_scores_final.png)
<br>


## Future Research

If more time was available with the data the group could further explore why Cluster Centroids yielded a better result for the logistic regression model compared to all other models.  In addition, other classifiers could be explored to identify if other models can better predict fraudulent activity. Further research of the current models could produce better AUC-ROC and F1-scores with the addition of different parameter configurations for the model instantiation.<br>

## References

<sup>1</sup> SAS Institute, Inc. https://www.sas.com/en_us/insights/fraud/fraud-prevention.html

<sup>2</sup> U.S. Federal Trade Commission 2019 Data Book:

https://www.ftc.gov/system/files/documents/reports/consumer-sentinel-network-data-book-2019/consumer_sentinel_network_data_book_2019.pdf)

