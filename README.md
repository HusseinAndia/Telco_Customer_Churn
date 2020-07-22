# Telco_Customer_Churn

This repository contains my own solution for Kaggle Competition [Telco Customer Churn](https://www.kaggle.com/blastchar/telco-customer-churn).
The main purpose of this project is to analyze the data for customers, develop focused customer retention and try to predict behavior to retain customers.

## Table Of Contents
## 1. Data Manipulation

* In this section, i load the data and read it.
* I use ``.info()`` to show informayion about the data like dtype, # of columns etc.
* Convert ``TotalCharges`` column to numerical type then drop Nan values.
* For columns with ``No internet service`` rows, i replace it with ``No`` so i have only 2 values in these columns. 

## 2. Exploratory Data Analysis (EDA)

* In this section, i explor data by presenting graphs.
* ``Note`` : In github if you use graphs with ``Plotly``, they won't appear so we will present them here.
* This is the graph in cell ``[8]``.![Monthly and Payment Method](/img/MonthlyCharge_PaymentMethod.png)
  * I noticed that most customers prefer Electronic check as their payment method.
  * Between all churn customers Electronic check method also has a very high churn rate.

* This is the graph in cell ``[11]``.![Tenure and Contracts](/img/Tenure.PNG)
  * Customers with "Month to Month Contract" have a very high churn rate.
  * While one and two year contracts' customers wait untill the end of their contracts and most of them renew contract more than once.
 
## 3. Data preprocessing

* In this section, i prepare data before feed it to the prediction models.
* Drop columns i do not need in this stage like ``customerID``.
* For columns with only 2 values ``Yes`` and ``No``, i convert them to ``0`` and ``1``.
* And For columns with many valuea, i use ``get_dummies()`` to convert them to ``0's`` and ``1's``.
* In **Correlation Matrix** sub section, i will use correlation map and heat map to see the correlation between features each other.
* ``Note`` : I will present part of correlation map as it's huge won't be able to present it whole and as in github it only appears as a table.![correlation map](/img/corr_map.PNG)

## 4. Models Building

* In this section, we try many models to get best accuracy.
* I use ``Synthetic Minority Over-sampling Technique for Nominal and Continuous (SMOTE-NC)`` technique to balance the target i want to predict in the training set trying to get high accuracy.
### Models Performance 
* I split the data into 2 main groups, one normal train and test sets and the other for ``SMOTE-NC`` data.
* I trained 4 classification models ``RandomForestClassifier``, ``LogisticRegression``, ``DecisionTreeClassifier`` and ``XGBClassifier``.
* For calculating models performance, i used ``accuracy_score``, ``f1_score``, ``precision_score``, ``recall_score``.

|           Model                  | Accuracy | Recall    | Precision | f1_score |
|----------------------------------|----------|-----------|-----------|----------|
|	XGB Classifier	                 | 77.86%	  |  50.26%	  | 61.27%	  | 55.22%   |  
|	XGB Classifier(SMOTENC)	         | 76.73%	  |  65.09%   |	56.17%	  | 60.30%   |
|	Decision Tree Classifier	       | 78.24%	  |  36.47%   |	68.75%	  | 47.66%   |
|	Decision Tree Classifier(SMOTENC)| 74.88%	  |  71.72%   |	52.76%   	| 60.80%   |
|	Logistic Regression		           | 79.05%   |  51.31%	  | 64.33%	  | 57.08%   |
|	Logistic Regression(SMOTENC)	   | 77.34%	  |  71.72%   | 56.53%	  | 63.23%   |
|	Random Forest Classifier	       | 77.34%	  |  46.94%	  | 60.72%	  | 52.95%   |
|	Random Forest Classifier(SMOTENC)| 77.15%	  |  56.54%	  | 58.17%	  | 57.34%   |
