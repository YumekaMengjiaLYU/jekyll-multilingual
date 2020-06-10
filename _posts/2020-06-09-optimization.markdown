---
layout: post
title:  "Lecture 5: Optimization for Machine Learning"
ref: welcome
date:   2020-06-09
tags: courses
lang: en
---
## 1.Intro and motivation

### Motivation

- Optimization algorithms are the basic engine behind deep learning methods that enable methods to learn from data by adapting their parameters.

- They solve the problem of the minimization of an objective function that measures the mistakes made by the model.
    - e.g. prediction error(classification), negative reward(reinforcement learning)

- Work by making a sequence of small incremental changes to model parameters that are each guaranteed to reduce the objective by some small amount.

### Basic notation

- Parameters
$$
\theta \in R^n
$$

- Real-valued objective function
$$
h(\theta)
$$

- Goal of optimization
$$
\theta^* = argmin h(\theta)
$$

### Example: neural metwork training objective
- The standard neural network training objective is given by:

$$
h(\theta)=\frac{1}{m} \sum_{i=1}^m \ell(y_i, f(x_i, \theta))
$$
## 2.Gradient descent
### Gradient descent: definition
- Basic gradient descent iteration:
$$
\theta_{k+1} = \theta_k - \alpha_k \nabla h(\theta_k)
$$

### Intuition: gradient descent is "steepest descent"

- Gradient direction $\nabla h(\theta_k)$ gives greatest reduction in $h(\theta_k)$ per unit of change in $\theta$.

- If $\nabla h(\theta_k)$ is "sufficiently smooth", and learning rate small, gradient will keep pointing down-hill over the region in which we take our step.

### Intuition: gradient descent is minimizing a local approximation

- 1st-order Taylor series for around current $\theta$ is

- For small enough d this will be a reasonable approximation

- Gradient update computed by minimizing this within a sphere of radius r

### The problem with gradient descent
High - diverge
Low - Converge very slowly

### Convergence theory: technical assumptions
- has Lipchistz continuous derivatives

- is strongly convex (perhaps only near minimum) 
$$
h \geq 
$$
- For now: gradients are computed exactly (i.e. without approximations/not stochastic)

### Convergence theory: upper bounds
If previous conditions hold and we take 

Number of iterations 

### Convergence theory: useful in practice?

- Issues with bounds such as this one:
    - too pessimistic (they must cover worst-case examples)
    - Some assumptions too strong (e.g. convexity)
    - Other assumptions too weak (real problems have additional useful structure)
    - Rely on crude measures of objective (e.g. condition numbers)
    - Usually focused on asymptotic behavior (do care how quickly you are getting to a point preaymptotically)

- The design/choice of an optimizer should always be informed by practice more than anything else. But theory can help guide the way and build intuitions.
## 3.Momentum methods

### The momentum method
- Motivation
    - the gradient has a tendency to flip back and forth as we take steps when the learning rate is large
    - e.g. the narrow valley
- The key idea:
    - accelerate movement along directions that point consistently down-hill across many consecutive iterations (i.e. have low curvature)
- How?
    - treat current solution for like a ball rolling along a surface whose height is given by, subject to the force of gravity

### Defining equations for momentum
- Classical Momentum
- Nesterov's variant

### Narrow 2D valley example revisited

### Upper bounds for Nesterov's momentum variant

### Convergence theory: 1st-order methods and lower bounds
- A first-order method is one where updates are linear combinations of observed gradients. 

- included:
    - gradient descent
    - momentum methods
    - conjugate gradients

- not included:
    - preconditioned gradient descent/2nd-order methods

### Lower bounds

No major algorithmic improve ment

### Comparison of iteration counts
To achieve $h(\theta_k)-h(\theta*) \geq \epsilon$, the number of iterations k satisfies:
- (Worst case) lower bound for 1st-order methods
$$
\kappa \in \omega
$$
- Upper bound for gradient descent
- Upper bound for GD w/ Nesterov's momentum
## 4.2nd-order methods
### The problem with 1st-order methods
- **Dependency on global condition number**:For many 1st-order method, the number of steps needed to converge grows with "condition number":

$$
\kappa = \frac{Max curvature}{Min curvature}=\frac{L}{\mu}
$$

- **Depend on the problem**:This will be very large for some problems (e.g. certain deep architecture)
- 2nd-order methods can improve (or even eliminate) this dependency on kappa

### Derivation of Newton's method
- Approximate h(\theta) by its 2nd-order Taylor series around current \theta:

$$
h(\theta + d) h(\theta) + \nabla h(\theta) d + 
$$

- Minimize this local approximation to obtain
$$
d = -H(\theta) \nabla h(\theta)
$$

- Update current iterate with this
$$
\theta_{k+1} = \theta_{k} - H(\theta)^{-1}\nabla h(\theta_{k})
$$

**In practice people still use momentum for 2nd-order**

### Comparison to gradient descent
- Max allowable global learning rate for GD to avoid divergence:

- Gradient descent implicitly minimizes a bad approximation of 2nd-order Taylor series:

$$
h(\theta+d) \approx h(\theta) + \nabla h(\theta)^\top d + \frac{1}{2} d^\top H(\theta)d
$$

Subsitute Hessian with LI
The curvature is maximum every where

- LI is too pessimistic/conservative an approximation of the Hessian! It treats all directions as having max curvature.
## 5.Stochastic optimization