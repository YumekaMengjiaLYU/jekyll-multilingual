---
layout: post
title:  "Lecture 1: Introduction to Reinforcement Learning"
ref: welcome
date:   2020-06-10
tags: reinforcement-learning-lectures
lang: en
---
## About
### Characteristics 
What makes reinforcement learning different from other machine learning algorithms?
- There is no supervisor, only a reward signal (trial and error paradigm)
- Feedback is delayed, not instantaneous
- Time really matters (sequential, non i.i.d. data, a dynamic system) 
- Agent's actions affect the subsequent data it receives

### Examples
- Fly stunt manoeuvers in helicopter
- Just by RL, defeat the world champion at Backgammon
- Manage an investment portfolio
- Control a power station
- Make a humanoid robot walk
- Play many different Atari games better than humans

## The Reinforment Learning Problem
### Rewards
Reinforment learning is based on the reward hypothesis.
<div class="definition">

All goals can be described by the maximization of expected cumulative reward.

</div>
- A reward $R_t$ is a scalar feedback signal
- Inficates how well agent is doing at step t
- The agent's job is to maximize cumulative reward

### Examples of Rewards
- Fly stunt manoeuvres in a helicopter
    - +ve reward for following desired trajectory
    - -ve reward for crashing
- Defeat the world champion at Backgammon
    - +/-ve reward for winning/losing a game
- Manage an investment portfolio
    - +ve reward for each $ in bank
- Control a power station
    - +ve reward for producing power
    - -ve reward for exceeding safety thresholds
- Make a humanoid robot walk
    - +ve reward for forward motion
    - -ve reward for falling over
- Play many different Atari games better than humans
    - +/-ve reward for increasing/decreasing score

### Sequential Decision Making
_How can we create a unifying framework for all of them?_

Goal is the same!
- Goal: select actions to maximize total future reward
- Actions may have long term consequences - have to think ahead
- Reward may be delayed
- It may be better to sacrifice immediate reward to gain more long-term reward
- Examples:
    - Financial investment (may take months to mature)
    - Refuelling a helicopter when short on fuel (might prevent a crash in several hours)
    - Blocking opponent moves (might help winning chances many moves from now)

### Agent and Environment
Want to build an algorithm/agent that acts like a brain.

For every time step, it is able to take actions based on observation and reward signals.

- At each step $t$ the agent:
    - Executes action $A_t$
    - Receives observation Q
    - Receives scalar reward $R_t$

- The environment:
    - Receives action $A_t$
    - Emits observation $O_t$
    - Emits scalar reward $R_t$

The experiences of the agent can be defined by the time series of observation, reward and action, which are the data used for RL.

### History and State
- The history is the sequence of observations, actions, rewards

$$H_t = A_1, O_1, R_1, ..., A_t, O_t, R_t$$

- i.e. all observable variables up to time t
- i.e. the sensorimentor system of a robot or embodied agent
- What happens next depends on the history:
    - The agent selects actions (the algorithm is the mapping)
    - The environment selects observations/rewards
- State is the summary of information used to determine what happens next
- Formally, at time step t, state is a function of the history:
$$S_t = f(H_t)$$

There are several definitions of state!

### Environment State
- The environment state $S_t$ is the environment's private representation
- i.e. whatever data the environment uses to pick the next observation/reward
- The environment state is not usually visible to the agent
- Even if $S_t$ is visible, it may contain irrelevant information (have subjective representation might be a good thing)

It does not tell us amything useful about building the algo.

### Agent State
- The agent state $S_t$ is the agent's internal representation
- i.e. whatever information the agent uses to pick the next action
- i.e. it is the information used by reinforcement learning algo
- It can be any function of history: $S_t = f(H_t)$

### Information State
An information state (a.k.a Markov state) contains all useful information from the history.

<div class="definition">

A state is Markov if and only if 
$$P[S_{t+1} |S_t] = P[S_{t+1} | S_1, ... S_t]$$

