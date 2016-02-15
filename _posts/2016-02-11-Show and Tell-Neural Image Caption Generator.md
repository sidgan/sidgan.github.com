---
layout: post
title: "Show and Tell - Neural Image Caption Generator"
description: ""
category: [technical]
tags: [ai , ml, image captioning, paper review]
---
{% include JB/setup %}

## [Show and Tell: Neural Image Caption Generator](http://arxiv.org/abs/1411.4555)

Computer Vision and Natural Language processing are connected via problems that generate a caption for a given image. This caption is like the description of the image and must be able to capture the objects in the image and their relation to one another. Then, this caption must be expressed in a semantically correct form in a natural language. This paper presents a neural net trained using SGD. This model combines the sub-networks for vision and language models. If the model is pre-trained on a larger corpus then the resulting captions can make use of additional data. This model gives a BLEU score of 59 on the Pascal dataset. An LSTM based sentence generator is used.

In this paper a single joint model takes an image as input and is trained to maximize the likelihood of producing a target sequence of words where each word comes from a dictionary that describe the image perfectly. In machine translation and natural language processing the task is usually to transform a sentence in a source language to another language by maximizing the likelihood. Similarly, nowadays in machine translation RNNs are trained to do the same task. These encoder RNNs read the source sentence and transform it into a such fixed length vector representation which is the initial state of the decoder RNN. This decoder RNN has the hidden state which generates the target sentence. IT is necessary to note that the captions or descriptions generated may be of variable length but this model does not support that. 

In this paper, the RNNs are replaced by A CNN, which produce a representation of the input image by embedding it to a fixed length vector. This fixed length vector can be used for several computer vision related tasks. These CNNs can be used as image encoders by first pre training it for an image classification task and using the last hidden layer as na input to the RNN decoder that finally generates the sentences. 

A sequence model is thus generated which maximizes the probability of correct translation given an input sentence which is used both for training and inference. Hence, the job is to take an input image and translate it to its description. 

The design patterns followed are: 

	- The function which models how the images and words are fed as inputs 
	- The exact form of this function
 
The images are represented using CNNs with batch normalization and can be generalized to scene classification using transfer learning. The function choice is governed by its ability to deal with vanishing and exploding gradients, which are a common challenge in designing and training RNNs. To counter this, LSTMs are used which contains a memory cell which encodes all the knowledge that it possesses at every time step of what inputs have been observed up to this step. This LSTM model is trained for prediction of each next word in a sentence after being conditioned on the image and all the previous words.  Both the image and the the words are mapped to the same space, meaning the image by using the CNN and the words using the word embeddings. The word embeddings contain only the words minus the stop words in a one hot vector representation. The image is input only once and this gives better results than giving the image as input every time step. 

This yields two approaches that can be used to generate a sentence when given an image. These include: 
	- Sampling 
    		- Sample the first word according to the probabilities and the corresponding embedding as inputs and sample probabilities until the end of sent token or the maximum length of the sentence is reached.    
	- Beam Search
    		- Iteratively consider each of the best sentences to a certain time as the potential candidates to generates sentence of size one greater than the time stamp. This uses the arg max approach.    


 