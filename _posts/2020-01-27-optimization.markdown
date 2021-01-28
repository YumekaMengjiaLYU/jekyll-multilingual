---
layout: post
title:  "Optimization Models in Machine Learning"
ref: welcome
date:   2021-01-27
tags: career
lang: en
---

# Intro to Optimization

## Overview

A general optimization problem has the form

+ x optimization variable

+ f objective function

+ constraint functions

## Problem Classes

There are different classes of optimization problems, which can determine a problem's difficulty and solutioun method:

+ Constrained vs Unconstrained

+ Smooth vs Nonsmooth

+ Convex vs Nonconvex

## Convex Optimization

A convex optimization problem has objective and constraint functions that satisfy the inequality

$$f_i(\lambda x+(1-\lambda)y)\leq \lambda f_i(x) +(1-\lambda)f_i(y)$$

for all $x, y\in R^n$ and $0\leq\lambda\leq0$

## Solution Methods

Very few optimization problems have a closed-form solution; most problems are solved using iterative methods.

One important iterative method is gradient descent
$$x^{k+1}=x^k-\alpha \delta f(x^k)$$

### Iterative Methods for Optimization
Iterative methods start with an initial guess $x^0$. Each iteration, a mew value $x^{k+1}$ is generated based on the previous value $x^k$, often using local information such as the gradient $\delta f(x^k)$ or the Hessian $\delta^2 f(x^k)$. The algorithm terminates when a stopping condition is satisfied, which can be specified in terms of the size of the gradient, $||\delta f(x^k)||<\epsilon$, the difference between successive iterates,  $||x^{k+1}-x^k||<\epsilon$ or $||f(x^{k+1})-f(x^k)||<\epsilon$, or a maximum number of iterations, $k>k_max$ 

### Gradient Descent

Gradient descent is built upon the fact that the gradient of a function always points in the direction os maximum ascent, so the negative gradient points in the direction of maximum descent.

### Initial Guess and Condition Number
In the field of numerical analysis, the condition number of a function measures how much the output value of the function can change for a small change in the input argument. 
For $c \in (-2,2)$, the function $f(x,y) = x^2 + cxy+y^2$ describes an ellipsoid with a constant Hessian $\delta^2 f(x,y)$. The condition number of the Hessian $\delta^2 f(x,y)$ is the ratio of its largest eigenvalue to its smallest eigenvalue, and gives a measure of the ellipsoid's eccentricity.

+ A condition number near one means that the ellipsoid is nearly spherical, and different initial conditions along a sublevel set will converge in a similar number of iterations.

+ A large condition number indicates that the sublevel sets are much wider in some directions than in others, so different initial conditions along a sublevel sets could take much longer to converge than others.

Using regularization could improve the condition number

### Stochastic Gradient Descent
For many machine learning problems with large data sets, computing the gradient can be computationally expensive, so an approximation of the gradient is used instead. 

Consider an unconstrained optimizatin problem of the form
$$min \frac{\sum_{i=1}^m f_i(x)}{m}$$
In many cases, each function $f_i$ corresponds to the prediction errorfor a single training example.
Rather than computing the full gradient every iteration, we can approximate it using a sample of the constituent functions. while true stochastic gradient descent only samples one training example per iteration, it's typically more effective to use multiple training examples, called a mini-batch.

One problem with approximating the gadient is that you get a noisy gradient. Depending on the training examples used, the approximations can vary in both size and direction from the true gradient. (For this reason, it no longer makes sense to use the size of the gradient as our stopping condition) One way to reduce the variance is to use a larger mini-batch, but using too large a batch size reduces the computational efficiency gained by approximating the gradient in the first place.

The same problems we had with the step size for gradient descent are now magnified by the noisy gradient: too large a learning rate can cause the problem to diverge, while too small a learning rate can make it slow to converge. A common approach to this problem is to use an adaptive learning rate, defined by a learning rate schedule. The main idea of the approach is to start with a larger learning rate, then slowly decreases it as the model nears a solution. While this doesn't do anything to decrease the variance within the gradient estimates, it prevents the algorithm from oscillating around a solution once it's found one.

## Machine Learning Models
Many problems in machine learning seek to build a model
$$g(a;x) \sim y$$
given a dataset $(a_1,y_1), ...,(a_m,y_m)$
+ a data features
+ y data value or label class
+ prediction function
+ model parameters
+ m number of data points
+ n number of data features
# Linear Regression and Regularization

### Regularization

Many problems in machine learning add a regularization term to the objective function in order to:

+ incorporates prior knowledge about structure in x, such as sparsity or smoothness

+ help avoid overfitting

+ get more robust to data perturbations solutions

+ improve the stability of the solution process

 
# Logistic Regression

# Outlier Removal