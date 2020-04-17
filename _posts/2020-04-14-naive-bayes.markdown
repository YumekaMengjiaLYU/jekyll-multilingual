---
layout: post
title:  "Bayes Naive Classifiers"
ref: welcome
date:   2020-04-14 
categories: algorithms
lang: en
---

There is an important disctinction between generative and discriminative models.

### Why Naive? 
We assume that every feature is independent of the other ones.

### Why Bayes?
We apply Bayes' theorem in the classfier's decision rule.
### Why Classifiers?
NBC classify, meaning it predicts which set of categories a new observation belongs.

Naive Bayes classifiers are a family of probabilistic classifiers that is able to predict, given an observation of input, a probability distribution over a set of classes.
Support Vector Machine is popular supervised learning algorithm that can be used for both regression and classification. 
Its pros and cons can be summarized as follows
Pros:

+ Highly scalable, requiring a number of parameters linear in the number of predictors in a learning problem and hence faster compared to complicated algorithms.
+ Works well for high dimensional problems such as text classification because it makes a very strong assumption. 

Cons:

+ The naive assumptionis not usually the case in real life problems.

### Construct Naive Bayers

References:
[MIT 15.097 Course Notes][ref-1]
[Naive Bayes Classifier Wiki][ref-2]
[Medium Post by Soner Yildirim][ref-3]
[ref-1]:https://ocw.mit.edu/courses/sloan-school-of-management/15-097-prediction-machine-learning-and-statistics-spring-2012/lecture-notes/MIT15_097S12_lec07.pdf&sa=U&ved=2ahUKEwi-18iFy-_oAhVgmHIEHenxAIwQFjAAegQIABAB&usg=AOvVaw1uQhAK5Np4e23kDR_1BqEd
[ref-2]:https://en.wikipedia.org/wiki/Naive_Bayes_classifier
[ref-3]:https://towardsdatascience.com/naive-bayes-classifier-explained-50f9723571ed