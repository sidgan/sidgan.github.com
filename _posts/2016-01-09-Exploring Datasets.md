---
layout: post
title: "Exploring Image Captioning Datasets"
description: ""
category: [technical]
tags: [ai , ml, datasets, image captions]
---
{% include JB/setup %}

 
### PASCAL SENTENCE DATASET 

- Link: http://vision.cs.uiuc.edu/pascal-sentences/

PASCAL stands for Pattern Analysis Statistical Modeling and Computational learning. It has 3 tasks: 


### FLICKR 8K 

- Publically available dataset: http://nlp.cs.illinois.edu/HockenmaierGroup/8k-pictures.html
- The Flickr 8K dataset includes images obtained from the Flickr website. 
- University of Illinois at Urbana, Champaign has the sole link of this dataset. 
- The images do not contain any famous person or place so that the entire image can be learnt based on all the different objects in the image. 


### FLICKR 30K 

- This is an extension to the Flickr 8K. 
- Link: http://shannon.cs.illinois.edu/DenotationGraph/

Image search is based on associating the query text with the tags of the image that help to identify the image. Identification of images then becomes multi-label classification problem of associating images with individual words or tags. It is a much harder problem to automatically associate images with complete and novel descriptions of images such as captions. 
	
### MS COCO 

- Link: http://mscoco.org/

This dataset does not focus on iconic views that contain just one view of a single object such that objects in the background, partially occluded and amidst clutter are also present and are important for image retrieval tasks. Iconic images contain a single subject within the image frame that is clearly defined and occupies most space within the image frame. The object would be complete or at least easily recognizable. Detailed spatial understanding of the object layout is a core component of scene analysis. An objects spatial location can be defined coarsely using a bounding box or with precise pixel level segmentations. Image datasets like ground truth stereo and optical flow datasets promote tracking of movement of one object from one frame to another. 

- Detecting non-iconic views or non-canonical perspectives
	
- Pair of objects in conjunction with images retrieved using scene based queries. 
- Labeling is done as the image containing a particular objet category using hierarchal labelling 
- Individual instances are labeled and verified and finally segmented 
	 
	- Binary labels that indicate if a image belongs to a category or not. 
- Object detection
	- Detect if an object is present and if present to what class of objects does it belong to.
	- After detecting an object, localize its position within the image
	- It is difficult to detect objects that are not in their natural surroundings 
- Semantic scene labeling
	- Each pixel of an image is to be labeled as belonging to a category 
	- This enables the labeling of objects for which instances are hard to define

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