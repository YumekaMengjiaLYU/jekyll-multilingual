---
layout: post
title:  "Lecture 6: Sequences and Recurrent Networks"
ref: welcome
date:   2020-06-10
tags: courses
lang: en
---

## 1.Motivation
_What are sequences?_
> Element can be repeated
> Order matters
> Of variable length

_How can we develop models that deal with sequential data?_

**Summary**:
> Sequences are collections of variable length where order matters.
> Sequences are widespread across machine learning applications
> Not all deep learning models can handle sequential data

## 2.Fundamentals
![Bias Variance Decomposition](/jupyternb/image/comparison-rnn.png)

### Scalability

### Downsides of using N-grams
**Although it alleviates scalability**
- Doesn't take into account words that are more than N words away
- Data table is still very large

### Summary
Modeling probabilities of sequences scales BADLY given the non-independent structure of their elements

_Can this probability estimation be learned in a more efficient way?_

### Learning to model word probabilities

**1.Vectorizing the context**

f

Desirable properties for f:
- Order matters
- Variable length
- Learnable (differentiable)
- Individual changes can have large effects (non-linear/deep)
- preserve long-term dependencies

**Summary**:
N-grams and simple aggregation do not meet the requirements for modeling sequences.
![Bias Variance Decomposition](/jupyternb/ngram-addition.png)

**2.Modeling conditional probabilities**
Desirable properties for g:
- Individual changes can have large effects(non-linear/deep)
- Returns a probability distribution

**Summary**
N-grams and simple aggregation do not meet the requirements for modeling sequences.

_How can we build a deep network that meets our requirements?_

### Recurrent Neural Networks
**Step 1:**
Persistent state variable h stores information from the context observed so far.

**Step 2:**
RNNs predict the range y (the next word) from the state h:

Softmax ensures that we obtain a probability distribution over all possible words

**Step 3:**
Input next word in sentence x.

Weights are shared over time steps
RNNs rolled out over time

### Loss: Cross Entropy
Next word prediction is essentially a classification task where the number of classes is the size of the vocab.

| For one word | For the sentence | 
|-------|--------|
| $$\mathcal{L}_\theta = -y_t log y_t$$ | $$\mathcal{L}_\theta = -y_t log y_t$$ |
## 3.Generation