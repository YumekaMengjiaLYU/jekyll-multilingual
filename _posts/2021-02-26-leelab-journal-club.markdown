---
layout: post
title:  "Research Meeting Notes"
ref: welcome
date:   2021-02-26
tags: career
lang: en
---
The Combat+Neuroharmony family of algorithms for harmonizing multi-site neuroimaging data

https://www.sciencedirect.com/science/article/pii/S1053811920306133?via%3Dihub

https://www.sciencedirect.com/science/article/pii/S1053811919310419

Site and scanner effects in cortical thickness data

Original ComBat Algorithm

Harmonizing multi-site cross-sectional data

+ Methods for removing site effects

residuals harmonization
$$y_{ijv} = \alpha_v+ Z_{ij}^T\theta_v+\epsilon_{ijv}$$

Adjusted residuals harmonization
$$y_{ijv} = \alpha_v+ X_{ij}^T\beta_v+Z_{ij}^T\theta_v+\epsilon_{ijv}$$
 ComBat harmonization
$$y_{ijv} = \alpha_v+ X_{ij}^T\beta_v+Z_{ij}^T\theta_v+\delta_{iv}\epsilon_{ijv}$$
 Performance of ComBat
 Kolmogoro-Smirmov test

CovBat Algorithm
Harmonizing multi-site covariance effects for MVPA

Removing joint site effects for multivariate analyses

Harmonizing individual images from unseen scanners
machine learning models aimed at clinical translation where the focus is on the assessment of individual scans from previously unseen scanners. To overcome this challenge, we developed a tool that is capable of harmonizing single images from unseen/unknown scanners based on a set of image quality metrics, i.e. intrinsic characteristics which can be extracted from individual images without requiring a statistically representative sample

The tool was able to reduce scanner-related bias from unseen scans.

•
Neuroharmony represents a significant step towards imaging-based clinical tools.

Additional resources
ComBat for gene expression data

https://academic.oup.com/biostatistics/article/8/1/118/252073
•       ComBat for DTI

https://www.sciencedirect.com/science/article/pii/S1053811917306948
•       ComBat for CT

https://www.sciencedirect.com/science/article/pii/S105381191730931X
ComBat for fMRI
https://onlinelibrary.wiley.com/doi/full/10.1002/hbm.24241
•       Longitudinal ComBat

https://www.sciencedirect.com/science/article/pii/S1053811920306157
•       Non-linear GAM ComBat

https://www.sciencedirect.com/science/article/pii/S1053811919310419
•       CovBat

https://www.biorxiv.org/content/10.1101/858415v4
•       Neuroharmony

https://www.sciencedirect.com/science/article/pii/S1053811920306133
