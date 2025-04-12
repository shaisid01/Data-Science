# Customer-Attrition-Prediction

Capstone Project
Data Science Career Track, Springboard
Thanks to mentor Julian Jenkins III
<br />Build a predictive analysis on the credit card dataset to understand whether the customer churn or not, and identify the reasons for them to leave.

<br />I have used a credit card datset.Credit cards are a good source of income for banks because of different kinds of fees charged by the banks like annual fees,balance transfer fees, and cash advance fees, late payment fees, foreign transaction fees, and others. Some fees are charged to every user irrespective of usage, while others are charged under specified circumstances.
#### Objectives:
<br />●Explore the dataset and visualize the same
<br />●Build a model to predict the customer is going to churn or not
<br />●Optimize the 3 models with appropriate techniques
<br />●Generate a set of insights and recommendations that may help the bank
#### Data Source
From google data search
https://www.kaggle.com/c/1056lab-credit-card-customer-churn-prediction/data
#### Data Wrangling
There are 10127 rows and 23 columns. Here are the steps performed to clean and oraganize
the data.
<br />● Checked for missing values
<br />● Checked for Null
<br />● Checked for missing values
<br />● Checked for unique values
<br />● Weird values or filled, for example “unknown”
<br />● Corrected weirdly formatted values(income category)
<br />● From the initial look on data, found below information.
#### <b>My target variable is :Attrition_Flag: if the account is closed then "Attrited Customer" else "Existing Customer"</b>
#### Feature Scaling and Distribution:
4 different types scaling is applied -
<br />1. z-score scaling : Approximately normally distributed
<br />2. Divided by Median: related by magnitude or right skewed
<br />3. Log scaling:related by magnitude
<br />4. Square root : for counts
<br />![image](https://user-images.githubusercontent.com/87315447/160265343-4e7becfa-7992-40d7-89f3-d5b52837e66f.png)
#### Exploratory Data Analysis
At this Exploratory Data analysis step feature relationship is evaluated.The features that are likely to have the most impact in modeling based on relationships between the features and the response variable are identified. SCaled features are compared with original features with help of hist plot. Pearson correlation coefficients were used to identify statistical relationship strengths. 
<br />Scaling is visualized with distribution plot one sample is below -
![image](https://user-images.githubusercontent.com/87315447/160265382-e5115c84-5f8c-41ec-8739-b0a8658b808d.png)
#### Pre-Processing
In the Pre-processing I applied the scaling best found from the EDA as follows
<br />● Z scoring for "Customer_Age","Months_on_book"
<br />● Div median for 'Total_Revolving_Bal'
<br />● Log scaling for "Credit_Limit","Total_Trans_Amt"
<br />● Test and Train sets are created with 80:20 ratio.
<br />● One hot encoding is applied
#### Modeling
Steps followed to build model are -
1. Set the model object, Pipeline, cross-validator, etc.
<br />2. Evaluate the fit on the training data (make sure everything is working,
<br />3. is the metric acceptable?)
<br />4. Pick the threshold (using the training data)
<br />5. Evaluate on the test data
<br />6. Make sure to compare train and test results (generally perform worse on test)
#### Model used are
<br />1. Logistic Regression
<br />2. Random Forest Classification
<br />3. XGBoost Classification
#### Evaluation Metrics
This project aims to predict potential churn customers, and it is realized that the client cost of mistakenly classifying non-churn customers as churn may be high in practice because banks would not want to lose valuable customers, and the banks would like to identify churners at their best efforts as well. Thus, it would be useful to consider Recall. To complement this Receiver Operating Characteristic curve (ROC) is used. ROC is a plot of True Positive Rate (TPR) against False Positive Rate (FPR). This means I can consider TPR and FPR simultaneously, by making use of the area under the curve (AUC) of ROC. 
<br />TPR or Recall or Sensitivity tells us what proportion of the positive class got correctly classified. TPR = TP/(TP+FN)
<br />FPR tells us what proportion of the negative class got incorrectly classified by the classifier. FPR = FP/(TN+FP)
<br />All models are used to predict the actual class of the data point by predicting its probability of belonging to different classes. This gives us more control over the result.And ROC_AUC threshold is used to interpret the result of the classifier.
#### Steps followed to build model are
<br />1. Set the model object, Pipeline, cross-validator, etc.
<br />2. Evaluate the fit on the training data (make sure everything is working,
<br />3. is the metric acceptable?)
<br />4. Pick the threshold (using the training data)
<br />5. Evaluate on the test data
<br />6. compare results
#### Random Forest with Grid SearchCV: Metrics Evaluation
![image](https://github.com/user-attachments/assets/864247e4-b2d7-4c3e-b968-20e2fa4ae235)
![image](https://github.com/user-attachments/assets/1be2a121-2825-4b43-af49-af4bd1b4073f)

#### XGBoost with GridSerachCV Classification: Metric Evaluation
![image](https://github.com/user-attachments/assets/e44f592d-0529-438f-9ae1-0ee755674912)
![image](https://github.com/user-attachments/assets/c2786b3b-1f1e-4fc8-870b-e78a41024d13)

#### Metrics Comparison
![image](https://github.com/user-attachments/assets/7ba2ec0c-3aad-4dab-ba6e-839552877ca4)

#### Best Performing Models:

XGBoost: The model shows high performance on both the training and test datasets, with precision and recall above 0.95 for both classes. It provides a balanced approach with high F1-scores.

Random Forest: Also provides very good performance with precision and recall both equal to 1.0 on the training set. It performs well on the test set, but slightly lower than XGBoost.

#### Conclusion:

For best overall performance, XGBoost seems to be the most balanced model with high precision, recall, and F1-score across both train and test sets.

For class imbalance, Logistic Regression with Threshold Adjustment or Logistic Regression SMOTE may help, but models like Random Forest and XGBoost generally outperform these in terms of overall performance.

#### Improvements

PCA is lowering the performance, so feature selection techniques like Recursive Feature Elimination (RFE) or Lasso Regression to identify the most important features can be tried.

Hyperparameter Tuning: Grid Search or Randomized Search can be used to find the optimal hyperparameters for the models. For models like Random Forest, XGBoost, or Logistic Regression, tweaking parameters such as max_depth, learning_rate, n_estimators, and others can improve performance

Cross-validation helps to ensure that the model is not overfitting to the training data and generalizes well to unseen data. Use k-fold cross-validation to get a better estimate of the model's performance.

Ensemble methods like Voting Classifier, Stacking, or Boosting (e.g., ADABoost) combine multiple models to improve the overall prediction. Sometimes, combining models like Logistic Regression and Random Forest into a voting classifier can improve results.
