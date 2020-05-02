---
layout: post
comments: true
title:  "Decision Tree in Python"
ref: welcome
date:   2020-04-06
tags: algorithms
lang: en
---
Decision tree is popular supervised learning algorithm that can be used for both regression and classification. 
Its pros and cons can be summarized as follows, copied from [Machine Learning with Swift][ref-1]: 

Pros:

+ Easy to visualize, understand and interpret.
+ Can work with numerical and categorical features.
+ Requires little data preprocessing (one-hot encoding, dummy variables etc.)
+ Non-parametric model: no assumptions about the shape of data.
+ Fast for inference.
+ Feature selection happens automatically: unimportant features will not influence the result. The presence of multicollinearity also doesn't affect the quality.

Cons:

+ Tends to overfit.
+ Unstable: small changes in data can dramatically affect the structure of the tree and hence influence the final prediction.
+ Finding the globally optimal decision tree is NP-complete. That's why we use different heuristics and greedy search.
+ Inflexible, in the sense that you can't incorporate a new data into them easily. If you obtained new labeled data, you should retrain the tree from scratch on the whole dataset.


The full code is [here][ref-2]

## Data Import
We are going to use the [cardiotocography data set][ref-3]. 
After downloading the data file, we will use Pandas **read_excel()** method to import data into pandas dataframe. Since there is no header in our data, we set _header_ parameter's value to **0**. Since the raw data is located in the third sheet of the Excel workbook, we set _sheet_name_ parameter's value to **2**. Since the last three rows at bottom of the worksheet are irrelevant data, we set _skipfooter_ parameter's value to **3**.

{% highlight python %}
import pandas as pd

ctg_data = pd.read_excel('CTG.xls', header=0, sheet_name=2, skipfooter=3)
{% endhighlight %}

## Data Preprocessing
{% highlight python %}
# Select the relevant numerical columns.
selected_cols = ['LB', 'AC', 'FM', 'UC', 'DL', 'DS', 'DP', 'ASTV', 'MSTV', 'ALTV',
                 'MLTV', 'Width', 'Min', 'Max', 'Nmax', 'Nzeros', 'Mode', 'Mean',
                 'Median', 'Variance', 'Tendency', 'NSP']
ctg_data = ctg_data[selected_cols].dropna()

# Shuffle the dataset.
data_shuffled = ctg_data.sample(frac=1.0, random_state=0)

# Split into input part X and output part Y.
X = data_shuffled.drop('NSP', axis=1)

# Map the diagnosis code to a human-readable label.
def to_label(y):
    return [None, 'normal', 'suspect', 'pathologic'][(int(y))]

Y = data_shuffled['NSP'].apply(to_label)
{% endhighlight %}

Let's split our data into training and test set using sklearn's **train_test_split()** method. 
{% highlight python %}
from sklearn.model_selection import train_test_split
# Partition the data into training and test sets.
Xtrain, Xtest, Ytrain, Ytest = train_test_split(X, Y, test_size=0.2, random_state=0)
{% endhighlight %}
The parameter _test_size_ is given value 0.2; it means test sets will be 20% of whole dataset and training dataset’s size will be 80% of the entire dataset. _random_state_ variable is a pseudo-random number generator state used for random sampling. If you want to replicate our results, then use the same value of random_state.

## Decision Tree Training

### Using Gini Index as criterion
{% highlight python %}
from sklearn.tree import DecisionTreeClassifier

ctg_gini = DecisionTreeClassifier(criterion = "gini", random_state = 100, max_depth=3, min_samples_leaf=5)
ctg_gini.fit(X_train, y_train)
{% endhighlight %}

### Using Information Gain as criterion
{% highlight python %}
ctg_entropy = DecisionTreeClassifier(criterion = "entropy", random_state = 100, max_depth=3, min_samples_leaf=5)
ctg_entropy.fit(X_train, y_train)
{% endhighlight %}

## Calculating Prediction Accuracy Score

The function **accuracy_score()** will be used to print accuracy of Decision Tree algorithm. Accuracy is represented by the ratio of the correctly predicted data points to all the predicted data points. It helps to understand the effectiveness of our algorithm. 
{% highlight python %}
ctg_entropy = DecisionTreeClassifier(criterion = "entropy", random_state = 100,
                               max_depth=3, min_samples_leaf=5)
ctg_entropy.fit(X_train, y_train)
{% endhighlight %}

{% highlight python %}
from sklearn.metrics import accuracy_score
# Prediction for Decision Tree classifier with criterion as gini index
y_pred_gini = ctg_gini.predict(X_test)

# Prediction for Decision Tree classifier with criterion as entropy
y_pred_entro = ctg_entropy.predict(X_test)

# Accuracy for Decision Tree classifier with criterion as gini index
print ("Accuracy using gini index is ", accuracy_score(y_test,y_pred_gini)*100)

# Accuracy for Decision Tree classifier with criterion as entropy
print ("Accuracy using gini index is ", accuracy_score(y_test,y_pred_entro)*100)
{% endhighlight %}

Output:
>Accuracy using gini index is  88.02816901408451
>Accuracy using gini index is  87.32394366197182


References:

[Programming Assignment 1A][ref-4]

[Building Decision Tree Algorithm in Python with Scikit Learn-Rahul Saxena][ref-5]

[ref-1]: https://learning.oreilly.com/library/view/machine-learning-with/9781787121515/697c4c5f-1109-4058-8938-d01482389ce3.xhtml
[ref-2]: https://github.com/YumekaMengjiaLYU/tutorials
[ref-3]: https://archive.ics.uci.edu/ml/datasets/Cardiotocography
[ref-4]:http://www.cse.chalmers.se/~richajo/dit866/pa1a.html
[ref-5]:https://dataaspirant.com/2017/02/01/decision-tree-algorithm-python-with-scikit-learn/