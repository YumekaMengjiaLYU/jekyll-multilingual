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

### Markov Process
A Markov process is a memoryless random process, i.e. a sequence of random states $S_1$, $S_2$, $\cdots$ with the Markov property.

<div class="definition">

A Markov Process is a tuple <S, P>
- $\mathcal{S}$ is a finite set of states
- $\mathcal{P}$ is a state transition probability matrix

$$P_{ss'} = P[S_{t+1}=s' | S_t=s]$$

</div>

## Markov Reward Processes

### Markov Reward Process
A Markov reward process is a Markov chain with values.
<div class="definition">

A Markov Reward Process is a tuple $\langle \mathcal{S}, \mathcal{P}, \mathcal{R}, \gamma \rangle$
- $\mathcal{S}$ is a finite set of states
- $\mathcal{P}$ is a state transition probability matrix

$$P_{ss'} = P[S_{t+1}=s' | S_t=s]$$
- $\mathcal{R}$ is a reward function, 

$$\mathcal{R}_s = E[R_{t+1}=s' | S_t=s]$$

- $\gamma$ is the discount factor
</div>
### Return
<div class="definition">
The return $G_t$ is the total discounted reward from time-step t.

$$
G_t = R_{t+1} + \gamma R_{t+2} + \cdots
$$
</div>
- The discount $\gamma$ is the present value of future rewards
- The value of receiving R after k+1 time-steps is ${\gamma}^k R$
- This values immediate reward above delayed reward
    - $\gamma$ close to 0 leads to "myopic" evaluations
    - $\gamma$ close to 1 leads to "far-sighted" evaluation

### Why discount?

Most Markov reward and decision processes are discounted.
- Mathematically convenient to discount rewards
- Avoids infinite returns in cyclic Markov processes
- Uncertainty about the future may not be fully represented
- If the reward is financial, immediate rewards may earn more interest than delayed rewards
- Animal/human behavior shows preference for immediate reward
- It is sometimes possible to use undiscounted Markov reward processes (i.e. $\gamma=1$), e.g. if all sequences terminate

### Value Function
- The value function $v(s)$ gives the long-term value of state s
<div class="definition">
The state value function $v(s)$ of an MRP is the expected return starting from state s
$$
v(s) = E[G_t | S_t = s]
$$
</div>

### Bellman Equation for MRPs
The value function can be decomposed into two parts:
- immediate reward R_{t+1}
- discounted value of successor state $\gamma v(S_{t+1})$

$$
v(S) = E[R_{t+1} + \gamma v(S_{t+1}) | S_t=s]
$$

![backpropagation](/jupyternb/image/bellman-graph.png)

### Bellman Equation in Matrix Form
The Bellman equation can be expressed concisely using matrices,

$$
v = \mathcal{R} + \gamma \mathcal{P}v
$$
where v is a column vector with one entry per state

$$
\[
\begin{bmatrix}
    v_{1}       \\
    \vdots \\
    v_{n}       
\end{bmatrix}
=
\begin{bmatrix}
    \mathcal{R}_{1}       \\
    \vdots \\
    \mathcal{R}_{n}        
\end{bmatrix}
+
\gamma\begin{bmatrix}
    \mathcal{P}_{11} & \dots  & \mathcal{P}_{1n} \\
    \vdots \\
    \mathcal{P}_{11} & \dots  & \mathcal{P}_{nn}
\end{bmatrix}\begin{bmatrix}
    v_{1}       \\
    \vdots \\
    v_{n}       
\end{bmatrix}
\]
$$
## Markov Decision Processes

## Extensions to MDPs