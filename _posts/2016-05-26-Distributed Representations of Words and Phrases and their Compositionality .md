---
layout: post
title: "Distributed Representations of Words and Phrases and their Compositionality"
description: "Distributed Representations of Words and Phrases and their Compositionality"
category: [technical]
tags: [deep learning, ml, ai, nlp, brain]
---
{% include JB/setup %}



### [Tomas Mikolov, Ilya Sutskever, Kai Chen, Greg Corrado, Jeffrey Dean](http://arxiv.org/abs/1310.4546v1)

The Skip-Gram model's greatest advantage is its efficiency in learning high quality vector representations of words from large amounts of unstructured text data.  The training objective is to learn a word representation that is good at predicting nearby words. Training of Skip-Gram model does not need dense matrix multiplications which makes the training efficient such that an optimized single machine implementation can train on more than 100 billion words in one day. These learned vectors explicitly encode linguistic patterns and regularities which can also be represented as linear translations.

This paper makes a few extensions to the Skip-Gram model. The extensions are: 

1. Subsampling of frequent words during training leads to speedup of 2x-10x. It results in better vector representations of less frequent words. 
2. A variant of Noise Contrastive Estimation is introduced which results in faster training and better vector representations of frequent words when compared to the representations yielded by hierarchial softmax. 

Skip Grams are made more expressive when vectors are used to represent whole phrases as the word representation is already limited by their inability to represent idiomatic phrases. These idiomatic phrases are not compositions of individual words. An example would be, "Globe Trotters" is not a natural combination of the meanings of the individual words, "Globe" and "Trotters". 

