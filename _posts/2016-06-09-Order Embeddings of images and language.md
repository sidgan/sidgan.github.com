---
layout: post
title: "Order Embeddings of images and language"
description: "Order Embeddings of images and language"
category: [conference]
tags: [deep learning, ml, ai, nlp, paper review, image captioning]
---
{% include JB/setup %}


### [Ivan Vendrov, Ryan Kiros, Sanja Fidler, Raquel Urtasun](http://arxiv.org/abs/1511.06361)

All problems relating images and text involve the visual semantic hierarchy and have some partial order over images and langauge. Example: Captions are abstractions of images. 

If a system is able to learn representations that represent the partial order structure then it should help in solving the image-text problems. A method for learning the ordered representations which is the basis for many tasks involving image and languages. 

Distributed representations or embeddings are used to model the image-caption relations because they can map text and images to high dimensional vector space. This mapping is distance preserving so semantically similar objects are mapped to points near each other in the embedding space. The distance measure should be symmetric and Euclidean or cosine is usually used. However, the visual semantic hierarchy is antisymmetric so there is a systematic model error which is introduced. 

This paper uses an explicit constraint to impose the transitivity and antisymmetry of the partial order unlike other methods which learn a binary relation. Instead of distance preserving, an order preserving visual semantic hierarchy with a partial order over the embedding space is learnt. Hence, this is called order embeddings. Just by replacing the comparison operator, the Euclidian distance by the order comparison an improvement over the state of the art for hypernymy prediction, caption-image retrieval and natural language inference is seen. 

Somethings I didnt understand: 

- How is hierarchy represented by mapping to high dimensional points?
- How does the representation ensure that the visual semantic hierarchy is antisymmetric ?


