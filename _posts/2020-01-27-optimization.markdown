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

# Linear Regression and Regularization

# Logistic Regression

# Outlier Removal