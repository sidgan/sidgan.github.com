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

The advantage of using neural networks is that the system becomes are simple and general, the same end-to-end system can be used for machine translation, conversations and question answering. 

The only difference in conversations is that the input sequence is the concatenation of what has been covered so far (the entire context) and the output sequence is the reply.

Translation in comparision to conversations is a much easier task. This is again fortified by the fact that the objective function in conversations is a simplification of the human communication objective. Human conversations are long term and is based on exchange of information rather than step to step prediction. They also need world knowledge which is absent in an unsupervised model.

### Model 

A sequence to sequence, called seq2seq framework which takes input of one token at one timestamp and outputs one token at one timestamp. The framework is established using RNNs. The training phase involves learning the given true output through backpropagation.  

In language tasks the objective is to decrease the perplexity and in this task as well the model is trained to maximize the cross entropy of the correct sequence using the context. 

### Experiments 

The experiments in the paper were carried out on two datasets: 

1. A closed domain IT helpdesk troubleshooting dataset
2. An open domain movie transcript

Some local [experiments](http://sidgan.me/technical/2016/05/01/Capstone) were carried out by us and these show that the model can remember facts, understand context and can perform common sense reasoning all in an end-to-end fashion. However, in agreement with the paper there are some disadvantages and advantages as below. 

#### Disadvantages

1. Answers are simple, can be unsatisfying
2. No personality of system


#### Advantages 

1. Model can generalize to new questions
2. Not rule based
3. No look up of answer from an existing database
4. is able to extract knowledge from noisy open domain dataset

It is necessary to remember that conversation models are [AI-Hard](http://sidgan.me/technical/2016/01/09/Image-Captioning-as-AI-Hard) and as such there is no well defined metric to measure the quality of a conversational model. Usually all systems perform evalvation manually using AMT. 


