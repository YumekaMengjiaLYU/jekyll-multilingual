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

Let's fit the logistic regression model to our data:

{% highlight python %}

X_train, X_test, y_train, y_test = train_test_split(heart_disease, test_size=0.2, random_state=0)

log_regressor = LogisticRegression()
log_regressor.fit(X_train, y_train)

y_pred = log_regressor.predict(X_test)

print(classification_report(y_test, y_pred))

print(confusion_matrix(y_test, y_pred))
{% endhighlight %}
[here]: https://www.kaggle.com/dileep070/heart-disease-prediction-using-logistic-regression

References:

[Course Note][ref-1]

[Notes Andrew NG Course][ref-2]

[Medium Post][ref-3]

[ref-1]: https://www.stat.cmu.edu/~ryantibs/advmethods/notes/logreg.pdf
[ref-2]: https://joparga3.github.io/standford_logistic_regression/index.html#what-is-logistic-regression
[ref-3]: https://medium.com/@anishsingh20/logistic-regression-in-python-423c8d32838b