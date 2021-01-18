---
layout: post
title:  "fastICA and cICA"
ref: welcome
date:   2021-01-17
tags: career
lang: en
---


## Whittle likelihood

Whittle likelihood is an approximation to the likelihood function of a stationary Gaussian time series, and is commonly used in time series analysis and signal processing for parameter estimation and signal detection.


Let {\displaystyle X_{1},\ldots ,X_{N}}X_1,\ldots,X_N be a stationary Gaussian time series with (one-sided) power spectral density {\displaystyle S_{1}(f)}{\displaystyle S_{1}(f)}, where {\displaystyle N}N is even and samples are taken at constant sampling intervals {\displaystyle \Delta _{t}}\Delta_t. Let {\displaystyle {\tilde {X}}_{1},\ldots ,{\tilde {X}}_{N/2+1}}{\displaystyle {\tilde {X}}_{1},\ldots ,{\tilde {X}}_{N/2+1}} be the (complex-valued) discrete Fourier transform (DFT) of the time series. Then for the Whittle likelihood one effectively assumes independent zero-mean Gaussian distributions for all {\displaystyle {\tilde {X}}_{j}}{\displaystyle {\tilde {X}}_{j}} with variances for the real and imaginary parts given by

{\displaystyle \operatorname {Var} \left(\operatorname {Re} ({\tilde {X}}_{j})\right)=\operatorname {Var} \left(\operatorname {Im} ({\tilde {X}}_{j})\right)=S_{1}(f_{j})}{\displaystyle \operatorname {Var} \left(\operatorname {Re} ({\tilde {X}}_{j})\right)=\operatorname {Var} \left(\operatorname {Im} ({\tilde {X}}_{j})\right)=S_{1}(f_{j})}
where {\displaystyle f_{j}={\frac {j}{N\,\Delta _{t}}}}{\displaystyle f_{j}={\frac {j}{N\,\Delta _{t}}}} is the {\displaystyle j}jth Fourier frequency. This approximate model immediately leads to the (logarithmic) likelihood function

Once (4) is available, we maximize it to obtain the estimates
of the unmixing matrix W and the parameters in the power
spectra of the sources (see Section 2.3). The maximum Whittle
likelihood approach can be interpreted as assigning a different
weight of (e
j W) · (Wej)/fjj(rk) to the source periodogram  ̃f
at the Fourier frequency rk. This procedure will be referred to
as cICA hereafter,
AR models are the most

commonly used time series approaches for the temporal corre-
lation structure in fMRI analysis.