---
layout: post
title:  "All About ICA"
ref: welcome
date:   2021-01-17
tags: career
lang: en
---

For my practicum, I am working with fMRI data. Two algorithms that I've come across is normal ICA and fast ICA.

For example, principal components analysis (PCA)
finds a set of components that are orthogonalto one another in multidimensional
space, whereas independent components analysis (ICA) finds a set of components
that are independent of one another. 

## PCA
[Video][ref-2]
[PCA ICA][ref-3]
## ICA
The definition is copied from the [paper][ref-1]
$$ X_{M \times T} = A_{M \times M}S_{M \times T}$$

+ X is a random p-vector representing miltivariate input measurements

+ S is a latent source p-vector whose components are independently distributed random variables

+ A is a $p \times p$ full-rank non-randomm mixing matrix

+ estimate the unmixing matrix $W = A^{-1}$ such that $\hat S = \hat W X$ is the estimate of $S$

The goal of ICA is to recover the latent source signals as

$$S = WX$$ with $$W = A^{-1}$$

### Assumptions

#### Independence

+ two variables are independent if and only if the joint pdf is factorizable in the following way
$$p(s_1,s_2) = p(s_1)p(s_2)$$

+ $$$$

#### Non-Gaussian

+ the distribution of any orthogonal transformation of the Gaussian has the same distributino as

+ if R is some arbitrary orthogonal matrix so that

### Measure of Non-gaussianity

For ICA estimation, we need to have a quantitative measure of non-gaussianity

+ Kurtosis

+ Entropy

+ Negative entropy

+ Approximation

### Caution and Limitation

#### Scaling

#### Signal Permutations

The order of mixing matrix and independent components are unknown

#### Number of Sensors

+ The number of separated signals cannot be larger than the number of inputs

+ Current research is being done to reduce the constraint

### ICA IN fMRI

+ Rely on the intrinsic structure of data

+ No assumptions about the form of the or the possible causes of responses are made

+ The only assumption is mutual independence in space for spatial ICA or in time for temporal ICA

### Temporal ICA

+ Components have independent temporal dynamics: 
Strength of one component at a particular moment in time does not provide information on the strength of other components at that moment

+ Components may be correlated in space

+ Popular for cocktail party problem or EEG

### Spatial ICA

+ Components have independent spatial distributions

"Strength of one component in particular voxel does not provide information on the strength of other components in that voxel"

+ Components may be correlated in time

+ Popular for fMRI

### Remarks

+ fastICA has built in prewhitening

+ the algorithm is stochatic

+ a lot of ICA algorithms are designed to have random initialization like k-means. They often gives similar answers, but not always.

## FastICA
From Wiki:

FastICA is an efficient and popular algorithm for independent component analysis invented by Aapo Hyvärinen at Helsinki University of Technology. Like most ICA algorithms, FastICA seeks an orthogonal rotation of prewhitened data, through a fixed-point iteration scheme, that maximizes a measure of non-Gaussianity of the rotated components. Non-gaussianity serves as a proxy for statistical independence, which is a very strong condition and requires infinite data to verify. FastICA can also be alternatively derived as an approximative Newton iteration.
### Definition

## Wavelet Analysis

Fourier transform is a powerful tool, but it does not represent abrupt changes efficiently.

Fourier transform represents data as a sum of sine waves which are not localized in time or space domain.

To accurately analyze signals and images that have abrupt changes, we need to use a new class of functions that are well localized in time and frequency.

A wavelet is a rapidly decaying, wave-like oscillation that has zero mean. Unlike sinusoids, which extend to infinity, a wavelet exists for a finite duration.

+ Morlet
+ Daubechies
+ Coiflets
+ Biorthogonal
+ Mexican Hat
+ Symlets
This is because, unlike the sinewave, the wavelet has a band pass characteristic in the frequency domain. Mathematically, the equivalent frequency is defined using this equation 
$$F_{eq}=\frac{C_f}{s\delta_t}$$
, where Cf is center frequency of the wavelet, s is the wavelet scale, and delta t is the sampling interval.

 A stretched wavelet helps in capturing the slowly varying changes in a signal while a compressed wavelet helps in capturing abrupt changes. 

 We need to shift the wavelet to align with the feature we are looking for in a signal

  Key applications of the continuous wavelet analysis are: time frequency analysis, and filtering of time localized frequency components. The key application for Discrete Wavelet Analysis are denoising and compression of signals and images.

  Analytic wavelets are best suited for time frequency analysis as these wavelets do not have negative frequency components.  This list includes some analytic wavelets that are suitable for continuous wavelet analysis.  
