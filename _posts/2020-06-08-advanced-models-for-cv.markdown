---
layout: post
title:  "Lecture 4: Advanced Models for Computer Vision"
ref: welcome
date:   2020-06-08
tags: courses
lang: en
---
_Goal of the lecture: Know how to redefine the building blocks to perform different visual tasks using different inputs and different forms of supervision._
## 1.Supervised image (beyond classification)
 | Task definitions | Train and eval | Tricks of the trade |
|-------|--------|---------|
| Objecy detection | Models and losses | Hard negative mining |
| Semantic segmentation | Metrics and benchmarks | Transfer learning |

### Tasks - increasing granularity
classification -> object detection -> semantic segmentation -> instance segmentation
### Object detection
**A Multitask problem: Classification & Localization**


| Inputs | Targets | 
|-------|--------|
| RGB Image H*W*3 | Class label & Object bounding box (for all the objects present in the scene) |

### Bounding box prediction
> How to learn to predict real-valued bounding box coordinates?

#### Recap: Softmax + cross entropy
**Assign data points to categories; output is discrete.**

Mistakes are not quantifiable in classification; the idea is not ordered.

In classification, the output is discrete; in regression, the output is continuous.

### Quadratic loss for regression
Minimize the MSE over samples.


$$
l_2(x,t) = |x-t|^2

$$

**The question is: How to deal with multiple targets?**

### Classification then regression
**Convert regression into classification, by discretizing the output values, and then refine through regression.**


Bin the output space and then use one hot label. Once in the local area then regress.

### Summary 

| Property | Classification | Regression |
|-------|--------|---------|
| Basic | map inputs to predefined classes | map inputs to continuous values |
| Output | discrete values | continuous values |
| Nature of the data | unordered data | ordered data |
| Algorithms | logistic regression, decision trees, neural networks | linear regression, neural networks |

### Case study 1: Faster R-CNN
Two-stage detector
- Identify good candidate boundary boxes
    - Discretize bbox space
        - anchor points for (x,y)
        - scales and ratios for (h,w)
    - n candidates per anchor
    - predict objectness score for each box
    - sort and keep top K
Deep learning is very flexible, and we can replace those pieces in the puzzle. But we have to put functions that are differentiable so that we can backprop through.
Non-differentiable building block
- Classify and refine

### Case study 2:RetinaNet - one-stage detector
Most of the candidate boxes are easy negatives: poor learning signal

### Issue with one-stage detectors
- Most of the candidate bboxes are background. easy to classify
- The accumulated loss of the many easy examples overwhelms the loss of rare useful examples
- Faster R-CNN prunes thses
- One stage detectors employ hard negative mining heuristics.
- RetinaNet uses Focal Loss

### Semantic segmentation

Bounding boxes are not good representations for certain types of objects.
We need more refined representation.

| Inputs | Targets | 
|-------|--------|
| RGB Image  | Class label for every pixel |

### Case study: U-NET
- Encoder-decoder model
- Skip connections to preserve details

### Evaluation metrics
Classification

- Accuracy: percentage of correct predictions
Top-1: top prediction is the correct class
Top-5: correct class is in top-5 predictions

Object detection and segmentation
- Intersection-over-union
non-differentiable: used only for evaluation

## Trick of the trade
### Transfer learning

Let D = {x, p(x)}, X = {x1,..xn} be a domain and T={Y, f(')}, f(.)=y a task  defined on this domain
Given a source domain and task (Ds Ts) and a target domain and task (Dt tt ) reuse knowledge learnt by f in ft

**Intuition is to reuse knowledge - features are shared across tasks and datasets.**
### Transfer learning across different domains

#### Sim2Real
- Train in simulation using RL- Ds
- Use Automatic Domain Randomization: data augmentation + hard negative mining
- Test in real world - Dt

## 2.Supervised (Beyond singe image input) Classification
### Experiment
### Video
- Motion - cues for object recognition during learning
- Natural data augmentation: translation, scale, 3D rotation, camera motion, light changes
### Optical flow estimation

| Inputs | Targets | 
|-------|--------|
| Pairs of RGB Image  | Dense flow map;2D translation displacement |

### Case study: FlowNet
- Encoder-decoder architecture similar to U-NET
- Supervised training
- Loss: Euclidean distance
- Flying chairs dataset
- Sim2Real transer

### Video models using 3D convolutions
Video as a volume
- stack frames T H W 3
- apply 3D convolutions
### Properties of 3D convolutions
- 3D convolutions are non-causal
- masked 3D convolutions are causal

Strided, dilated, padded,  ...  convolutions apply in 3D as well.

| Inputs | Targets | 
|-------|--------|
| - RGB Video T H W 3 
  - (optional) flow map | action label |

### Transfer learning returns
**Intuition: a tiled image is a video of a static scene, filmed with a fixed camera**

### Challenges in video processing
- Difficult to obtain labels
- Large memory requirements
- High latency
- High energy consumption
### Improve efficiency of video models
- Inspiration from biological systems
- Maximize parallelism to increase throughput and reduce latency
- Exploit redundancies in the visual data to obtain frugal models
## 3.(Beyond supervised) image classification
### Self-supervision - Metric learning
Standard losses (eg. cross entropy, mse)
- learn mapping between inputs and output distribution/values
Metric learning
- learn to predict distances between inputs given some similiarity measure

Metric learning
- Contastive loss
- Triplet loss
- State-of-the-art on representation learning

Applications
- Multimodal self-supervised representation (image+sound)
- Information retrieval
- Low-shot face recognition

## 4.Open questions