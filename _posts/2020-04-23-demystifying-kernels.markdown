---
layout: post
title:  "Kernel Demystified"

date:   2020-04-23 
tags: career
categories: 
- career
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

Hilbert space

Now let us formally introduce kernel:

Given $$\phi: \mathcal {X} -> \mathcal {K}$$ feature mapping, the kernel is the corresponding inner product function. 

Then let us introduce a child of kernel: kernel technique:

$$G \in $$

Our problem is transformed to finding feature map $$\phi$$ and feature space $$\mathcal {K}$$.

Perceptron Algorithm:

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
<pre id="quicksort" style="display:hidden;">
    % This quicksort algorithm is extracted from Chapter 7, Introduction to Algorithms (3rd edition)
    \begin{algorithm}
    \caption{Quicksort}
    \begin{algorithmic}
    \PROCEDURE{Quicksort}{$A, p, r$}
        \IF{$p < r$} 
            \STATE $q = $ \CALL{Partition}{$A, p, r$}
            \STATE \CALL{Quicksort}{$A, p, q - 1$}
            \STATE \CALL{Quicksort}{$A, q + 1, r$}
        \ENDIF
    \ENDPROCEDURE
    \PROCEDURE{Partition}{$A, p, r$}
        \STATE $x = A[r]$
        \STATE $i = p - 1$
        \FOR{$j = p$ \TO $r - 1$}
            \IF{$A[j] < x$}
                \STATE $i = i + 1$
                \STATE exchange
                $A[i]$ with $A[j]$
            \ENDIF
            \STATE exchange $A[i]$ with $A[r]$
        \ENDFOR
    \ENDPROCEDURE
    \end{algorithmic}
    \end{algorithm}
</pre>

<script>
    pseudocode.renderElement(document.getElementById("quicksort"));
</script>
