---
layout: post
title:  "Lecture 1: Intro to Machine Learning & AI"
ref: welcome
date:   2020-06-03
tags: courses
lang: en
---

## Solving Intelligence
### What is intelligence?
If we want to create artificial intelligence, we need to know the characteristics of an intelligent agent.

The hallmark of human intelligence lies in its generality, as science fiction author Robert Heinlein puts it,  _"specialization is for insects"_. 
After sifting through over 70 definitions of intelligence, Shane Legg arrived at the following synthesized definition:
>Intelligence measures an agent's ability to achieve goals in a wide range of environments.


Reinforcement Learning
- General Purpose Framework for AI
- Agent interacts with the environment
- Select actions to maximize long-term reward (not immediate reward)
- Encompasses supervised and unsupervised learning as special cases

Why use games to solve AI?
- Microcosms of the real world
    - Games are a pivoting ground for real-word situations
- Stimulate Intelligence
    - By presenting a diverse set of challenges
- Good to test in simulations
    - Efficient/run thousands in parallel/faster than real time
- Measure progress and performance
    - Measure progress and compare against human performance (can also serve as a reward) 


A particular application [Human-level control through deep reinforcement learning][ref-1]: Ran reinforcement learning algorithms over different Atari games and achieved "superhuman skills" in many of those Atari games. 

By Legg's definition that the hallmark of intelligence is the ability to solve many different tasks to a high standard, the agent can be considered to have acquired some degree of intelligence.

### Why "Deep Learning"?
- First need to Previous systems required feature engineering for every new problem
    - For documents, we would need bag-of-words features. 
    - For visuals, we need particular filters like edge detectors.
- Deep Learning enables end-to-end learning for a given loss and architecture of the neural network
- Weak prior knowledge can be encoded via architecture (e.g. convolutions, recurrence) 
    - Learning becomes easier as it requires less training data and hence less computation 
- Deep Learning made possible by:
    - Greater computational power (GPUs, TPUs)
    - More available data (mobile devices, online services, distributed sensors, crowdsourcing)
    - Better understanding of algorithms and architecture (open source on Github/arXiv)

## AlphaGo&Alpha Zero Case Studies

### 1.Board Games 
[A general reinforcement learning algorithm that masters chess, shogi, and Go through self-play][ref-2]

Go: 361 vertices, many scenarios.
AlphaZero uses two networks to reduce the size of search space of possible games.
**Policy Network** 
- take in the raw go position 
- map it to a probability distribution over moves
**Value Network** 
- take in given position 
- output one number as evaluation of that position (is it good for black or white?)
human game records
To train, we do imitation learning from human players which give the weights of policy network.
Then we can use the policy network to generate more games that allow us to train the value network.

From the data, we can learn the probability of any given position for black or white to win (learning the value func).

The problem: exhaustive search/ huge search tree.
The policy network allows us to be smart about the moves that we choose and can bias the search in the right direction.
The game tree is deep.
The trained value network can give us an estimate of how good the position is.
Togethr, the policy network and the value network reduce the size of the search tree and allow us to traverse it and find good plans

In March 2016, AlphaGo defeated Lee Sedol.




Using much less human knowledge, AlphaZero can play games against itself. Initialized with a policy and value network, AlphaZero self-plays by evaluating the search tree from a given position and making its best move. Then repeat from the next position.  





**Conclusions**
- Deep Learning enables us to search the huge search space of complex board games.
- Self-play produces large amounts of data necessary for training the deep neural networks.
- Self-play provides an **automatic curriculum**, starting from simple opponents to stronger and stronger opponents. (training against itself)
- System discovers new knowledge.(Discover chess opening thoery)
- New directions: Learn rules of the game, more than two players, imperfect information, larger action spaces etc.

### 2.Learning to Play Capture the Flag

[Human-level performance in 3D multiplayer games with population-based reinforcement learning][ref-3]


- Large-scale decentralized multi-agent learning problem : objective game where multiple agents need to learn to interact to play

- Population-based training 
- Internal reward evolution
- Hierarchical temporal policies
- Agents exceed human-level, as both teammates and opponents
- Rich emergent representation and behavior

Rule: Pick up other's flag -> Bring it to your own base while keeping the home flag unstolen. 

Training Procedure
- Train a population of agents
- CTF games played by bringing together agents from population for an episode
- Individual streams of experience sent back to participating agents
- Each agent trains with independent RL, independent actions, no global information.

Neural Network Architecture
- Hierarchy of recurrent neural networks at two time scales: Slow and Fast RNN
- Internal/Intermediate rewards based on game events learned at even slower time scale

Population-based Training
- Population of agents serves two purposes
    - Provides diverse teammates and opponents: robust multi-agent training without collapses found with naive self-play
    - Provides meta-optimization of agents using population-based training. Used for model selection, hyperparameter adaptation, internal reward evolution (robustness against different playing styles)

**Conclusions**
- Deep Reinforcement Learning can learn to play complex multi-player video games at human level
- Train populations (want diverse training signals) of agents to enable optimization and generalization 
- Use procedurally generated environments to produce robust, generalizable behaviors

### 3.Folding Proteins with AlphaFold
[AlphaFold: Improved proteins structure prediction using potentials from deep learning][ref-4] Using Deep Dilated Convolutional Residual Network

**Conclusions**
- Deep learning-based distance prediction
    - Gives more accurate predictions of contact between residues
    - A richer source of information than contact prediction
    - Constructs a smooth potential that is easy to optimize
- Limitations
    - Accuracy still limited
    - Method depends on finding homologous sequences
    - Only predicts backbone, side chains filled by external tool
- Work builds on decades of experimental and computational work of other researchers
- Deep Learning can deliver solutions to science & biology problems


[ref-1]:https://web.stanford.edu/class/psych209/Readings/MnihEtAlHassibis15NatureControlDeepRL.pdf

[ref-2]:https://science.sciencemag.org/content/362/6419/1140

[ref-3]:https://science.sciencemag.org/content/364/6443/859

[ref-4]:https://www.nature.com/articles/s41586-019-1923-7
