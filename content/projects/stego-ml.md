---
title: A frist approach for steganography using Language Models
date: 2020-12-24
categories: ["Projects"]
---

# Introduction

This project was conducted upon the [EPFL CS-433 course](https://www.epfl.ch/labs/mlo/machine-learning-cs-433/), for a semester project, during the fall semester 2020.

### What is Steganography ?

The principle of Steganography is to hide a secret message inside another message or in an image. These techniques can be used to avoid Man In the Middle (MITM) attacks and send secret messages to a pre-defined receiver. 

![The same image viewed by white, blue, green, and red lights reveals different hidden numbers. Source of the image : Wikipedia](/images/projects/steganography-wiki.png)

In practice, such protocols need to follow a **golden rule**:
* a common secret needs to be shared before (for the previous image, which color you need to use to reveal the secret image)

This rule applied also for well-known symmetric cryptography protocols where the common secret is the shared key. 

### Steganography and Deep Learning

Deep Learning and Steganography seems to be a good match, several papers from this one in [2017](https://papers.nips.cc/paper/2017/hash/838e8afb1ca34354ac209f53d90c3a43-Abstract.html) or more recently this one in [2021](https://arxiv.org/pdf/2101.00350.pdf) presents novel ways to hide a complex image into other images.

![Qualitative results from the 2021 paper](/images/projects/stego-paper-2021.png)

This model can achieve impressive results and these methods may be already in use into some real-world applications.

# Overview of the pipeline

Alice and Bob needs first to agree on the same Language Model and on the same preconditioning of the LM. This is a pre-required condition before running this protocol. 

![](/images/projects/stego.png)

# Code

The code is available online [here](https://github.com/younesbelkada/stego_ml) as well as the report that can be found [here](/files/MLCourse_2.pdf)