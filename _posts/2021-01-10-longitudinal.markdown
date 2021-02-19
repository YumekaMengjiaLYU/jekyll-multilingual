---
layout: post
title:  "What I Learned In My Longitudinal Analysis Class"
ref: welcome
date:   2021-01-10
tags: career
lang: en
---
As I put a lot of time in my internship, I ultimately changed the grading option for this class to Pass/Fail. For this reason, I did not put enough efforts needed in this class. As a makeup, I'd like to summarize the most important things I have learnt in this class.

### Definition
A Longitudinal study refers to an investigation where participants outcomes and possibly treatments or exposures are collected at multiple follow-up times.

+ Linear mixed models permit regression analysis with correlated Data

+ Mixed models specify variance components that represent within-subject variance in outcomes, and between-subject variation in trajectories

+ Linear mixed model parameters can be obtained using maximum likelihood

+ GEE permits regression analysis with correlated continuous, binary, or count Data

+ GEE requires specification of a regression model and a working correlation models

+ Two standard error estimates are provided with GEE: a model-based standard error that is valid if the correlation model is correctly specified; and an empirical standard errors which are valid even if the correlation model is not correct provided the data contain a large number of independent clusters

+ Estimation with GEE does not involve a  likelihood function, rather it is based on the solution to regression equations that only use models for the mean and covariance

### Approaches to Analysis with Missing Data

+ Imputation

Proper methods of imputation use multiple imputation to account for the uncertainty in the missing data. Imputation methods require that a model be adopted that links the missing data to the required data.

+ Modeling
Modeling of both the missing data process and the longitudinal data use maximum likelihood for estimation.

Use of linear mixed models estimated with maximum likelihood is one example of the approach.
To validly correct for MAR missingness, the mean and the covariance must be correctly specified.

+ Weighting

Weight the available data using non-response methods to weight the observed data in order to account for the missing data. Use of inverse probability weighting, or non-response weighting can be applied to general statistical summaries.

However, it is important to note that these methods are designed to address
data that are assumed to be MAR rather than the more serious non-ignorable
(NI) missing data. Non-ignorable missing data can lead to bias which can
not be corrected simply through modelling and estimation of the drop-out
model and/or the response model since unidentifiable parameters that link
the probability of missingness to the unobserved data are needed. Therefore,
reliance on statistical methods to correct for bias due to attrition either requires an untestable assumption that the data are MAR, or requires some
form of sensitivity analysis to characterize plausible estimates based on various missingness assumptions.
