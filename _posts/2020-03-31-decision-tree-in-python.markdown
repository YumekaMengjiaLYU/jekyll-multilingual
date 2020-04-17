---
layout: post
comments: true
title:  "Decision Tree in Python"
ref: welcome
date:   2020-04-06
categories: algorithms
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
After downloading the data file, we will use Pandas **read_excel()** method to import data into pandas dataframe. Since there is no header in our data, we set _header_ parameter's value to **0**. Since the raw data is located in the third sheet of the Excel workbook, we set _sheet-name_ parameter's value to **2**. Since the last three rows at bottom of the worksheet are irrelevant data, we set _skipfooter_ parameter's value to **3**.

{% highlight python %}
import pandas as pd

ctg_data = pd.read_excel('CTG.xls', header=0, sheet_name=2, skipfooter=3)
{% endhighlight %}



[ref-2]: https://github.com/YumekaMengjiaLYU/tutorials
[ref-3]: https://archive.ics.uci.edu/ml/datasets/Cardiotocography
References:


[ref-1]: https://learning.oreilly.com/library/view/machine-learning-with/9781787121515/697c4c5f-1109-4058-8938-d01482389ce3.xhtml
