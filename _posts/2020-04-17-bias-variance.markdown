---
layout: post
comments: true
title:  "On Bias and Variance"
ref: welcome
date:   2020-04-17
tags: theory
lang: en
---

First we already have a great [post][ref-4].
Trade-offs are _everywhere_. As an EE undergraduate taking courses in circuits, I was taught how circuit design is a game of trade-offs and there is never free lunch: we have to trade one thing for other desirable properties.    
For example, in analog design, we have to consider many aspects of the circuit performance such as linearity, noise, input/output impedance, stability, and voltage swings. Normally we cannot optimize all of these parameters and have to trade some aspects for others. Sometimes we have to resort to trials and errors by treaking the dials and knobs available to us.
Therefore, it isn't surprising for me to come across tradeoff again in machine learning.

What is a bias-variance tradeoff?
It refers to the situations where models have a lower bias in parameter estimation have a higher variance of the parameter estimates across samples, or vice versa.
Starting from the definition of variance:
$${ \operatorname {Var} [X]=\operatorname {E} [X^{2}]-{\Big (}\operatorname {E} [X]{\Big )}^{2}.}$$

$${ \operatorname {Err} (x)=\operatorname {E} [Y^{2}]-{\Big (}\operatorname {E} [X]{\Big )}^{2}.}$$
![Bias Variance Decomposition](/jupyternb/image/decomposition.png){:class="img-responsive"}

A illustration from [Choosing Prediction Over Explanation in Psychology: Lessons From Machine Learning][ref-6]
![Prediction](/jupyternb/image/bias-variance.png)
An estimator’s predictions can deviate from the desired outcome (or true scores) in two ways.
First, the predictions may display a systematic tendency (or bias) to deviate from the central tendency of
the true scores (compare right panels with left panels). Second, the predictions may show a high degree
of variance, or imprecision (compare bottom panels with top panels). 


References:

1.[Bias Variance Tradeoff][ref-1]

2.[Trade-off][ref-2]

3.[Analog Design Trade-Offs in Applying Linearization Techniques Using Example CMOS Circuits][ref-3]

5.[ESL Chap 7-Model Selection-Rob Tibshirani][ref-5]
[ref-1]:https://en.wikipedia.org/wiki/Bias%E2%80%93variance_tradeoff
[ref-2]:https://en.wikipedia.org/wiki/Trade-off
[ref-3]:https://www.allaboutcircuits.com/technical-articles/analog-design-trade-offs-in-applying-linearization-techniques-CMOS-circuits/
[ref-4]:http://scott.fortmann-roe.com/docs/BiasVariance.html
[ref-5]:http://statweb.stanford.edu/~tibs/stat315a/LECTURES/chap7.pdf
[ref-6]:http://jakewestfall.org/publications/Yarkoni_Westfall_choosing_prediction.pdf

Probability Density estimation is the construction of an estimate based on observed data. It involves selecting a probability distribution function and the parameters of that function that best explains the joint probability of the observed data.
The GMM or Gaussian Mixture Model is a mixture model that uses a combination of probability distribution and requires the estimation of mean and standard deviation parameters 

Advantages
It is guaranteed that the likelihood will increase with each iteration.
During implementation, the E-step and M-step are very easy for many problems.
The solution for M-step often exists in closed form.
Disadvantage
EM algorithm has a very slow convergence.
It makes the convergence to the local optima only.
EM requires both forward and backward probabilities.