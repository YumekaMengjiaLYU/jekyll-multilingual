---
layout: post
title:  "Kernels Demystified"
ref: welcome
date:   2020-04-23 
categories: career
lang: en
---

Let $${\displaystyle {\mathcal {X}}}{\displaystyle {\mathcal {X}}}$$ be a nonempty set, sometimes referred to as the index set. A symmetric function $${\displaystyle K:{\mathcal {X}}\times {\mathcal {X}}\to \mathbb {R} }{\displaystyle K:{\mathcal {X}}\times {\mathcal {X}}\to \mathbb {R} }$$ is called a positive definite (p.d.) kernel on $${\displaystyle {\mathcal {X}}}{\mathcal {X}}$$ if

$${\displaystyle \sum _{i=1}^{n}\sum _{j=1}^{n}c_{i}c_{j}K(x_{i},x_{j})\geq 0\quad \quad \quad \quad (1.1)}{\displaystyle \sum _{i=1}^{n}\sum _{j=1}^{n}c_{i}c_{j}K(x_{i},x_{j})\geq 0\quad \quad \quad \quad (1.1)}$$
holds for any $${\displaystyle x_{1},\dots ,x_{n}\in {\mathcal {X}}}{\displaystyle x_{1},\dots ,x_{n}\in {\mathcal {X}}}, given {\displaystyle n\in \mathbb {N} ,c_{1},\dots ,c_{n}\in \mathbb {R} }{\displaystyle n\in \mathbb {N} ,c_{1},\dots ,c_{n}\in \mathbb {R} }$$.

Kernel methods owe their name to the use of kernel functions, which enable them to operate in a high-dimensional, implicit feature space without ever computing the coordinates of the data in that space, but rather by simply computing the inner products between the images of all pairs of data in the feature space. This operation is often computationally cheaper than the explicit computation of the coordinates. This approach is called the "kernel trick".