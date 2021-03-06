---
layout: post
title: "Who Said it?"
description: ""
category: [technical]
tags: [naive bayes, classification]
---
{% include JB/setup %}


“I love reading Jeffrey Archer.” It is possible to guess which of your friends said it. The computer can also guess who! In a group of people, who is more likely to have said something can be predicted if the computer has heard them talk before. The computer can analyze their thought process while interacting with them and, in due course of time, predict the most probable speaker, given a statement. 


## Introduction

‘Who Said It?’ aims at mirroring the analytical power of the human brain. Just as the human brain can process a given amount of data to deduce something, we can train our computer to analyse a training data set, learn from it, and answer from what it has learnt when queried upon.
 
A dataset comprising of statements made by three Indian politicians, Narendra Modi, Arvind Kejriwal and Rahul Gandhi is analysed by the computer. When a statement is given to it, it will use this analysis to name the politician who is most likely to have said it.

## Training Dataset

The training dataset is a collection of statements that is stored in csv (comma separated values) format. An approximately equal number of statements made by the three politicians Arvind Kejriwal from Aam Aadmi Party, Rahul Gandhi from Congress and Narendra Modi from BJP are present in the dataset. These statements are derived from their speeches obtained from various sources on the Internet. 

### Removing redundant data

To create the feature vector we need to get rid of redundant data. These include additional white spaces and neutral words that do not contribute towards identification of the speaker. We call the latter [stop words](https://github.com/sidgan/Who-Said-it-/blob/master/stopwords.txt) (e.g. a, and, party, the, election etc.) 

### Creating the feature vector

The statements in the training dataset are processed word by word producing a string of important words binary values which is later used for prediction of the model. The feature vector is also devoid of redundant data such as repeats, punctuation, numerical values and stop words. Hence, these are ignored while prediction.
 
### Extracting Features

Now from the feature vector generated, binary values indicating confidence value of that feature is appended to each feature. 

### Working

The model is based on extracting the feature vector of the problem statement and comparing it against the training dataset using a classifier. 

### Extracting features of problem statement

The data redundancy is removed just like it is done for the training dataset.  A feature vector is created and extraction is performed. 

### Classification of the problem statement

The problem statement is classified using the Naive Bayes classifier on the extracted feature vector. Thus, the machine is able to predict the most probable speaker of the problem statement. 
 
## Conclusions

The machine was successfully able to predict known statements of the speakers. To improve the prediction more precise classifiers can be utilized. 
