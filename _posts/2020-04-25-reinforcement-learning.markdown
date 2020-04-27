---
layout: post
title:  "Reinforcement Learning"
ref: welcome
date:   2020-04-26
tags: career
lang: en
---
It is about taking suitable action to maximize reward in a particular situation. It is employed by various software and machines to find the best possible behavior or path it should take in a specific situation. Different from supervised learning, it learns from its experience.

Q-Learning is a basic form of Reinforcement Learning which uses Q-values (also called action values) to iteratively improve the behavior of the learning agent.

The ‘q’ in q-learning stands for quality. Quality in this case represents how useful a given action is in gaining some future reward.

s- set of states
a- set of actions
Pr = transitions
alpha = starting state distribution
gamma = discount factor
rs /r(s,a)= reward 

we want to obtain a function Q(s,a) that predicts best action a in state s in order to maximize a cumulative reward. This function can be estimated using Q-learning, which iteratively updates Q(s,a) using the Bellman Equation. 

The exploration vs exploitation dilemma is exemplified by the question of whether an AI should trust the learnt values of Q enough to select actions based on it or try other actions hoping that might give it a better reward.

It will perform the sequence of actions that will eventually generate the maximum total reward. This total reward is also called the Q-value and we will formalise our strategy as:



The above equation states that the Q-value yielded from being at state s and performing action a is the immediate reward r(s,a) plus the highest Q-value possible from the next state s’. Gamma here is the discount factor which controls the contribution of rewards further in the future.

References:


[Metaheuristic Optimization][ref-1]

[Simple Reinforcement Learning: Q-learning][ref-2]

[A Hands-On Introduction to Deep Q-Learning using OpenAI Gym in Python][ref-3]

[ref-1]:https://www.geeksforgeeks.org/what-is-reinforcement-learning/
[ref-2]:https://towardsdatascience.com/simple-reinforcement-learning-q-learning-fcddc4b6fe56
[ref-3]:https://www.analyticsvidhya.com/blog/2019/04/introduction-deep-q-learning-python/