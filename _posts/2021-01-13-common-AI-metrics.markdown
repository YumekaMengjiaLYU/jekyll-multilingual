---
layout: post
title:  "A Breakdown of Common AI Metrics"
ref: welcome
date:   2021-01-14
tags: career
lang: en
---

### Precision and Recall

Google has a wonderful [tutorial][ref-1] on precision and recall, and I will summarize it here:

$$Precision=\frac{TP}{TP+FP}$$

$$Recall=\frac{TP}{TP+FN}$$

Recall is also called as true positive rate or sensitivity in diagnostic testing.

Precision is also called as positive prediction value in diagnostic testing.
### F1 score
F1 score relies on both precision and recall.  It is usually more useful than accuracy especially when the distribution is uneven.

$$F1 = \frac{2Precision*Recall}{Precision+Recall}$$



### ROC curve

ROC stands for Receiver Operating Characteristic. 

A ROC curve has the False Positive rate as the x-axis, and the True Positive rate as the y-axis.

### AUC

AUC stands for Area Under the roc Curve. In other words, it is the integral of the ROC curve from (0,0) to (1,1).

AUC is desirable for the following two reasons:

AUC is scale-invariant. It measures how well predictions are ranked, rather than their absolute values.
AUC is classification-threshold-invariant. It measures the quality of the model's predictions irrespective of what classification threshold is chosen.
However, both these reasons come with caveats, which may limit the usefulness of AUC in certain use cases:

Scale invariance is not always desirable. For example, sometimes we really do need well calibrated probability outputs, and AUC won’t tell us about that.

Classification-threshold invariance is not always desirable. In cases where there are wide disparities in the cost of false negatives vs. false positives, it may be critical to minimize one type of classification error. For example, when doing email spam detection, you likely want to prioritize minimizing false positives (even if that results in a significant increase of false negatives). AUC isn't a useful metric for this type of optimization.

### Top-N Accuracy

If one of the top N probabilities predictions contain the true label, it would count the prediction as correct.

Top-N accuracy is particularly helpful for multi-class classications probems where $K$ is large.

An example would be a recommender system: when we recommend music or videos to users on Spotify or Netflix, we don't usually just recommend one specific album or title; instead, we recommend a set of "cherry-picked" options. In other words, we are not offering one single best prediction; we are offering a suite of options on a menu where the user can choose as he or she wants.

In such scenarios, it is intuitive that Top-N accuracy is more suiting than regular accuracy.


[ref-1]: https://developers.google.com/machine-learning/crash-course/classification/precision-and-recall