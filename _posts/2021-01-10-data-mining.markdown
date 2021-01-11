---
layout: post
title:  "What I Learned In My Data Mining Class"
ref: welcome
date:   2021-01-10
tags: career
lang: en
---
Thanks to professor Qian for teaching this class!

### Variable Selection

### Basis Expansions
Overarching idea:
Augment or replace the vector of inputs with additional variables, which are transformations of the inputs, and then use linear models in this new space of derived input features.

#### Linear Basis Expansion
$h_m(X)$ are our basis expansions
$f(X) = \sum_{m=1}^M \beta_m h_m(X)$

#### Common Expansions
- $h_m(X) = X_m$

- $h_m(X) = X_j^2$

- $h_m(X) = X_jX_k$

- $h_m(X) = log(X_j)$

- $h_m(X) = \sqrt(X_j)$
### Smoothing Methods

### Kernel Methods


### Trees 
 Bagging and random forests are “bagging” algorithms that aim to reduce the complexity of models that overfit the training data. In contrast, boosting is an approach to increase the complexity of models that suffer from high bias, that is, models that underfit the training data. https://sebastianraschka.com/faq/docs/bagging-boosting-rf.html
#### CART

#### Bagging

#### Boosting

#### Random Forests
Random Forests are a modification to Bagging which generatesand averages a large collection of decorrelated trees

The key feature is to grow each tree from m < p variablesselected randomly from the training data

Smaller m will result in smaller correlations between each treeand consequently the average of B trees.

Advantages
- usually have good prediction ability
- can be used to solve both classification as well as regressionproblems
- very little tuning is required
Disadvantages
- it is computationally expensive
- less interpretable than a single decision tree
### Neural Networks

### Density Esimation
If the goal is to estimate the PDF, then this problem is called density estimation
#### Parametric Density Estimation

##### Parametric model
A problem of parametric model is that the bias ¯p(x) − p(x) is unavoidable so even we have huge amount
of observations from the same population, we are still unable to recover the original PDF. 

However, the
parametric model has an advantage that each parameter has its own meaning so it is very easy to interpret
the result.
##### Mixture Model
If we want to use a parametric model, how can we resolve the problem of unavoidable bias? Here is a method
that can alleviate this bias – mixture of distributions.
The mixture of distributions is using a mixture of parametric distribution to model the underlying population
PDF.
#### Nonparametric Density Estimation

##### Histogram

##### Kernel density estimator
A kernel function generally has three features:
-  K(x) is symmetric.

- $\int K(x)dx = 1$.

- limx→−∞ K(x) = limx→+∞ K(x) = 0.

Three most common kernel functions 

- Gaussian Kernel $K(x) = \frac_{1}{\sqrt(2\pi)}e^{(-x^2/2)}$
- Uniform Kernel $K(x) = \frac_{1}{2} I(-1\leq x\leq 1)$
- Epanechnikov Kernel $K(x) = \frac{3}{4} max{1-x^2,0}$

The Epanechnikov is a special kernel that has the lowest (asymptotic) mean square error.

http://faculty.washington.edu/yenchic/18W_425/Lec6_hist_KDE.pdf
##### K-nearest neighbor

##### Basis approach

### Hidden Markov Chains

Components of HMM are
- The number of states $J$

- The initial state distribution $P(S0)$

- The hidden state transition probability $P1(st+1)$

- The output distribution $B(ot|st)$

Algorithm

- Evaluation

- Decoding

- Learning
### Clustering

### Multiple Testing

#### Permutation Test

Permutation test use random shuffles of data to get the correct sampling distribution of a test statistic under the null hypothesis. 

It does not assume normality, just that the points are drawn from the same unknown distribution independently; and it's used when the distribution of the test statistic is unknown or hard to compute

How we test:
- Compare the difference of means (or some other reasonable statistic) between the two groups


- Make a large number of random shufflings of the points

- For each compute the statistic

- See whether, out of say 9999 shuffles, when the true value is added in, it is in the top 5% of these 10000 shuffles


https://homes.cs.washington.edu/~suinlee/genome560/lecture10.pdf
### Reinforcement Learning