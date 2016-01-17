---
layout: post
title: "Exploring Datasets"
description: ""
category: [technical]
tags: [ai , ml, datasets, image captions]
---
{% include JB/setup %}

 
### PASCAL SENTENCE DATASET 

- Link: http://vision.cs.uiuc.edu/pascal-sentences/

### FLICKR 8K 

- Publically available dataset: http://nlp.cs.illinois.edu/HockenmaierGroup/8k-pictures.html
- The Flickr 8K dataset includes images obtained from the Flickr website. 
- University of Illinois at Urbana?Champaign has the sole link of this dataset. 

### FLICKR 30K 

- This is an extension to the Flickr 8K. 
- Link: http://shannon.cs.illinois.edu/DenotationGraph/
	
### MS COCO 

- Link: http://mscoco.org/


### DAQUAR Dataset

It is a dataset for question answering (natural language sentences) based on real world images( which include indoor scenes).

#### Vision and Language 

-	A set of images and questions about their content is presented. 
-	DAQUAR questions contains 1088 nouns, while answers contain 803 nouns along with other POS. 



#### Common sense knowledge 

Search space can be restricted based on understanding non-visual cues from the questions. 

#### Question Answering 

Questions are asked based on spatial concepts within different frame of reference. 

#### Performance Evaluation 

Settling on the perfect metric is difficult because:

- Automation 
	- Understand natural language and try to gauge answers
	- Individual judging of every answer is a difficult task so an automatic approximation is reached.
- Ambiguity 
	- The gradual category membership of of human perception is variable and brings ambiguity
	- Multiple interpretations of questions are possible leading to many correct answers
- Coverage
	- The equivalence class among the answers is considered by assigning similar scores to members of the same class.

#### Metrics 

-	WUPS SCORE
	- It is an automatic metric that quantifies performance of the holistic architecture.
	- It provides a soft generalization of the accuracy that takes ambiguities of different concepts into account using set membership measure. 
	- It offers two generalizations
		- Interpretation metric 
			- That many human answers takes the max score and high score will be granted to that answer if it is similar to a human answer
		- Extension
			- Use vector based representations of the answers 
			- The coverage issues are less pronounced 
