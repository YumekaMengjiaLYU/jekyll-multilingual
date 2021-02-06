---
layout: post
title:  "A Look into Statistical Tests"
ref: welcome
date:   2021-01-22
tags: career
lang: en
---


TYPE I Error
+ H_0 is true, but we mistakenly reject it : false positive
+ controlled by significance level $\alpha$

Type II Error
+ H_0 is false, but we fail to reject it: false negative

The probability that a hypothesis test will correctly reject a false null hypothesis is the power of the test

several different ways of quantifying the likelihood of obtaining false positives

+ family-wise error rate
+ probability of any false positives
want to guard against having any false positives at all

+ false discovery rate
+ control proportion of false positives among rejected tests

### Correct for the FWER


FWER 
probability of making one of more Type I errors in a family of tests, under the null hypothesis

Controlling

+ Bonferroni correction
+ Random field theory
+ Permutation tests

Tradeoff
detect and control FWER

### Bonferroni correction
+ Bonferroni correction is very conservative: results in very strict significance levels
+ decreases the power of the test (probability of correctly rejecting a false null hypothesis) and greatly increases the chance of false negatives
+ not optimal for correlated data, and most fMRI data has significant spatial correlation

number of independent tests << voxels


### issues with FWER

+ Methods that control the FWER(Bonferroni, RFT, Permutation Tests) provide a strong control over the number of false positives

+ While this is appealing, the resulting thresholds  often lead to tests that suffer from low power

+ Power in critical in fMRI applications because the most interesting effects are usually at the ede of detecdtion

### FDR

FWER control the probability of any false positives

FDR controls the proportion of false positives among all rejected tests


l