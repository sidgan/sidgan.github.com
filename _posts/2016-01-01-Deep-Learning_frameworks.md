---
layout: post
title: "Deep Learning Frameworks"
description: ""
category: [technical]
tags: [ai , ml, deep learning, frameworks]
---
{% include JB/setup %}

The purpose of this post is to write down what I know about these frameworks, as I learn more, I will keep on updating with more information. These are the deep learning frameworks that I have used or am using: 

## Tensor Flow 

+ Both C++ and Python
+ Released by Google

## Theano

Its a python library that allows one to define, optimize, and evaluate mathematical expressions involving multi-dimensional arrays efficiently. Developed at University of Montreal. 

Some important and beneficiary features of Theano are: 

+ Tight integration with NumPy
	+ Use numpy ndarray in Theano-compiled functions.
+  Hence Theano has been powered for large-scale computationally intensive investigations as it is also approachable enough to be used in the classroom. 
+ The package contains a number of utility modules that are helpful with machine learning tasks.
+ Keras, Pylearn2 are some other libraries which are build on Theano. 
+ Have a state of the art model for RNN and LSTM
+ Supports automatic gradient differentiation which is considered one of the most important points about it. 
+ Lower level abstraction offered by working with symbolic functions mean that more freedom with what we want is possible
+ This might be one of the reasons why it may seem complicated, there are no ready to run models, everything must be done on our own. 
+ I think the underlying architecture of Theano converts everything to a computational graph which makes fast calculations and calculations that can be shared easily among different parts of a process. 

## Caffe

+ Berkeley Vision and Learning Center developed it
+ Pretrained models are available for MNIST and other datasets which makes their use easy and highly newbie friendly
+ Extremely portable 
+ Fast, Caffe is said to have the fastest implementation of CNN
+ Caffe installation on OS X is slightly difficult. It was so much more easier on Ubuntu 14.04
+ Can be easily configured to use GPU's using flags

## Gensim 

+ Python library
+ Implementation of Word2Vec and Doc2Vec which is widely used
+ Easy installation


## Deeplearning4j

+ A Java and Scala library. 
+ Mainly a business framework
+ Brings a scala-like thinking
+ Easy installation

##Torch

+ I am a newbie at it because of not much knowledge about Lua. Torch is written in Lua. 
+ Written in Lua which is lightweight and easy to write wrappers of ultra fast C and C++ for Lua. 
+ State of the art convolutional network models 

## Cuda 

+ Support by GPU acceleration
+ CuDNN supports other frameworks and libraries
+ NVIDIA GPU's only