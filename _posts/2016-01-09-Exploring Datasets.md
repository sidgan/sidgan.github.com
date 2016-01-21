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

PASCAL stands for Pattern Analysis Statistical Modeling and Computational learning. It has 3 tasks: - Image Classification- Object Detection- Object SegmentationThe dataset has 20 classes, including aeroplane, bicycle, boat, bottle, bus, car, cat, chair, cow, dining table, dog, horse, motorbike, person, potted plant, sheep, train, TV.  For selecting this dataset, no quality filter was applied, the complete dataset has been directly downloaded from Flickr. Because of no filtering, there are complex scenes, scaling, view points of different objects, unnatural lighting. Training set consists of 10,103 images with 23,374 objects such that there are approximately 500 training objects per category. Each object is segmented completely with its bounding box. Standard evaluation method of average precision per class is used with train/test and validation splits. 
Some challenges include:
- Action Classification Taster Challenge 	- Given a bounding box predict whether the person in the bounding box is performing an action or not. 	- Action classes include, Calling, playing an instrument, reading, riding bike, riding horse, running, taking a photo, using the computer, walking, jumping and ?other? class. - Given the bounding box of a person, predict the spatial position of the head, hands and feet. This encourages research on image interpretation. 
### FLICKR 8K 

- Publically available dataset: http://nlp.cs.illinois.edu/HockenmaierGroup/8k-pictures.html
- The Flickr 8K dataset includes images obtained from the Flickr website. 
- University of Illinois at Urbana, Champaign has the sole link of this dataset. 
- The images do not contain any famous person or place so that the entire image can be learnt based on all the different objects in the image. 


### FLICKR 30K 

- This is an extension to the Flickr 8K. 
- Link: http://shannon.cs.illinois.edu/DenotationGraph/

Image search is based on associating the query text with the tags of the image that help to identify the image. Identification of images then becomes multi-label classification problem of associating images with individual words or tags. It is a much harder problem to automatically associate images with complete and novel descriptions of images such as captions. Multiple captions for each image are taken because there is a great amount of variance that is possible in the captions that can be written to describe a single image. This also helps satisfy the dynamic nature of images. There are multiple objects in the image but in a caption usually the main subject and either one or two of the secondary subjects are included in the caption.
	
### MS COCO 

- Link: http://mscoco.org/

This dataset does not focus on iconic views that contain just one view of a single object such that objects in the background, partially occluded and amidst clutter are also present and are important for image retrieval tasks. Iconic images contain a single subject within the image frame that is clearly defined and occupies most space within the image frame. The object would be complete or at least easily recognizable. Detailed spatial understanding of the object layout is a core component of scene analysis. An objects spatial location can be defined coarsely using a bounding box or with precise pixel level segmentations. Image datasets like ground truth stereo and optical flow datasets promote tracking of movement of one object from one frame to another. Three core problems in scene understanding that are presented in this paper are: 

- Detecting non-iconic views or non-canonical perspectives- Contextual reasoning between objects- 2D localization of objectsIt has instance level segmentation which means that the dataset has every instance of every object category labelled and fully segmented.Images features:
	
- Pair of objects in conjunction with images retrieved using scene based queries. 
- Labeling is done as the image containing a particular objet category using hierarchal labelling 
- Individual instances are labeled and verified and finally segmented Images count: 
	 - 91 common object categories with 82 having more than 50000 labelled instances. - 2,500,000 instances in 328,000 images - Fewer categories but more instances per category, which enables better learning and makes this a richer dataset on which the max score is less as compared to PASCAL dataset. - Number of labeled instances per image help in learning contextual information Datasets can be addressed to one out of three kinds of problems:- Image classification 
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
