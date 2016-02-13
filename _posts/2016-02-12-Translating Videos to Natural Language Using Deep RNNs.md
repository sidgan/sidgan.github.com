---
layout: post
title: "Translating Videos to Natural Language Using Deep RNNs"
description: ""
category: [technical]
tags: [ai , ml, image captioning, paper review]
---
{% include JB/setup %}

## [Translating Videos to Natural Language Using Deep RNNs]()

Natural languages and videos have had little history because of limited training data which has the video and its respective descriptive sentences. It has also been hindered by the lack of rich models that can capture the joint dependencies of a sequence of frames and words. This paper proposes a way to translate the video to natural languages with a single deep neural network using transfer knowledge from auxiliary tasks. Each frame is modeled independently by a CNN and the sequence is modeled by a RNN (LSTM). Pre-training on images and text data exploits related data to supplement the limited amount of descriptive video content currently available. The end to end deep model for video to text generation that simultaneously learns a latent meaning state and a fluent grammatical model of the associated language, which is able to leverage still image classification and caption data and transfer deep networks based on the video domain. Initially video was only used to retrieval and predicting event tags but now it has expanded to generating descriptions. This model learns a joint state vector implicitly and models the sequence dynamics of the language. The video is converted to intermediate role representations and then decoded into a sentence. This bypasses the detection of high level roles that use the output of the deep CNN directly as the state vector that is decoded into a sentence. This avoids the need for labeling semantic roles which back be difficult to detect in case of large vocabularies. 

These models work by applying feature transformation which generates a fixed dimensional vector. A RNN as a sequence model is used for  is used to decode the vector into a sentence. The most likely description for a video is given by maximizing the log likelihood of the sentence. The videos are converted to the fixed length representation using the CNNs. 














