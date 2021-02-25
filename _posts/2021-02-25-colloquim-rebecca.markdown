---
layout: post
title:  "Department Colloquium by Dr. Rebecca Hubbard Notes"
ref: welcome
date:   2021-02-25
tags: career
lang: en
---

Title: Accounting for Data Provenance in EHR-based Phenotyping

Abstract: Opportunities to use “real world data,” data generated as a by-product of digital transactions, have exploded over the past decade. Such data sources facilitate research in a naturalistic setting and with greater speed than is possible for research that relies on primary data collection. However, using data sources that were not collected for research purposes comes at a cost, and naïve use of such data without considering the complex data generating mechanisms they arise from can lead to biased inference. In this talk, I will use my research on electronic health records (EHR)-based phenotyping to illustrate how statistical approaches to missing data and complex study designs can be harnessed to improve the validity of analyses using real-world data. EHR-based phenotyping is hampered by complex missing data patterns and heterogeneity across patients and healthcare systems, features that have been largely ignored by existing phenotyping methods. As a result, not only are EHR-derived phenotypes expected to be imperfect, but they often feature exposure-dependent differential misclassification, which can bias results towards or away from the null. I will review novel and existing approaches to EHR-based phenotyping, highlighting the impact of missing data on phenotype estimation. Finally, I will discuss approaches to minimize bias when incorporating error-prone phenotypes into subsequent analyses. The overarching goal of this presentation is to use the example of phenotyping to illustrate the unique contribution of statistics to the process of generating evidence from real world data.


+ Enormous medical research potential associated with study of afterwards
+ In the context of EHR based research, clinical informaticians have capitalized on deep knowledge of databased and EHR data structures to lead in this field

+ Statisticians have been hesitant to engage due to the imperfections of these dataset

Inference, missing data, study designs
+ Demonstrate how Bayesian clustering can be used to account for EHR data provenance in phenotyping

+ Present a method to reduce bias in analyses using healthcare data-derived phenotypes

Data Provenance
EHR
+ Longitudinal observational study with no specification of timing of visits, data elements to be collected at each visit, or definition of data elements
+ Unlike data from a designed study, the data capture process in EHR is outside the control of the researcher

+ observational research on steroids

+ Phenotype = collection of characteristics describing a patients
+ Need ways to deduce characteristics not explicit

+ Most of existing literature on EHR phenotyping relies on clinical decision resulted
Bayesian estimation
+ Bayesian framework combines strengths of data-driven statistical learning and use of clinical knowledge-base
+ Expert opinion on predictive performance of biomarkers incorporated into prior distributed

+ Observable features(codes, medications, biomarkers)
+ Posterior distribution can be a measurements
+ Posterior means and CIs for model parameters

+ Bias: missing data, selection bias, measurement error and other limitations of the healthcare data create the risk of substantial bias in parameter estimation
+ Variance: healthcare databases may include millions of records, allowing us to generate low variance estimates

Large healthcare databases create risk of generating extremely precise, biased estimates

What can we do about phenotyping?

+ How can we obtain unbiased estimates in analyses using EHR-derived phenotypes as outcomes?

+ challenge
  + Validation data

  Inference with imperfect phenotypes
  
