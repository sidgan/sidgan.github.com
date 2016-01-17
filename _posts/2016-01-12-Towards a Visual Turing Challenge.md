---
layout: post
title: "Towards a Visual Turing Challenge"
description: ""
category: [technical]
tags: [ai , ml, datasets , image captions]
---
{% include JB/setup %}


## [Towards a Visual Turing Challenge]( http://arxiv.org/abs/1410.8027)

A Visual Turing test is an open domain task of question answering based on real world images that resembles the the Turing Test. 

This is inspired from the holistic architectures for challenging grounding, natural language generation from image and video, image to sentence alignment and question answering problems. 


### Evaluation

-	Interpreting and evaluating the answer of a system becomes difficult and ideally relies on human judgment 
-	However, these are not objective methods that can?t be evaluated automatically at a large scale. 
-	The evaluation methodology that assigns scores over a large output domain is challenging as the system which is based on ontologies has limited domain. 
-	Human judgment has its inherent ambiguities so, if the aim is to mimic human response then these ambiguities are always present. 
	- These are affected by binding, reference frames, social conventions but are not limited to the affect of these. 
-	So, the better evaluation metric is to take majority voting or social consensus.
	- This incorporates agreement amongst humans in the metric.

### Challenges 

#### Vision and Language 

- These inculcate the ground of any representation in the external world and are a reference point for machines and humans. 
- Humans think in terms of spatial and temporal concepts
- Humans are able to understand and make sense of thousands of concepts at once, so an architecture that tries to reproduce the human behavior for vision and language must be able to 'think' and realize 'ideas' or concepts with the same diversity and complexity. 
	- Concept Ambiguity 
		- The semantic boundaries between two concepts are fuzzy 
		- Results in introduction of some ambiguities
		- According to the Prototype theory, this is referred to the Gradual category membership in the human perception. 
		- EG: being able to differentiate between Fiji apples and Granny Smith apples. 

#### Common sense knowledge 

-	The answer to some questions do not require critical thinking but instead require commonsense knowledge. 
-	This requires understanding which objects are present in an image, relations between these objects and their locations. 
-	EG: Question: The book on top of the table is next to what object?
-	Commonsense knowledge has different parts and each may be used with different modalities. 
-	Objects that often co-occur together, like a knife and fork next to a plate are components of what can be learnt using visual based commonsense knowledge. Learning that these are utensils requires more knowledge. 

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
