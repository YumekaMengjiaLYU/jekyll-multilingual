---
layout: post
title:  "Deep Learning for Natural Language Processing"
ref: welcome
date:   2020-07-05
tags: deep-learning-lectures
lang: en
---

The course slides:

<iframe src="https://storage.googleapis.com/deepmind-media/UCLxDeepMind_2020/L7%20-%20UCLxDeepMind%20DL2020.pdf" width="100%" height="500em"></iframe>

## 1.Background: deep learning and language
GPT2, BERT, WaveNet

### Why is Deep Learning such an effective tool for language processing?

#### 1. Words are not discrete symbols.

- Multi-head processing

- Distributed representations

#### 2. Disambiguation depends on context

- Self-attention

#### 3. Important interactions can be non-local

- Self-attention

- Multiple players

#### 4. How meanings combine depends on those meanings

- Skip connections

- Distributed representations

## 2.The Transformer

### Distributed representation of words

### What is the vocab on which our model is going to operate?

### The transformer builds on solid foundations

### Emergent semantic and syntactic structure in distributed representations

### The Transformer: Self-attention over word input embeddings

### Compute self-attention for all words in input (in parallel)

### Multi-head self-attention

### Feedforward layer

### Skip-connections - for "top-down" influences

### The Transformer: Position encoding of words

- Add fixed quantity to embedding activations

- The quantity added to each input embedding unit depends on:

    - The dimension of the unit within the embedding

    - The absolute position of the words in the input

## 3.Unsupervised and transfer learning with BERT

BERT: Pretraining of Deep Bidirectional Transformers for Language Understanding

Masked language model pretraining
Transformer encoder
Classification layer: Fully connected layer + GELU + Norm

Next sentence prediction pretraining


## 4.Grounded language learning at DeepMind: