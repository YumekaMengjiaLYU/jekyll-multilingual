---
layout: post
comments: true
title:  "On Bias and Variance"
ref: welcome
date:   2020-04-17
tags: theory
lang: en
---

Trade-offs are _everywhere_. As an EE undergraduate taking courses in circuits, I was taught how circuit design is a game of trade-offs and there is never free lunch: we have to trade one thing for other desirable properties.    
For example, in analog design, we have to consider many aspects of the circuit performance such as linearity, noise, input/output impedance, stability, and voltage swings. Normally we cannot optimize all of these parameters and have to trade some aspects for others. Sometimes we have to resort to trials and errors by treaking the dials and knobs available to us.
Therefore, it isn't surprising for me to come across tradeoff again in machine learning.

What is a bias-variance tradeoff?

Starting from the definition of variance:
$${ \operatorname {Var} [X]=\operatorname {E} [X^{2}]-{\Big (}\operatorname {E} [X]{\Big )}^{2}.}$$


References:

[Bias Variance Tradeoff][ref-1]

[Trade-off][ref-2]

[Analog Design Trade-Offs in Applying Linearization Techniques Using Example CMOS Circuits][ref-3]

[ref-1]:https://en.wikipedia.org/wiki/Bias%E2%80%93variance_tradeoff
[ref-2]:https://en.wikipedia.org/wiki/Trade-off
[ref-3]:https://www.allaboutcircuits.com/technical-articles/analog-design-trade-offs-in-applying-linearization-techniques-CMOS-circuits/