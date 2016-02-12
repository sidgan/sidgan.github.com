---
layout: post
title: "Deep Visual Semantic Alignments for Generating Image Descriptions"
description: ""
category: [technical]
tags: [ai , ml, image captioning, paper review]
---
{% include JB/setup %}

## [Deep Visual Semantic Alignments for Generating Image Descriptions](http://arxiv.org/abs/1412.2306)

They use an ensemble of CNN?s over images, BRNN?s over sentences and a structured objective that aligns these two modalities through a multimodal embedding. This Multimodal RNN is used to generate image captions. This model has been tested on the Flickr8K, Flickr80K and MS COCO datasets. This paper treats the language as a rich label space in contrast to the other works which usually focus on labeling images with a fixed set of visual categories. These closed vocabularies constitute the convenient modeling assumptions but are restrictive in comparison to the varying degree of natural language descriptions that a human can compose.

A dense description of images is generated which is rich enough to reason about the content of the image and their representation in the domain of natural language. Also, the descriptions of images have objects in them but whose location within the are unknown. These locations are inferred from contiguous segments of the sentences and these sentences are treated as weak labels. If these alignments are learnt then they can be used in a generative model for the descriptions.

The alignment model presented in this paper is a combination of CNN over images, bidirectional RNN over sentences and a structured objective that aligns these two modalities through a multimodal embedding. Using this process it is possible to generate dense descriptions of images. However, the design of the model should be rich enough to simultaneously reason about the content of the images and their representations in natural language domain. This model is kept free of assumptions, including any hard coded boilerplates. Hence, all the outputs are produced through learning from the training data. Another important constraint is that the image captioning datasets have in their descriptions a multiplex mention of objects, however their respective locations cant be defined. These are like abstract concepts, like beautiful, happy, stern.  

This paper brings a novel way to approach these problems by leveraging large image captioning datasets by treating these captions as weak labels in which the contiguous segments of the words correspond to some particular but unknown location in the image. These alignments are inferred and then the generative model description is learnt using them. To make this possible a deep neural network is developed which infers the latent alignments between the segments of sentences and the regions of the images that they describe. The effectiveness of this model is gauged through the image sentence retrieval experiments. A multimodal RNN architecture takes an input image and generates a description for that image.  

The idea presented in this paper is motivated by the approach of learning ground dependency tree relations to image regions with a ranking objective. Images are represented using a region CNN which is pre-trained on ImageNet and fine tuned on the classes of the ImageNet Detection Challenge. There are 60 million parameters. The sentences are represented in the same dimensional embedding space. This is done by projecting every individual word to the embedding. This does not take into account the word order and context of words. In order to include some semantic information bidirectional RNNs are used for word representations. They take a sequence of N words and transform each into a similar embedding as the image. This representation includes variably sized context information. 

After attaining the common dimensional space the image sentence score serves as a function of the individual region word scores. The sentence-image pair must have a high matching score if its words have a confident support in that image. However, this results in generation of single words which is not required. TO satisfy this, the alignment is extended over contiguous sequences of words to a single bounding box. This is done in a Markov Random Field where the binary interactions between neighboring words encourage  an alignment to the same region. With a sentence and image and its bounding box, the latent alignments are produced and formulated in a MRF chain structure. 

Now, the problem of variable sized output sequences is to be solved. Each image may have a caption of different length and this needs to be modeled within the architecture as well. Sentence tokens like, START, * and STOP are used for modeling. The image context vector is provided to the RNN for training and for testing the image representation is used to compute the distribution over the first word, (which comes after START) 

SGD is used for training with mini batches of 100 images and their captions. Dropout regularization is used in all layers except the recurrent layer. The generative RNN is more difficult to optimize because of the word frequency disparity between the rare and the common words. 

### Experimental Datasets:
- Flickr8K
- Flickr30K
- MSCOCO
 
