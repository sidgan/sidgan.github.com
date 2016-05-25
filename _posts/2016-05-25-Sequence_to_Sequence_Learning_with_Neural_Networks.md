---
layout: post
title: "Sequence to Sequence Learning with Neural Networks"
description: "Sequence to Sequence Learning with Neural Networks"
category: [technical]
tags: [deep learning,ml,ai,nlp, brain]
---
{% include JB/setup %}

### [Ilya Sutskever, Oriol Vinyals, Quoc V. Le](http://arxiv.org/abs/1409.3215v3)

Deep Neural Networks are utilized in an end to end approach to sequence learning while making minimal assumptions about the sequence structure. A multilayered LSTM maps the input sequence to a vector of a fixed dimensionality and a deep LSTM decodes the target sequence from the vector. The LSTM was able to learn phrases and sentence representations that were sensitive to word order and invariant to the voice (active or passive). If the word order of the source sentences is reversed then the LSTM's performance increases because this introduces short term dependencies between the source and target sentences while making optimizations easier. The order of the target sentences is not reversed. 

