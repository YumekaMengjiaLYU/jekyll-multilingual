---
layout: post
title:  "Deep Learning Lectures: Intro to Machine Learning & AI"
ref: welcome
date:   2020-06-03
tags: courses
lang: en
---

1. 
### What is intelligence?
Intelligence measures an agent's ability to achieve goals in a wide range of environments.
Shane's 
Reinforcement Learning
- General Purpose Framework for AI
- Agent interacts with the environment
- Select actions to maximize long-term reward (not immediate reward)
- Encompasses supervised and unsupervised learning as special cases

Why use games to solve AI?
- Microcosms of the real world
    - games are a pivoting ground for real-word situations
- Stimulate Intelligence
    - By presenting a diverse set of challenges
- Good to test in simulations
    - Efficient/run thousands in parallel/faster than real time
- Measure progress and performance
    - Measure progress and compare against human performance 

Reinforcement learning algorithms can be trained to "superhuman skills" as playing Atari games.
By Shane's definition of the hallmark  the ability to solve many different tasks to a high standard, w to call that agent to have acquired some degree of intelligence.

### Why "Deep Learning"?
- First need to Previous systems required feature engineering for every new problem
    - need to define features that describe the state of the problem. For documents, we would need bag-of-words features. For visuals, we need particular features like edge detectors.
- Deep Learning enables end-to-end learning for a given loss and architecture
- Through architecture, we can put prior knowledge. Weak prior knowledge can be encoded via architecture (e.g. convolutions, recurrence)
- Deep Learning made possible by:
    - Greater computational power (GPUs, TPUs)
    - More available data (mobile devices, online services, distributed sensors, crowdsourcing)
    - Better understanding of algorithms and architecture (Github/arXiv)
2 AlphaGo&Alpha Zero

###
There are 361 vertices on which to put the stone.
Use two networks to reduce the size of search space of possible games.
policy network take as input the raw go position, map it to a probability distribution of moves
value network take in , output one number for evaluation
human game records
Imitation learning -> weights of policy network
generate allow us
learn the probability of any given position for black or white to win

Exhaustive search huge search tree
The policy network allows us to be smart about the moves that we choose. We can focus on the professional would be likely to play.
The game tree is deep.
Value net. No need to go all the way to observe its outcome. We can use the trained value network to give us an estimate of how good the position is.
The policy network and the value reduce the size of the search tree and allow us to traverse it and find good plans init.

In March 2016, AlphaGo defeated Lee Sedol.

AlphaZero: One Algorithm, Three Games

The Royal Game
Dr.