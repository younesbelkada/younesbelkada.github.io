---
title: An unsupervised method for table structure recognition
date:   2019-08-31 20:26:19 +0200
author: "Younes Belkada & Arthur Zucker"
categories: ["Projects"]
---

### Problem statement

Some organizations still use huge amounts of scanned tables / invoices. Rather than manually typing the contents of the tables into an excel file, one can think of using Deep Learning to tackle this problem.
Once you identify the distinguishable cells on the tables, we can pass an OCR (Optical Character Recognition) to each cell to read its contents and convert it to an excel file for example.

![The method performs table structure recognition in an unsupervised way](/images/projects/table.png)

Here comes the task of table structure recognition, the main goal would be to efficiently detect the individual cells given an image containing textual information (characters, digits).

This work has been achieved through one of my internships together with [Arthur Zucker](https://arthurzucker.github.io/), and the work resulted on the publication of a research article that can be browsed [here](https://link.springer.com/article/10.1007/s11036-021-01759-9).

### ***Why this task is so challenging ?***