---
layout: post
title:  "Attention and Memory in Deep Learning"
ref: welcome
date:   2020-07-05
tags: deep-learning-lectures
lang: en
---


The course slides:

<iframe src="https://storage.googleapis.com/deepmind-media/UCLxDeepMind_2020/L8%20-%20UCLxDeepMind%20DL2020.pdf" width="100%" height="500em"></iframe>

Attention is about igonoring things. It is about putting more things in the neural network; removing information so it is possible to focus on specific parts.

They respond more strongly to some parts to others. ignore irrelevant detail in the background

matrix of partial derivatives:
sensitivity of the network outputs with respect to the inputs

The back prop calculation that's used for gradient descent can be repurposed to analyse the sensitivity of the network.

Instead of passing through the errors with respect to some loss function, you set the error equal to output activations themselves, then perform back prop

What pieces of info the network is really focusing on

### Duelling Network
network that is applied to play Atari games and the input is video sequence.

output two headed
one head attempts to predict  the value of the state, as is kind of normal for RL,

tHE other head attemps to predict the action advantage - the differential givewhether a particular action would make value higher
tje degree over expectation over other actions
racing game: overtake as many cars as possible

Even for the same data, we get a very different sensitivity pattern depending on which tasks we are trying to perform.

The attention mechanism is allowing it to process the same data in two very different ways.

Attention allows you to ignore some parts of the data and focus on others.

### Recurrent Networks
Take sequences as input
output sequences

feedback connection that agive them memory about 

Memory can be thought as attention through time.

How are they using the memory to solve the task?

sequential jacobian: instead of  2d matrix o f  partial deri
3d matrix where the 3rd dimension is time

What we care about mostly is how sensitive is the network

If we look at the sequential Jacobian, we can see there is a peak sensitivity aorund here  which roughly corresponds to  letter i is written.

It doesn't extend so far back and

"-ing" is common helps to disambiguous

lifed the pen off page and put the dot
network is sensitive to that point

quantifiable sense of the degree to which it is using the information

### Machine Translation

Words may appear in a completely different order in a different language.

## Explicit Attention

- Computational efficiency
    - no need to process the data; save

- Scalability
    - take a fixed size part of an image-can scale to any sized image so that the resolution of input does not alter the architecture of network

- sequential
    - foveal gaze moving around a static image
    - a sequence of sensory inputs
    - doing this can improve robustness 
    - network with sequences of gllimpse/foveal were more robust to adversarial examples than ordinary cnns that looked at entire image

- Interpretability
    - require making a hard decision and choose part of data to look data
    - can analyze a bit more clearly what the network is actually using
    - implicit: use Jacobian as a guide-not necessarily a reliable signal

A loop is going on that influences the data it receives

Even if the network itself is feedforward, the system if recurrent.

It contains loop!

Define a probability distribution over glimpse.

attention vector a

simplest case: split to each piles softmax outputs are probabilities of picking each tile

HARD DECISION: no longer have the complete gradient as to what the network has done; we've got a stochastic policy, in RL terms, we are sampling

how to get a gradient with respect to discreet samples using REINFORCE

RL methods, designed for getting a training signal trhough discrete policy

anytime there is a non-differentiable module in there

using hard attention vs implicit attention present in nn

generally we want to something more complex than softmax over piles

### Complex Glimpses

squashed down

mimicking the effect of human eye
high resolution at the center of gaze
informaiton at proper is sufficient to  alert ou to somthign 

find digit in clutter

scalability
a sequential glimpse is more scalable is that you can use it, to represent multipile objects

multiple number from street address.

the  network moves its attention around really important parts  of 
indication what parts image

## Soft Attention
makes end to end training possible


have all the data and just need to make a decision on what to focus on what not; no need to make a decision

