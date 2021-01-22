---
layout: post
title:  "Kernel Demystified"

date:   2020-04-23 
tags: theory

lang: en
---

The two most common use of kernel in statistics
+ a weighting function used in kernel density estimation to estimate the probability density function of a randim variable

+ kernel method/trick employed to [visualization][ref-4]

Let us first look at the definition from Wikipedia
A kernel is a non-negative real-valued integrable function K. For most applications, it is desirable to define the function to satisfy two additional requirements:

+ Normalization:
{\displaystyle \int _{-\infty }^{+\infty }K(u)\,du=1\,;}\int _{-\infty }^{+\infty }K(u)\,du=1\,;
+ Symmetry:
{\displaystyle K(-u)=K(u){\mbox{ for all values of }}u\,.}K(-u)=K(u){\mbox{ for all values of }}u\,.

Kernel methods owe their name to the use of kernel functions, which enable them to operate in a high-dimensional, implicit feature space without ever computing the coordinates of the data in that space, but rather by simply computing the inner products between the images of all pairs of data in the feature space. This operation is often computationally cheaper than the explicit computation of the coordinates. This approach is called the "kernel trick".

Several algorithms, such as Perceptron Algorithm, Suppport Vector Machines and Gaussian Processes, only use the inner products rather than the feature values.

Worried about not being able to linearly separate your data? Here's the panacea:
**m general points in an m-1 dimensional space is always linearly separable by a hyperplane**
If the kernel is positive semi-definite, then we can construct a feature map.

For the classification of a new object (x,y), we only have to evaluate
$$y\Sigma_{i=1}^m \alpha_i <x, x_i>$$

That is, we do not have to know the actual values of x--in other words--$$\phi(x)$$!

It is enough to know the inner products between the object and the training points.

How liberating!

Hilbert space

Now let us formally introduce kernel:

Given $$\phi: \mathcal {X} -> \mathcal {K}$$ feature mapping, the kernel is the corresponding inner product function. 

Then let us introduce a child of kernel: kernel technique:

$$G \in $$

Our problem is transformed to finding feature map $$\phi$$ and feature space $$\mathcal {K}$$.

Perceptron Algorithm:

A perceptron receives multiple inputs, applies various transformations and functions and provides an output. It models a neuron which has a set of inputs, each of which is given a specific weight.

initialize the weights and threshold
provide the input and calculate the output
update the weights
repeat steps 2 and 3
Kernel functions are at the basis of the kernel trick which allows many learning algorithms based on linear models to build nonlinear models easily. A kernel function takes two input vectors as arguments and returns a real value corresponding to the inner product of the images of these vectors in some feature space without having to actually map the points to the feature space.

Techincally, a kernel function is a positive definite function associated to a reproducing kernel Hilbert space (RKHS) which must fulfill the basic requirement of corresponding to the inner product of the images of its arguments in some feature space.

Common kernel functions include the linear kernel, the polynomial kernel and the Gaussian kernel. Other kernel functions can be constructed from these basic kernels.

References:

[Kernel Methods Wiki][ref-1]

[Kernel Methods][ref-2]

[An Interactive Journey into Machine Learning][ref-3]

[ref-1]:https://en.wikipedia.org/wiki/Kernel_method
[ref-2]:http://www.cs.cmu.edu/~aarti/Class/10701_Spring14/slides/kernel_methods.pdf
[ref-3]:https://mlweb.loria.fr/book/en/kernels.html
[ref-4]: https://www.youtube.com/watch?v=3liCbRZPrZA
