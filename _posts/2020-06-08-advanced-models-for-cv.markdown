---
layout: post
title:  "Lecture 4: Advanced Models for Computer Vision"
ref: welcome
date:   2020-06-08
tags: courses
lang: en
---
 | Task definitions | Train and eval | Tricks of the trade |
|-------|--------|---------|
| Objecy detection | Models and losses | Hard negative mining |
| Semantic segmentation | Metrics and benchmarks | Transfer learning |

### Object detection
Multitask problem
classification localization

| Inputs | Targets | 
|-------|--------|
| Inputs | Targets | 
| RGB Image H*W*3 | Class label & Object bounding box (for all the objects present in the scene) |

### Bounding box prediction

Mistakes are not quantifiable in classification; the idea is not ordered.
In classification, the output is discrete; in regression, the output is continuous.
### Quadratic loss for regression
Minimize the MSE over samples.
### Summary 
 | Property | Classification | Regression |
|-------|--------|---------|
| Basic | map inputs to predefined classes | map inputs to continuous values |
| Output | discrete values | continuous values |
| Nature of the data | unordered data | ordered data |
| Algorithms | logistic regression, decision trees, neural networks | linear regression, neural networks |
