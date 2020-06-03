---
layout: post
title:  "Deep Learning Lectures: Intro to Machine Learning & AI"
ref: welcome
date:   2020-06-03
tags: courses
lang: en
---

## Solving Intelligence
### What is intelligence?
The hallmark of human intelligence lies in its generality, as science fiction author Robert Heinlein puts it,  _"specialization is for insects"_. 
Shane Legg's definition of the measure:
>Intelligence measures an agent's ability to achieve goals in a wide range of environments.


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
[Human-level control through deep reinforcement learning][ref-1]
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
## AlphaGo&Alpha Zero

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

Initialized with a policy and value network, AlphaZero plays by evaluating the search tree from a given position making its best move. So on and so forth

train value network
put these new in the 
generate better moves, n
AlphaZero plays game against itself
New policy/value network is used in ne

Discover chess opening thoery 

Conclusions:
- Deep Learning enables us to search the huge search space of complex board games.
- Self-play produces large amounts of data necessary for training the deep neural networks.
- Self-play provides an **automatic curriculum**, starting from simple opponents to stronger and stronger opponents. (training against itself)
- System discovers new knowledge.
- New directions: Learn rules of the game, more than two players, imperfect information, larger action spaces etc.

## Learning to Play Capture the Flag
Human-level performance in 3D multiplayer games with population-based reinforcement learning
ogjective game wehre multiple agents need to learn to interact to play
large-scale decentralized multi-agent learning problem

- population-based training 
- Internal reward evolution
- Hierarchical temporal policies
- Agents exceed human-level, as both teammates and opponents
- Rich emergent representation and behavior

Rul pick up flag bring it to your own base, have to make sure your own flag is at base not stolen.

procedual generation
every game a new map
Training Procedure
- Train a population of agents
- CTF games played by bringing together agents from population for an episode
- Individual streams of experience sent back to participating agents
- Each agent trains with independent RL, independent actions, no global information.

Neural Network Architecture
- Hierarchy of recurrent neural networks at two time scales: Slow and Fast RNN
- Internal rewards based on game events learned at even slower time scale

Conclusions
- Deep Reinforcement Learning can learn to play complex multi-player video games at human level
- Train populations of agents to enable optimization and generalization
- Use procedurally generated environments to produce robust, generalizable behaviors.
We can now begin to understand how agent act and why

## Folding Proteins with AlphaFold
AlphaFold: Improved proteins structure prediction using potentials from deep learning

Using Deep Dilated Convolutional Residual Network

Conclusions
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

