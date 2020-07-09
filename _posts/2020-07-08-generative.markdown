---
layout: post
title:  "Generative Adversarial Networks"
ref: welcome
date:   2020-07-05
tags: deep-learning-lectures
lang: en
---


The course slides:

<iframe src="https://storage.googleapis.com/deepmind-media/UCLxDeepMind_2020/L9%20-%20UCLxDeepMind%20DL2020.pdf" width="100%" height="500em"></iframe>

### Generative models

#### Explicit
What kind of distribution could have generated this data?

- We can learn an explicit model of the data, this

- Answer quesitons using the model

#### Impilicit

simulator that cna generate same properties 

In ML, we train the models to maximize the probability distribution of the data under our model. 

train latent variable models with maximum lax
gets tricky
use approxiate maximum likelihood

2014 GAN Ppaer show we can go from simple image of digits to images of faces, small resolution

black and white to colored

break the imagenet barrier in 2018, trained 

generate faces at very high resolution
quite photo realistic

not only on high diversity but also  high resolution

how are gans able to learn the probabilic so accuaraly to generate such data

player:
- discriminator
- generator

have a distribution on the input of  our model

variational auto-encoder 

distribution - multi-variate gaussian noise

noise is much more dimensional than the data

pass it to deterministic nn

discriminator
given some set of samples from our data and given form models,

are these real  or are t
hese generated?

discriminator as a teacher
guide and also improve itself

ge