## Whittle likelihood

Whittle likelihood is an approximation to the likelihood function of a stationary Gaussian time series, and is commonly used in time series analysis and signal processing for parameter estimation and signal detection.



Once (4) is available, we maximize it to obtain the estimates
of the unmixing matrix W and the parameters in the power
spectra of the sources (see Section 2.3). The maximum Whittle
likelihood approach can be interpreted as assigning a different
weight of (e
j W) · (Wej)/fjj(rk) to the source periodogram  ̃f
at the Fourier frequency rk. This procedure will be referred to
as cICA hereafter,


Limitations of static spectral analysis
It is visually interpretable only for stationary signals

We want to combine the temmporal precision but also want to ectract frequency specific information over time

One of the main way to do t-f anlysis is wavlet convolution

## Time-frequency Analysis

They taper to 0 at the beginning and the end.

Integrate to 0

Where do wavelets come from?

Why wavelets provide temporal specificity?
Fourier transform: dot product with this kernel

Morlet convolution: dot product with the kernel

Morlet wavelets in time and in frequency

+ in frequency domain the amplitude spectrum is a Gaussian

Convolution
+ in the time domain
should avoid using convolution in the time domain as it is very slow
for conceptual purposes

goal take two time series and mix them together to create a signal
in general signal is the thing you are interested in ; the kernel is the filter that you apply
+ in the frequency domain

In signal processing, time–frequency analysis[3] is a body of techniques and methods used for characterizing and manipulating signals whose statistics vary in time, such as transient signals.

It is a generalization and refinement of Fourier analysis, for the case when the signal frequency characteristics are varying with time. Since many signals of interest – such as speech, music, images, and medical signals – have changing frequency characteristics, time–frequency analysis has broad scope of applications.



## Independent Component Analysis
The Amari distance is a measure between two nonsingular matrices, useful for checking for convergence in independent component analysis algorithms and for comparing solutions.

$$X_1 = a_{11}S_1+a_{12}S_2 +\cdot +a_{1p}S_p$$
$$X_2 = a_{21}S_1+a_{22}S_2 +\cdot +a_{2p}S_p$$

$$X_p = a_{p1}S_1+a_{p2}S_2 +\cdot +a_{pp}S_p$$

S_l are assumed to be statistically independent


A real Morlet wavelet could be defined as the product of a complex sine wave and a Gaussian window:

$$M(t) = exp^{-t^2/\sigma^2} cos(2\pi \gamma t)$$
AR models are the most

commonly used time series approaches for the temporal corre-
lation structure in fMRI analysis.
### PCA and SVD

As a final remark, let’s discuss the numerical advantages of using SVD. A basic approach to actually calculating PCA on a computer would be to perform the eigenvalue decomposition of directly. It turns out that doing so would introduce some potentially serious numerical issues that could be avoided by using SVD.
### Whitening

Whitening can be used to easily alleviate the effects of coordinates given in different units. 

One of the important assumptions of the GLM, is that the elements of the error vector, are uncorrelated, Cor(i, j) = 0
for i = j and that they all have the same variance, Var(
i) = σ2 for all i. 

There are many cases when this assumption is violated. For example, imagine that the dataset
on age and processing speed included sets of identical twins; in this case, some
individuals will be more similar than others. More relevant to fMRI, this can also
occur when the dependent variable Y includes temporally correlated data. When
this occurs, the distribution of the error is given by Cov() = σ2V, where V is the
symmetric correlation matrix and σ2 is the varaince.
The most common solution to this problem is to prewhiten the data, or to remove
the temporal correlation. 

[ref-1]:https://www.tandfonline.com/doi/abs/10.1198/jasa.2011.tm10332
[ref-2]:https://www.youtube.com/watch?v=kw9R0nD69OU
[ref-3]:http://compneurosci.com/wiki/images/4/42/Intro_to_PCA_and_ICA.pdf