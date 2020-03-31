---
layout: post
title:  "Logistic Regression in Python"
ref: welcome
date:   2020-03-29 
categories: algorithms
lang: en
---

Logistic regression is the most basic algorithm for classfication. It extends the idea of linear regression to cases where the dependent variable only has a discrete number of outcomes, which are also called classes. Depending on the number of possible outcomes, we can classify logistic regression models into two types: binary logistic regression and multiple logistic regression. 


Instead of modeling `Y` as a linear function of `X` directly, we model the probability that is equal to class 1, given X. 

For this tutorial, we are going to use logistic regression to predict whether a patient has 10-year-risk of future coronary heart disease. The dataset can be downloaded [here][here].

We can import all the required libraries and our dataset:

{% highlight python %}
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn import metrics

grad_admissions = pd.readcsv('/Users/mengjialyu/Documents/Kaggle/graduate-admissions/Admission_Predict.csv')

{% endhighlight %}
Data preprocessing is an important initial step when doing machine learning projects. `seaborn` is a great library that can provide  a visualization of missing data. The `cmap` here refers to the mapping from data values to color space, abd 

{% highlight python %}
# Set the palette to the "pastel" default palette:
sns.set_palette("pastel")
sns.heatmap(heart_disease.isnull(), yticklabels = False, cbar= False)
{% endhighlight python %}
Now we have this pretty little graph :)
![heatmap](/assets/2020-03-30-heatmap.png)

It looks like do not have much missing data. So we can exclude the rows with missing values.
{% highlight python %}
heart_disease.dropna(axis = 0, inplace = True)
{% endhighlight python %}

Let's move on and fit a logistic regression model to our data.

From the [data-description][here], we know that Sex-`male`, Current Smoker-`currentSmoker`, BP Meds-`BPMeds`, Prevalent Stroke-`prevalentStroke`, Prevalent Hyp-`prevalentHyp` and Diabetes-`diabetes` are nominal variables. To apply a egression analysis on any dataset, we have to first tranform categorical features to dummy variables using the `get_dummies()` function from pandas. Dummy variables assign numerical values to the original categorical levels so that the computers can compute on them :) Note that we [one-hot encode][one-hot encode] our data by setting the parameter `drop_first` to `True`.
{% highlight python %}
heart_disease = pd.get_dummies(heart_disease, columns = ['male','currentSmoker','BPMeds','prevalentStroke', 'prevalentHyp', 'diabetes'])

X = heart_disease.loc[:, heart_disease.columns != 'TenYearCHD']
y = heart_disease.loc[:, 'TenYearCHD']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)

log_regressor = LogisticRegression()
log_regressor.fit(X_train, y_train)

y_pred = log_regressor.predict(X_test)

print(classification_report(y_test, y_pred))

print(confusion_matrix(y_test, y_pred))
{% endhighlight %}
[here]: https://www.kaggle.com/dileep070/heart-disease-prediction-using-logistic-regression
[one-hot encode]: https://machinelearningmastery.com/why-one-hot-encode-data-in-machine-learning/
References:

[Advanced Methods for Data Analysis Course Note][ref-1]

[Notes Andrew NG Course][ref-2]

[Medium Post][ref-3]

[ref-1]: https://www.stat.cmu.edu/~ryantibs/advmethods/notes/logreg.pdf
[ref-2]: https://joparga3.github.io/standford_logistic_regression/index.html#what-is-logistic-regression
[ref-3]: https://medium.com/@anishsingh20/logistic-regression-in-python-423c8d32838b