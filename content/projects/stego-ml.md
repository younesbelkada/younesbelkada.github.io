---
title: A frist approach for steganography using Language Models
date: 2020-12-24
categories: ["Projects"]
comment: false
weight: 10
comment: false
tags: ['Steganography', 'Deep Learning', 'Language Models']
featuredImage: ""
featuredImagePreview: ""
lightgallery: true
---

# Introduction

This project was conducted upon the [EPFL CS-433 course](https://www.epfl.ch/labs/mlo/machine-learning-cs-433/), for a semester project, during the fall semester 2020. This project tries to find a novel approach for steganography applied to text data using Language Models.

### What is Steganography ?

The principle of Steganography is to hide a secret message inside another message or in an image. These techniques can be used to avoid Man In the Middle (MITM) attacks and send secret messages to a pre-defined receiver. 

{{< image src="/images/projects/steganography-wiki.png" caption="The same image viewed by white, blue, green, and red lights reveals different hidden numbers." height="300" width="300" title="Source of the image : Wikipedia">}}

In practice, such protocols need to follow a **golden rule**:
* a common secret needs to be shared before (for the previous image, which color you need to use to reveal the secret image)

This rule is applied into well-known [symmetric cryptography](https://en.wikipedia.org/wiki/Symmetric-key_algorithm) protocols where the common secret is the shared key. 

### Steganography and Deep Learning

Deep Learning and Steganography seems to be a good match. In 2017, Google releases [Hiding Images in Plain Sight:
Deep Steganography](https://papers.nips.cc/paper/2017/file/838e8afb1ca34354ac209f53d90c3a43-Paper.pdf) that attempts to hide a secret image into another image of the same size. The method implies 3 networks, 2 neural networks to **encode** the input image and another network to **decode** the encoded image.

{{< image src="/images/projects/fig-stego.png" caption="Model architecture of the described method - Figure directly taken from the paper" height="600" width="600" >}}

More recently [Abhishedk Das et al.](https://arxiv.org/pdf/2101.00350.pdf) proposes a novel way to encode multiple images into a single encoded cover image, and retrieve accurately the multiple images using only the single cover image as an input.

{{< image src="/images/projects/fig-stego-2021.png" caption="Model architecture of the described method - Figure directly taken from the paper" height="600" width="600" >}}

These techiques can achieve impressive results and may be already in use into some real-world applications.


{{< image src="/images/projects/stego-paper-2021.png" caption="Qualitative results from the paper 'Multi-Image Steganography Using Deep Neural Networks' by Abhishedk Das et al." height="400" width="400" >}}

Deep Learning and Steganography are also a good match when it comes to speech data, according to the paper [Hide and Speak: Towards Deep Neural Networks for Speech Steganography](https://arxiv.org/pdf/1902.03083.pdf), but we have struggled (back in 2020!) to find very intersting work matching ***Steganography***, ***Deep Learning*** and ***textual data***. Here came the challenge that drove us and pushed us to pursue the project.

### Why Steganpography applied to text?

Image that you want to communicate with your friend and make sure that your message is completly hidden and secure when passing through the communication channel. Classic and current techniques are purely based on asymmetric encryption (using Public and Private keys) and very hard to break in practice. Having several encrypted messages passing through a channel can easily arose the Man In The Middle's attention. How to avoid this? ***Using Steganography!***

Steganography provides (in theory) the feature of hiding a message into ***another*** message. This can be lead to two main contributions for more robust communication protocols:

* Since the covered messages will make sense, they can circulate in the communication channel without being encrypted and without arousing the MITM's attention
* For more robust protection, the covered messages can be encrypted using classic encryption methods. Our Deep Learning method will play the role of an extra very robust protection.  

# Overview of the pipeline

Alice and Bob needs first to agree on the same Language Model and on the same preconditioning of the LM. This is a pre-required condition before running this protocol. 


{{< image src="/images/projects/stego.png" caption="General pipeline of the method" height="600" width="600" >}}

# Code

The interactive code is available online [here](https://github.com/younesbelkada/stego_ml) as well as the report that can be found [here](https://www.epfl.ch/labs/mlo/wp-content/uploads/2021/05/crpmlcourse-paper822.pdf)