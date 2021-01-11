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

### Smoothing Methods

### Kernel Methods


### Trees 

#### CART

#### Bagging

#### Boosting

### Neural Networks

### Density Esimation
If the goal is to estimate the PDF, then this problem is called density estimation
#### Parametric Density Estimation

##### Parametric model

##### Mixture Model

#### Nonparametric Density Estimation

##### Histogram

##### Kernel density estimator
A kernel function generally has three features:
-  K(x) is symmetric.

- $\int K(x)dx = 1$.

- limx→−∞ K(x) = limx→+∞ K(x) = 0.

Three most common kernel functions 

- Gaussian Kernel
- Uniform Kernel
- Epanechnikov Kernel
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