---
layout: post
title:  "Linear Regression in Python"
ref: welcome
date:   2020-03-27 
categories: algorithms
lang: en
---
Linear regression, as its name suggests, predict the value of the outcome variable `y` by finding out a linear relationship between input `x` and output `y`. It is a simple approach for supervised learning and is especially useful for predicting a quantitative response. Depending on the number of predictors `x`, we can classify linear regression models into two types: binary linear regression and multiple linear regression. 

For this tutorial, we are going to use multiple linear regression to predict the chance of graduate school admissions. The dataset can be downloaded [here][here].

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

Using the `LinearRegression()` function from `sklearn`, we can fit a linear regression model to our data.

`train_test_split()` is an especially useful function. It splits a given dataset into random train and test subsets. The argument `test_size` varies between 0.0 and 1.0, and represents the proportion of the dataset to include in the train split. Another argument `random_state` represents the [seed][seed] used by the random number generator. 

Let's fit the linear regression model to our data:
{% highlight python %}

X = grad_admissions[['GRE Score', 'TOEFL Score', 'University Rating', 'LOR ', 'SOP', 'CGPA', 'Research']].values
y = grad_admissions['Chance of Admit '].values

grad_admissions.isnull().any()
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state=0)

regressor = LinearRegression()

regressor.fit(X_train, y_train)
{% endhighlight %}


We can evaluate our model by calculating the mean squared error of the model.

{% highlight python %}
# transform X from numpy array to panda data frame to access .columns attribute
X= pd.DataFrame(X)
coeff_df = pd.DataFrame(regressor.coef_, X.columns, columns=['Coefficients'])

y_pred = regressor.predict(X_test)


df = pd.DataFrame({'Actual': y_test, 'Predicted': y_pred})

mean_squared_error = np.sqrt(metrics.mean_squared_error(y_test, y_pred))
print(mean_squared_error)
{% endhighlight %}

Our mean squared error is computed to be 0.069, which is slightly less than 10% of the actual mean 0.724. 

This indicates that our linear regression model is reasonably accurate and can make good predictions!

[here]: https://www.kaggle.com/mohansacharya/graduate-admissions/data
[seed]: https://www.statisticshowto.datasciencecentral.com/random-seed-definition/

References:

[Medium Post][ref-1]

[ref-1]:https://towardsdatascience.com/a-beginners-guide-to-linear-regression-in-python-with-scikit-learn-83a8f7ae2b4f