# Credit Fraud Prediction Model

## Data Preparation

The first step was cleaning the data, there were not many null values the maximum null values per column were 321, I decided to drop the null values in the columns activated_date, last_payment_date and cash in advance, the main reason was they did no have a large amount of null values. In the case of column balance had only 2 null values and minimum_payments had the max number of null values and I decided to fill the mean of each column.

## Exploring the Data

First I learned about the structure of the Credit card data set, the data types,  descriptive statistics,  to have an idea of how we were going to treat our data. We can appreciate that most max values of each column are far away from de mean this indicates that there are a lot of outliers. Specially the following columns  purchase, oneoff_purchases, cash advance, minimun_payments and payments. We also used boxplot to observe the outliers. The outlier of the balance column, there are more outliers in 2020. A reason could be that we only have data of the last 3 months of 2019 and 7 months from 2020.

I obtained a heatmap to identify the variable that had high correlation to not repeat two variables that were highly correlated.

## Model 1

#### Logistic Regression
The model that I used was the Logistic regression model although I also considered an ensemble model which considered 3 models that were, logistic regression, Random Forest and Naive Bayes.
I obtained the variables ordered by significance with Recursive Feature elimination (RFE) and the 3 most important explicative variables  were cash_advance_frequency, minimum_payments',  and cash_advance'.

### Assumptions

We chose the following variables which are the most important according to RFE also we consider those that were not correlated which are the following, 'prc_full_payment',"cash_advance",'payments','installments_purchases','balance_frequency','purchases'and'cash_advance_frequency.
Also we tested the model with one variable and added a variable at a time and if the model did not perform better we did not consider it.

To check  that multicollinearity was not an issue we used Variance Inflation Factor (VIF), the results were low and did not exceed a VIF of 3.

Durbin-Watson was used to validate the independence of error.

### Validation

Classification report was used to validate the model, both classes have the same precision but class 0 has more recall than class 1. It is a quite a good model because it has 
f1-score of .9%. The pseudo square was .81. In the confusion matrix there were no false positives but there are 3 false negatives and 16 true positives. And the area under the curve was .9583.

## Model 2

#### Ensemble methods

That option uses the predicted class labels and takes the majority vote, the model that is considered: LogisticRegression, RandomForestClassifier and Bayes Naive. we chose the
hard voting class The predicted class is the class with the highest majority of votes.

## Other Intent Methods

I tried other methods to obtain a better performance without success, I tried undersampling the data, with the data undersampled I used the model 
Extreme Gradient boosting  based on decision tree algorithm it applies better regularization technique to reduce overfitting. 

## Conclusions
 I consider this model is the best because it does not only rely in one model to have
a better performance it has 3 models. If I had to choose the best model it would be ensemble. The classification report the f1.score and pseudo score performed the same as Model1. Also, the Extreme Gradient boosting is an alternative because it helps not overfit the model.






