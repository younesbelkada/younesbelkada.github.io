---
author: "Younes Belkada"
date: 2022-01-16
type:
- post 
- posts
title: "Mastering Natural Language Processing - Words as vectors"
weight: 10
tags: ["Journal", "Word Embeddings", "Deep Learning", "NLP"]
categories: ["Posts"]
comment: false
featuredImage: /images/posts/nlp_1.png
featuredImagePreview: /images/posts/nlp_1.png
lightgallery: true
---

## Why NLP is so exciting?

Natural Language Processing is an application of AI and Deep Learning that allows machines and algorithms understand languages (Natural Language) in order to easily deal with any problems related to text (text classification, sentiment analysis, summarization, etc.). There is also a very large interest around NLP from big tech companies and investors as the potential applications of Deep Learning for NLP are becoming more and more impactful.

## From a language for Humans to a language for machines

How do we teach machines to understand human language? Humans understand the each word that we read and listen because we know their meanings. A **meaning** can be defined as
+ The idea that is represented by a word, phrase, etc.
+ The idea that a person wants to express by using words, signs, etc.
+ The idea that is expressed in a work of writing, art, etc.

A machine needs to do the same thing. Associate to each word, a meaning. Previous work includes resources like *WordNet* that stores word's synonyms and semantics but can be showed that it is not *scalable*. We will see that there are several ways to explicitly teach a machine to understand and model a words meaning. 

### One hot vectors

Here comes the simplest approach for converting any word into a vector. We can simply encode any word into a binary vector. Below is a dummy example:

{{< image src="/images/posts/one-hot-vectors.png" caption="A dummy example for one-hot encoding- Source: Stanford cs224n lecture">}}

{{< admonition type=quote title="" open=true >}}
These two vectors are not orthogonal therefore, there is no natural notion of **similarity** for one-hot vectors!
{{< /admonition >}}

### Learning words representation

A word can be also defined by its context, *i.e.*, the nearby words of it. This idea can be exploited, rather than representing each word independently, a word should be represented by its context and this is called *Distributional semantics*.
{{< admonition type=quote title="Quote from  J.R. Firth" open=true >}}
 *You shall know a word by the company it keeps* 
{{< /admonition >}}
Therefore, the representation of the word *finance* should be close to the representation of the words *money*, *bank*, *trading*, *currency*, etc. This idea appeared to be very successful and used in techniques such as *Word2Vec*.

+ At each position *t* on the text, we have the center word *o* and the surrounding context words *c*. 
+ Objective: For each position *t* in the text, predict the context words with a window size of *m*, given the center word.
+ Objective function: Log-likelihood

{{< image src="/images/posts/word2vec.png" caption="Training pipeline of Word2vec - Source: Stanford cs224n lecture">}}


### Useful links

+ [Stanford CS224n lectures](http://web.stanford.edu/class/cs224n/)
+ [Word2Vec vs Language Models](https://ai.stackexchange.com/questions/26739/what-is-the-difference-between-a-language-model-and-a-word-embedding) 
+ [UMass CS685](https://people.cs.umass.edu/~miyyer/cs685/schedule.html)