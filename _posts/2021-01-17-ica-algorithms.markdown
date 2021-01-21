---
layout: post
title:  "fastICA and cICA"
ref: welcome
date:   2021-01-17
tags: career
lang: en
---

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

## Time-frequency Analysis
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