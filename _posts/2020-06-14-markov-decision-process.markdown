---
layout: post
title:  "Markov Decision Process"
ref: welcome
date:   2020-06-14
tags: reinforcement-learning-lectures
lang: en
---

## Markov Processes

### Introduction to MDPs
- Markov decision process formally describe an environment for reinforcement learning
- Where the environment is fully observable
- i.e. The current state completely characterizes the process 
- Almost all RL problems can be formalized as MDPs
    - Optimal control primarily deals with continuous MDPs
    - Partially observable problems can be converted into MDPs
    - Bandits are MDPs with one state

### Markov Property
"The future is independent of the past given the present"

<div class="definition">

A state is Markov if and only if 
$$P[S_{t+1} |S_t] = P[S_{t+1} | S_1, ... S_t]$$

</div>

- The state captures all relevant information from the history.

- Once the state is known, the history may be thrown away
- i.e. The state is a sufficient statistic of the future.

### State Transition Matrix
For a Markov state s and successor state $s'$, the state transition probability is defined by:

$$
\mathcal{P} = P[S_{t+1}=s' | S_t=s]
$$

State transition matrix $\mathcal{P}$ defines transition probabilities to all successor states $s'$

$$
\mathcal{P} = \begin{bmatrix}
\mathcal{P}_{11} & \cdots & \mathcal{P}_{11} \\
\vdots \\
\mathcal{P}_{11} & \cdots & \mathcal{P}_{nn}
\end{bmatrix}
$$
where each row of the matrix sums to 1.
## Markov Reward Processes

## Markov Decision Processes

## Extensions to MDPs