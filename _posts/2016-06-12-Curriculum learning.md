---
layout: post
title: "Curriculum learning"
description: "Curriculum learning"
category: [conference]
tags: [deep learning, ml, ai, nlp, paper review]
---
{% include JB/setup %}

### [Yoshua Bengio, Jerome Louradour, Ronan Collobert, Jason Weston](http://ronan.collobert.com/pub/matos/2009_curriculum_icml.pdf)

The basic idea is:

	Start Simple then Simplify

When we are being taught, we are given easier examples first and then the level of difficulty is increased. This is a really cool idea. Its something that is so natural in real life and is applied in neural networks. 

True in biology as well, we are given weak strains of virus so that our platelets can learn to fight against the actual much stronger virus. I think this is the general idea of what a vaccine is, I can surely be wrong though thanks to my limited knowledge of medicine and biology. 

Curriculum learning has an effect on speed of convergence and can be seen like the continuation method which is a general strategy for global optimization. It is about guiding the neural network to ensure that it is learning in the best possible way. 
	
Could Occams Razor be related to this idea? This is something to think about. 
