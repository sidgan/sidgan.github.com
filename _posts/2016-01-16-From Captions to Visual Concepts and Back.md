---
layout: post
title: "From Visual Concepts and Back"
description: "From Visual Concepts and Back"
category: [technical]
tags: [ai , ml, rnn]
---
{% include JB/setup %}

## [From Visual Concepts and Back]( http://arxiv.org/abs/1411.4952)

Visual detectors, language models, and multimodal similarity models are learnt directly from a dataset of image captions. Part of Speech tagging is used to train visual detectors 

- Word detector outputs are conditional inputs to a max entropy language model 
- Global semantics by re-ranking captions (sentences with high likelihood) using sentence level features, such as a linear weighting of them and, a deep multimodal similarity model. Weights are learnt using Minimum Error Rate Training. Sentence re-ranking is done by MERT because the language model gives several (M) best sentences. MERT uses a linear combination of features computed overran entire sentence. This model is trained on the m-best list for the validation set and then applied to the similar m-best list for the test set. The best sequence is selected and use the caption. 

State of the art results on MS COCO measured by BLEU score, these systems captions have equal or better quality 34% of the time when compared by human judges to the captions written by other people. 

Captions are used in training which have the following three advantages 

- Captions contain information that is salient, hence the main part of the image is included and not much focus on the background is present.
- Training a maximum entropy language model on image captions inherently includes the commonsense knowledge using language statistics about the scene.
	- This commonsense knowledge disambiguates noisy visual detections and helps in identifying a category (among a variety of gradual category memberships that are possible)
	- A joint multimodal representation is learnt from which the global similarity between images and text can be measured and the most suitable one is the best caption. 

### Approach

- Weak supervised learning is used to create detectors for a set of words that occur with high probability in image captions. 
	- Learning directly from image captions is difficult because of the absence of supervisory signals such as the bounding box of the object within the image.
	- Not all words have a well defined relationship with bounding boxes 
		- The system plays with the image sub regions and not the entire image 
		- Each region of the image is converted into features using CNN and fine tuned on the training data
		- Features obtained from each region are mapped to the high frequency words with high probability of being in the caption, this is trained using Multiple Instance Learning (MIL) which learns a discriminative visual signature for each word.

The task of caption generation is termed as an optimization problem in which the the novel image descriptions have to be generated from a bag of likely words using an effective language model. With the word detection scores we find the highest likelihood sentence that overs each word exactly once. New features are introduced based on DMSM (Deep Multimodal Similarity Model) which improve the selection of quality sentences. This learns two neural networks that map images and text to one common embedding so that the similarity between sentences and images can be measured. The DMSM uses cosine similarity between vector representations to measure the similarity between images and text. This cosine similarity is used by MERT for re-ranking. Image captioning can be done in either of the following two ways:- Retrieve existing human generated captions 	- Neural networks have been used to map images and text to a common vector representation 	- Retrieval based methods use similarity metrics that take as the input a predefined image feature 	- Images and text may be linguistically motivated semantic triples and similarity may be computed in that space. 	- This method returns well formed captions but these captions might not have an exact match to the image, because they might have been penned down by humans for a different image.- Generate novel captions by the computers themselves	- This includes understanding the image, detecting the objects and their bounding boxes and then generating novel captions. 	- This is a generative approach and utilizes semantic and syntactic constraints. 	- The Midge System combines MLE with syntactic structures to generate novel sentences	- The generated sentences are compared against the Baby Talk system which generates descriptions by filling in the sentence templates. The words that are filled in the missing slots are taken from a conditional random field that predicts the likely image labels. Word detection is done through a caption generation pipeline that detects a set of words that are likely to be part of the images description. These are usually the most frequent words in the training captions. The entire image can be taken as the input for the image classifier but this yields worse performance because some concepts or words may apply to image sub regions. So, using MIL approach of weak supervised learnings the detectors are able to learn. A positive (if the word is contained in the description) and negative (absent from the description) set of bounding boxes are taken as input by MIL such that each bag corresponds to one image. By iterating and selecting instances within only the positive bags, hence the ones that are present the classifier learns the positive labels. Probability of a word given an image region is computed using fully connected layers? convolutional network run over the image to obtain a coarse spatial response map. Each location in this map corresponds to the response map by applying the original CNN to overlapping shifted regions of the input image. This entire input is given to the MIL which gives a single probability for a word for each image. Cross entropy loss is used to optimize the CNN with SGD. The probability obtained from MIL gives the word score for the test image. 

The generation of the language is a search for the most likely sentence conditioned on the set of visually detected words. The probability distribution over the word sequences if used for this purpose. This is a statistical model which is capable of encoding meaningful information. The statistical model generates captions for an image using maximum entropy language models conditioned on the set of visually detected words (preceding words). This offers the advantage that all words may be used and repetition is not present. Sometimes the detected words are noisy and even though end of sentence has been detected there might still be words that are predicted with high confidence. In the calculation of the statistical model NCE (noise contrastive estimation) is used, which means that the exact denominator in the equation of the probability conditioned on preceding words is not calculated but approximated. 