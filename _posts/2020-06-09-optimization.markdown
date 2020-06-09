---
layout: post
title:  "Lecture 5: Optimization for Machine Learning"
ref: welcome
date:   2020-06-09
tags: courses
lang: en
---
## 1.Intro and motivation

### Motivation

- Optimization algorithms are the basic engine behind deep learning methods that enable methods to learn from data by adapting their parameters.

- They solve the problem of the minimization of an objective function that measures the mistakes made by the model.
    - e.g. prediction error(classification), negative reward(reinforcement learning)

- Work by making a sequence of small incremental changes to model parameters that are each guaranteed to reduce the objective by some small amount.

### Basic notation

- Parameters
$$
\theta \in R^n
$$

- Real-valued objective function
$$
h(\theta)
$$

- Goal of optimization
$$
\theta^* = argmin h(\theta)
$$

### Example: neural metwork training objective
- The standard neural network training objective is given by:
$$
h(\theta)=\frac{1}{m} \sum_{i=1}^m l(y_i, f(x_i, \theta))
$$
## 2.Gradient descent

## 3.Momentum methods

## 4.2nd-order methods

## 5.Stochastic optimization