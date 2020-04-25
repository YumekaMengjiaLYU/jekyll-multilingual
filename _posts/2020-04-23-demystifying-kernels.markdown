---
layout: post
title:  "Kernel Demystified"
ref: welcome
date:   2020-04-23 
categories: career
lang: en
---

Let $${\displaystyle {\mathcal {X}}}{\displaystyle {\mathcal {X}}}$$ be a nonempty set, sometimes referred to as the index set. A symmetric function $${\displaystyle K:{\mathcal {X}}\times {\mathcal {X}}\to \mathbb {R} }{\displaystyle K:{\mathcal {X}}\times {\mathcal {X}}\to \mathbb {R} }$$ is called a positive definite (p.d.) kernel on $${\displaystyle {\mathcal {X}}}{\mathcal {X}}$$ if

$${\displaystyle \sum _{i=1}^{n}\sum _{j=1}^{n}c_{i}c_{j}K(x_{i},x_{j})\geq 0\quad \quad \quad \quad (1.1)}{\displaystyle \sum _{i=1}^{n}\sum _{j=1}^{n}c_{i}c_{j}K(x_{i},x_{j})\geq 0\quad \quad \quad \quad (1.1)}$$

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

Now let us formally introduce kernel:

Given $$\phi: \mathcal {X} -> \mathcal {K}$$ feature mapping, the kernel is the corresponding inner product function. 

Then let us introduce a child of kernel: kernel technique:

$$G \in $$

Our problem is transformed to finding feature map $$\phi$$ and feature space $$\mathcal {K}$$.

Perceptron Algorithm:
$$
\begin{algorithm}[H]
\SetAlgoLined
\KwResult{Write here the result }
 initialization\;
 \While{While condition}{
  instructions\;
  \eIf{condition}{
   instructions1\;
   instructions2\;
   }{
   instructions3\;
  }
 }
 \caption{How to write algorithms}
\end{algorithm}$$

References:

[Kernel Methods Wiki][ref-1]

[Kernel Methods][ref-2]

[ref-1]:https://en.wikipedia.org/wiki/Kernel_method
[ref-2]:http://www.cs.cmu.edu/~aarti/Class/10701_Spring14/slides/kernel_methods.pdf