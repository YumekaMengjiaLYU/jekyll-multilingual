---
layout: post
title:  "Neural Networks Foundations"
ref: welcome
date:   2020-06-05
tags: courses
lang: en
---
## 1.Overview

### What are the areas of application?
- Computer vision
- Text and Speech
- Control
### What's made all this possible?
- Compute
    - specific hardware GPU that's much faster with respect to very specifiic operations matrix multiplication on which neural networks rely 
- Data
    - There is much more data available 
    - Models that are data hungry and improve as the amount of data increases
- Modulartiy
    - Modular blocks that can be arranged in various ways

### The deep learning puzzle
All that DL researchers are doing is building the small blocks that can be interconnected in various ways so that they jointly process data
> Deep Learning is constructing networks of parameterized functional modules & training them from examples using gradient-based optimization. - Yann LeCun

**Each of the computation units(nodes) needs to know**
- How to adjust this input, if my output needs to change?
- What to output?

## 2.Neural Networks
### Basics
#### Real neuron
> Human brain is estimated to contain around 86,000,000,000 of such neurons. Each connected to even thousands others.

- Connected to others
- Represents simple computation
- Has inhibition and excitation connections
- Has a state
- Outputs spikes
#### Artificial neurons
> The goal of simple artificial neurons models is to reflect some neurophysiological observations, not to reproduce their dynamics.

- Easy to compute
- Represents simple computation
- Has inhibition and excitation connections
- Stateless w.r.t time
- output real values rather than spikes through time
#### Linear layer
> In Machine Learning linear really means affine. Neurons in a layer are often called units. Parameters are often called weights.

- Easy to compute
- Collection of artificial neurons
- Can be efficiently vectorized
- Fits highly optimized hardware (GPU/TPU)
Matrix multiplication of 2 matrices in a naive fashion is cubic, and can be made more efficient by using divide and conquer that fits the GPU paradigm extremely well.
### Single layer neural networks
#### Sigmoid activation function
> Activation functions are often called non-linearities and are applied point-wise.

- Introduces non-linear behavior
- Produces probability estimate
- Has simple derivatives
- Saturates (once saturates, want to be told how to adjust weights any more)
- Derivatives vanish (gradients far to the left and right approach 0)
#### Cross entropy
> Cross entropy loss is also called negative log likelihood or logistic loss

- Encodes negation of logarithm of probability of correct classification
- Composable with sigmoid
- Numerically unstable

> Being addictive over samples allows for efficient learning.
Losses that have the form can be trained with stochastic gradient descent and can scale very well with big datasets.

#### Softmax 
**A smooth version of the maximum operation**
> Softmax is the most commonly used final activation in classification. 

> It can also be used to have a smooth version of maximum.

- Multi-dimensional generalization of sigmoid
- Produces probability estimate
- Has simple derivatives
- Saturates
- Derivatives vanish

#### Softmax + Cross entropy
> Widely used not only in classification but also in RL. Cannot represent sparse outputs(sparsemax). Does not scale too well with k- number of classes.

- Encodes negation of logarithm of probability of entirely correct classification
- Equivalent of multinomial logistic regression model
- Numerically stable combination
- Not scale well with 

Highly dimensional spaces are surprisingly easy to shatter with hyperplanes.

**Limitation: Linear models cannot do XOR**

### Two layer neural networks
 
#### 1-hidden layer network VS XOR
> Hidden layer provides non-linear input space transformation so that final linear layer can classify
The hidden layer is used to rotate and then slightly bend the input space with the sigmoid, and preprocess the data so that it becomes linearly separable.
- With just 2-hidden neurons we solve XOR
- Hidden layer allows us to bent and twist input space
- We use linear model on top, to do the classification
What makes it possible for neural networks to learn arbitrary shapes?

#### Universal Approximation Theorem
> For any continuous function from a hypercube [0,1] to real numbers, and every positive epsilon, there exists a sigmoid based, 1-hidden layer neural network that obtains at most epsilon error in functional space.

Big enough network can approximate, but not represent any smooth function. The math trick is to show that networks are dense in the space of target functions.

- One of the most important theoretical results for Neural Networks
- Shows that they are extremely expressive
- Tells us nothing about learning (how to learn them)
- Size of network grows exponentially

