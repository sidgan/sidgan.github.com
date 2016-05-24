---
layout: post
title: "The Neural Conversation Model"
description: "The Neural Conversation Model"
category: [technical]
tags: [deep learning,ml,ai,nlp, brain]
---
{% include JB/setup %}


### [Oriol Vinyals and Quoc V.Le](http://arxiv.org/abs/1506.05869v3)



Neural Networks to map sequences to sequences which in this regard are statements and their responses.

Simple and general, the same end-to-end system can be used for machine translation, conversations and question answering. 

The only difference in conversations is that the input sequence is the concatenation of what has been covered so far (the entire context) and the output sequence is the reply.

Translation in comparision to conversations is a much easier task. This is again fortified by the fact that the objective function in conversations is a simplification of the human communication objective. Human conversations are long term and is based on exchange of information rather than step to step prediction. They also need world knowledge which is absent in an unsupervised model.