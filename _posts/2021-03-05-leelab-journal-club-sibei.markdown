---
layout: post
title:  "Research Meeting Notes"
ref: welcome
date:   2021-03-05
tags: career
lang: en
---

The presentation is based off of [Unsupervised Detection of Lesions in Brain MRI using constrained adversarial auto-encoders](
https://arxiv.org/pdf/1806.04972.pdf)

auto-encoder
compress it extract the most representative information from the original image, reduce the input, and then put the reduced information into the neural network to learn

generative adversarial networks

initialize the parameters

sampling m samples from the real sample, sampling m noise samples from the prior distribution noise and obtaining generated samples through
then fix G and D is trained to distinguish the real samples and generated samples as accurately as possible

after updating D for k times, the parameters of the G are updated with a small learning rate, and the G is trained to reduce

Goal use the generated sample distribution (the green solid line) to fit the real sample distribution (the black dotted line) to achieve the purpose of

How to determine parameters
maximum likelihood Estimation

kullback-leibler divergence is a measure of difference between two probability distributions

find theta to make the KL of as small as possible

##VAE##
variational auto-encoder used for approximating high-dimensional data distributions of images and outlier detection using different approach from GAN

GAN can generate quality images from random noise, it is randomly initialized
VAE is a probability model, the intermediate vector is generated after the introduction of the probability model on the basis of original data; it is not randomly generated

Intuition
By constructing our encoder model to output a range of possible values from which we'll randomly sample to feed into decoder models

for any sampling of the latent distributions, we're expecting

investigate VAE and AAE models for unsupervised detection of lesion in brain MRI by learning the prior distribution of healthy brain images

propose a constraint during training that encourages latent space consistency

generative Models

encoder: map high dimensional data Xh to lower dimensional latent representation z
decoder: reconstruct the images X encoded in the space of z

abnormal regions are then detected by pixel-wise intensity difference between original image and reconstruction

Adversarial auto-encoder AAE follows a similar encoding-decoding scheme as VAE and yet replaces KL with JS divergence

advantages of AAE over VAE is the coverage in the latent space

in VAE, the reconstruction of abnormal images tends to be less sharp; AAE produces sharper reconstruction

both reconstruction and detection are shown to be improved with latent constraints

for successful implementation, expect the error distribution of lesion pixels to be separated from that of healthy pixels

a latent constraint proposed to ensure latent consistency and enable more accurate detection of abnormal region

natural competitive to the models we present is the autogan model

https://surfer.nmr.mgh.harvard.edu/fswiki/Samseg
