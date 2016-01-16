---
layout: post
title: "Learning a Recurrent Visual Representation for Image Caption Generation"
description: "Learning a Recurrent Visual Representation for Image Caption Generation"
category: [technical]
tags: [ai , ml, deep learning, frameworks]
---
{% include JB/setup %}


## [Learning a Recurrent Visual Representation for Image Caption Generation](http://arxiv.org/abs/1411.5654)

### Model Features 

+ Bi-directional mapping between images and their sentence based descriptions which are the captions are learnt using RNN?s.
+ Because of bidirectional nature the ability to generate caption given image and using same model to reconstruct the visual features given this visual description is possible.
+ The recurrent visual memory learns to remember long term visual concepts (sentence generation and visual feature reconstruction).
+ Dynamic representation within model
	-	 It captures the visual aspects of the scene as each new word is read and the representation is updated to reflect the new information.
+ The model uses special gating units for RNN language models so that they are able to learn long distance relations.
+ These dynamically updated visual representations act as long term memory of the concepts which were present before .
+ The network can saliently pick the concepts which convey the words which need to be spoken next.
+ The language model has around 3000 to 20,000 words. 
+ Word classing and a distribution of two terms is adopted as
	-	Prob(word) = Prob(class) * Prob(word \| class) 
+ The class label is learnt by unsupervised methods of grouping words of similar frequency together. 
	-	This accelerates the learning 
	-	Less loss of perplexity is present 
+ Likelihoods are computed using soft max function 
+ After each epoch the perplexity is reevaluated on a separate validation set
	-	Learning is reduced if perplexity does not decrease. 
+ Reduction is perplexity is necessary so, another step is taken for this purpose, the RNN model output is combined with Max Entropy Model which is learnt at the same time from the training set. 
+ The back prop of words is fixed at 3 for predicting the next word. 
+ Tokenization of the captions is done according to the Stanford CoreNLP tool and all text is converted to lower case letters. 


### Broadly the model can be broken down into two parts 

+ Generate the sentences using visual observations or features (Hence to find the likelihood of a word being generated at time t if the previously generated words are as in the given sentence and the observed visual features).
+ To find maximum likelihood of visual features given a set of spoken words. This is used to generate the visual representation of the scene or can also be used for image retrieval.

### Latent Variables

+ A latent variable is used that encodes the visual representation of the previous generated or read words, these are the long term memory cells.
+ A word at time t is represented by a one hot vector (1 or 0 depending on present or absent word).
+ The output from the latent variable is the likelihood of generating each word. 
+ The hidden state (which is introduced in this paper) gives the context based on the previous words (due to the problem of vanishing gradients it only can have short range interactions).
+ Adding an input layer whose visual features are constant / static, will help to the topic models or Part of Speech
	- In POS the input layer has to be dynamic as the words need direct access to the RNN

### Observations

+ Only half the static input layer is connected and this gives better results because different units can specialize in either text or visual features modeling. 
	- This special property would be lost if the entire hidden units were connected directly to the reconstruction layer because then the entire network would act as a normal autoencoder. 
+ The recurrent visual hidden layer which attempts to reconstruct the visual features from the previous words, is also used to predict the next word . 
	- Every time a word is generated the likelihood of the visual feature for that word is increased. 
	- Hence, the visual feature of that word is active and so, the network receives positive reinforcement to propagate the memory of the word from one time instance to the next. 
+ Rectified Linear Units with unbounded activations were numerically unstable and blew up in the RNNs.

### Learning
 
+ Back Propagation Through Time us used for learning. 
+ Network is unrolled for words and then BPTT is done.
+ The model is reset when end of sentence is reached
	- This ensures that the prediction does not cross sentence boundaries. 
	- Another measure to ensure is taking sample from a target sentence length (from the multinomial distribution of lengths learnt from the training data)
	- From this fixed length sampling of random sentences is done 
	- Finally, the lowest loss is the output 
+ Online learning for weights from RNN unite to output words used. 
+ Other parts of the network use once per sentence batch update. 
+ Activation for all units is calculated using sigmoid, unless softmax has been used before. 



In the previous approaches, sentences and images were mapped to a common embedding (aka joint feature approach) these were used for image searching or ranking image captions. 

These used 
 
- Kernel canonical correlation analysis
- RNN 
- Deep Networks

The disadvantage was that these were not able to perform inverse projections, they were not able to generate the image or sentence from embedding. 



### Ranking
 
- There is a non linear mapping between the entire image and sentence description.
- An objective function that (these may be present individually or in a combination)
	- Directly optimizes the ranking 
	- Adopts pre-trained representations to simplify learning 

### Evaluation 

- Sentence generation 
	- (state of the art) measured by BLEU and METEOR on PASCAL 1K
- Sentence retrieval 
	- (comparable to state of the art)
- Image retrieval 
	- (comparable to state of the art)

Evaluations were carried out on 

- PASCAL sentence dataset 
- Flickr 8K 
- Flickr 30K 
- MS COCO