</div>

- The future is independent of the past given the present
- Once the state is known, the history may be thrown away
- i.e. The state is a sufficient statistic of the future rewards
- The environment state $S_t$ is Markov
- The history $H_t$ is Markov
**All that matters is the current moment**

Non-markov: imperfect state representation 

### Rat Example
How to build an agent that does the best job of predicting what's gonna happen next?

### Fully Observable Environment
Fully oberservability: agent directly observes environment state

$O_t = S_t^a = S_t^a$

- Agent state = environment state = information state
- Formally, this is a Markov decision process.

### Partially Observable Environment
- Partial observability: agent indirectly observes environment
    - A robot with camera vision isn't told its absolute location
    - A trading agent only observes current prices
    - A poker playing agent only observes public cards
- Now agent state  $\neq$ environment state

- Formally this is a partially observable Markov decision process
- Agent must construct its own state representation ${S_t}^a$
    - Complete history ${S_t}^a = H_t$
    - Beliefs of environment state (vector of prob)
    - Recurrent neural network $\sigma ({S_{t-1}}^a W_s + O_t W_o)$

## Inside an RL Agent 
### Major Components of an RL Agent
- An RL agent may include one or more of these components
    - Policy: agent's behavior function
    - Value function: how good is each state and/or action (reward expected)
    - Model: agent's representation of the environment

### Policy
- A policy is the agent's behavior
- It is a map from state to action 
- Deterministic policy: $a = \pi (s)$ 
- Stochastic policy: $\pi (a | s) = P[A=a | S=s]$ 

### Value Function
- Value function is a prediction of future reward
- Used to evaluate the goodness/badness of states
- And therefore to select between actions

$$v_{\pi}(s) = E_{\pi} [R_t + \gamma R_{t+1} + {\gamma}^2 R_{t+2} + ... | S_t = s]$$

Discounting more future rewards.

### Model
- A model predicts what the environment will do next
- Transitions: $\mathcal{P} predicts the next state (i.e. dynamic)
- Rewards: $\mathcal{R}$ predicts the next immediate reward

$$\mathcal{P} = P[S'=s' | S=s, A=a]$$


$$\mathcal{R} = E[R | S=s, A=a]$$

Not a requirement to build a model for env.

### Maze Example
- Rewards: -1 per time step
- Actions: N, E, S, W
- States: Agent's location

### Categorizing RL agents
- Value based
    - No policy or Implicit policy
    - Value Functions

- Policy based
    - Policy
    - No Value Function

- Actor Critic
    - Policy
    - Value Function

- Model Free
    - Policy and/or Value Function
    - No Model (without knowing how env works)
- Model based
    - Policy and/or Value Function
    - Model
## Problems Within Reinforcement Learning

### Learning and Planning
Two fundamental problems in sequential decision making
- Reinforcement Learning
    - The enviroment is initially unknown
    - The agent interacts with the environment
    - The agent improves its policy
- Planning
    - A model of the environment is known
    - The agent performs computations with its model (w/o any external interaction)
    - The agent improves its policy
    - a.k.a deliberation, reasoning, introspection, pondering, thought, search

### Atari Example: Reinforcement Learning
- Rules of the game are unknown
- Learn directly from interactive game-play
- Pick actions on joystick, see pixels and scores

### Atari Example: Planning
- Rules of the game are known
- Can query emulator
    - perfect model inside agent's brain
- If I take action a from state s:
    - what would the next state be?
    - what would the score be?
- Plan ahead to find optimal policy
    - e.g. tree search

### Exploration and Exploitation
_How to balance exploration and exploitation?_
- Reinforcement learning is like trial-and-error learning
- The agent should discover a good policy
- From its experiences of the environment
- Without losing too much reward along the way
- Exploration finds more information about the environment
- Exploitation exploits known information to maximize reward
- It is usually important to explore as well as exploit.