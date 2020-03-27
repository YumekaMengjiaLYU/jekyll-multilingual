---
layout: post
title:  "Linear Regression in Python"
ref: welcome
date:   2020-03-27 09:48:44 +0100
categories: algorithms
lang: en
---
Linear regression, as its name suggests, solves a regression problem. It is a simple approach for supervised learning and is especially useful for predicting a quantitative response. 

The dataset can be downloaded [here][here].

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

[here]: https://www.kaggle.com/mohansacharya/graduate-admissions/data
