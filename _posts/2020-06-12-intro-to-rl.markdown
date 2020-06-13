---
layout: post
title:  "Lecture 1: Introduction to Reinforcement Learning"
ref: welcome
date:   2020-06-10
tags: RL Course
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
