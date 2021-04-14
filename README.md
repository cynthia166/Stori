# Credit Fraud Prediction Model

## Data Preparation

Firstly, I cleaned the data. I found a maximum of 321 null values in one column. Secondly, I decided to drop the null values in the columns activated_date, last_payment_date and cash in advance because they had few null values. 

 The column balance had only two null values and minimum_payments had the max  number of null values. In this case , I filled the null values with the mean of each column. 


## Exploring the Data

I examined the structure of the Credit card data set and the data types. Then, I used  descriptive statistics  to have an idea of how  analyzed the data. I used boxplot graphs to observe the outliers. I notice that most of the max values of each column are far away from de mean this indicates that there were many outliers. Specially the following columns:  purchase, oneoff_purchases, cash advance, minimun_payments and payments. The balance column had the maximum outliers in 2020. A reason could be that balance column had data of the last 3 months of 2019 and 7 months from 2020.

I obtained a heatmap to identify the variable that had high correlation and not used them.

## Model 1

#### Logistic Regression
The model that I used was the Logistic regression model although I also considered an ensemble model, which considered three models: logistic regression, random forest and naive bayes.
I obtained the variables ordered by significance with Recursive Feature elimination (RFE) and the three most important explicative variables were; cash_advance_frequency, minimum_payments',  and cash_advance'.

### Assumptions

The most important variables according to RFE and those that were not correlated were: 'prc_full_payment',"cash_advance",'payments','installments_purchases','balance_frequency','purchases'and'cash_advance_frequency.
In addition, we tested the model with one variable and added a variable at a time and if the model did not performed better we did not consider it.

I used Variance Inflation Factor (VIF) to check multicollinearity and it was not an issue, the results were low and did not exceed a VIF of 3. 
Durbin-Watson was used to validate the independence of error.

### Validation

I validate the model with a classification report, both classes have the same precision, but class 0 has more recall than class 1. It is a good model because has a f1-score of 0.9%. The pseudo square was 0.81. The confusion matrix had no false positives but there are 3 false negatives and 16 true positives. And the area under the curve was 0.9583.

## Model 2

#### Ensemble methods

The Ensemble methods use the predicted class labels and takes the majority vote, the model considered the following: LogisticRegression, RandomForestClassifier and Bayes Naive. I chose the hard voting class. The predicted class is the class with the highest majority of votes.

## Other Intent Methods

I test other methods to obtain a better performance without success; I used the Extreme Gradient boosting of data undersampled. It  applies better regularization techniques to reduce overfitting. 

## Conclusions
The Ensemble model is the best because it does not only rely in one model to have
a better performance it used three models; the classification report, the f1.score and pseudo score, they performed the same as  logistic regression . 