### Deep neural networks
#### Rectified Linear Unit (ReLU)
> One of the most commonly used activation functions. Made math analysis of networks much simpler.

- Introduces non-linear behavior
- Creates piece-wise linear functions
- Derivatives do not vanish
- Dead neurons can occur
- Technically not differentiable at 0

#### Depth
> Number of linear regions that are created by ReLU grows exponentially with depth and polynomially with width.

- Expressing symmetries and regularities is much easier with deep model than wide one.
- Deep model means many non-linear composition and thus harder learning.
Why depth really matters?
ReLU networks can be seen as a method to keep folding the input space on top of each other, which has two effe
-
- One way to represent symmetry. That only depth can give you. Would need exponential many neurons to represent the same invariance. (why depth really matters)
### Neural networks as computational graphs
Extremely flexible: There is no difference between weight or input into a node in a computational graph. Can substitute weight with another network.  
## 3.Learning
### Linear algebra recap
Gradient/Jacobian
### Gradient descent recap
> Choice of learning rate is critical. Main learning algorithm behind deep learning. Many modifications: Adam, RMSProp, ...

**Gradients of the sum is the sum of the gradients.**
- Works for any "smooth enough" function
- Can be used on non-smooth targets but with less guarantee
- Converges to local optimum (guaranteed when smooth)

### Neural networks as computational graphs - API
- Forward pass: Given input, what is the output?
- Backward pass: Jacobian with respect to input

### Gradient descent and computational graph
### Chain rule, backprop and automatic differentiation
### Linear layer as a computational graph
> Backward pass is a computational graph itself.

### ReLU as a computational graph
> We usually put gradient in 0 to be equal to 0.

- Can be seen as gating the incoming gradients. The ones going through neurons that were active are passed through, and the rest zeroed.

### Softmax as a computational graph
> Since exponents of big numbers will cause overflow, it is rarely explicitly written like this.

- Backwards pass is essentially a difference between incoming gradient and output.
### Cross entropy as a computational graph
> Though it is a loss, we could still multiply its backwards by another incoming errors.

Each of these operations on its own is numerically unstable and numerically stable solutions are desired. Each of these combinations is implemented in a way that is numerically stable, and all we need to do is to pick the combination you want from the lookup table.   
composing cross entropy with either Sigmoid or Softmax.

work  with any kind of neural network
relies on 
keep composing around  the same algorithm 
 optimization method that is going to converge to some local minimum
not necessarily a perfect model but it's gonna learn something
## 4. Pieces of the Puzzle
### Max as a computational graph
> Used in max pooling.

- Gradients only flow through the selected element. Consequently we are not learninig how to select.

### Conditonal execution as a computational graph
- Backwards pass is gated in the same way forward one is
- We can learn conditionals themselves too, just use softmax.


## 5.Practical Issues
### Overfitting and regularization
> Classical results from statistics and statistical learning theory which analyses the worst case scenario.

**Techniques**
- Lp regularization
- Dropout
- Noising data
- Early stopping
- Batch/Layer Norm

- As your model gets more powerful, it can create extremely complex hypotheses, even if they are not needed.
- Keeping things simple guarantees that if the training error is small, so will the test be.
- As models grow, their learning dynamics changes, and they become less prone to overfitting.
- New, exciting theoretical results, also mapping these huge networks onto Gaussian Processes.

> Model complexity is not as simple as number of parameters.

- Even big models still can benefit from regularization techniques.
- We need new notions of effective complexity of our hypotheses classes
### Diagnosing and debugging
- Initialization
    - Won't learn well for bad
- Overfit small sample
- Monitor training loss
- Monitor weights norms and NaNs
- Add shape asserts
- Start with Adam (3e-5 is a magical learning rate :) )
- Change one thing at the time
## 6.Multiplicative Interactions
### What MLPs cannot do?
#### Multiplicative interactions
> Being able to approximate something is not the same as represent it.

- Multiplicative units unify attention, metric learning and many others.
- They enrich the hypothesis space of regular neural networks in a meaningful way.

> If you want to do research in fundamental building blocks of Neural Networks, do not seek to marginally improve the way they behave by finding new activation function.

> Ask yourself what current modules cannot represent or guarantee right now, and propose a module that can.