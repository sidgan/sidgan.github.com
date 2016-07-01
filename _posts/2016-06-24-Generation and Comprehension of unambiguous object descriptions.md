---
layout: post
title: "Generation and Comprehension of unambiguous object descriptions"
description: "Generation and Comprehension of unambiguous object descriptions"
category: [conference]
tags: [deep learning, ml, ai, nlp, paper review]
---
{% include JB/setup %}

### [Junhua Mao, Jonathan Huang, Alexander Toshev, Oana Camburu, Alan Yuille, Kevin Murphy](https://arxiv.org/abs/1511.02283)

Spatial positions need bounding boxEvaluation of the mid level vectors because it could be an encoding - model will communicate better with itself in its own encoding. - CO-Training vs multi view system - Multiple models on diff views and then improve iterativelyTraining is semi supervised in this paper - this is like - bootstrapping?Examples show interesting visual features that can encode 'behind'. Assumption is that the training dataset must have such words. Hard ground truth is the most confusing caption.Mutual information is used in the paper.N - hyper param from UNC datasetApplications - Communication with automated systemsGuide attention models - generate soft and hard attention Dividing regions - Harms captioning and VQA - Big LSTM should be able to understand different regions- Residual networks 	- Force the network to remember the image	- Image vector is fed again and again		Are they training word embeddings on their own ? Their dims are different from the standard word embeddings. P(sentence | region, image) 	- Like an n gram - Next word given sentence so farFine tuning on the MS COCO should give the last layer with 80 dims but the paper says that it is 1000 dims, why?- 1000 dim is just to make sense with fine tuning?- End to end fine tuning Interesting to note that the weak labels did not mess up the actual result labelsA possible idea that comes to mind is, can unambiguous object descriptions be used for an image retrieval task?- What is the one thing about this image that defines it uniquely - Something that is different from all other images? - However, what may be unique in an image may not be unique over the entire dataset	- This might be a problem while approaching the image retrieval task. 