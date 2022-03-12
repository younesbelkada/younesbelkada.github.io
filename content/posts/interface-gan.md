---
author: "Younes Belkada"
date: 2022-03-12
type:
- post 
- posts
title: "InterfaceGAN++: How far can we go with InterfaceGAN?"
weight: 10
tags: ["Deep Learning", "GAN", "Face editing"]
categories: ["Posts", "Projects"]
comment: false
featuredImage: /images/posts/interfacegan.gif
featuredImagePreview: /images/posts/interfacegan.gif
lightgallery: true
---

I would like to explain in this post, one the projects I was involved during my Masters degree at *ENS Paris Saclay*, during the *Introduction to Numerical Imaging* course. 

### Introduction

[InterfaceGAN](https://genforce.github.io/interfacegan/) is a paper that has been published on CVPR 2020, by Yujin Shen et al. It argues that well-trained generative models learns a disentangled latent space representation.

Basically given a **generated** face image from a random gaussian noise, InterfaceGAN can control some specific attributes of the face without altering the semantic information of it. Simply said, given a generated face, it can change the age, gender, presence of eyeglasses and expression of it. But we were questioning to ourselves, does this property applies also for other attributes? How disentangled is the representation of well-trained GANs such as StyleGAN (or the more recent StyleGAN3)?

### Code

The code of our work is publicly available on GitHub, on [this link](https://github.com/younesbelkada/interfacegan). You can easily play with the Colab Notebook to generate your own custom faces.