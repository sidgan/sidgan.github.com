---
layout: post
title: "Adversarial Autoencoders"
description: "Adversarial Autoencoders"
category: [technical]
tags: [deep learning, ml, ai, nlp, paper review]
---
{% include JB/setup %}


[Alireza Makhzani, Jonathon Shlens, Navdeep Jaitly, Ian Goodfellow, Brendan Frey](http://arxiv.org/pdf/1511.05644v2.pdf)

	
## Autoencoder

Are used to optimize the reconstruction of the input at the output layers. So, whatever it got as the input, it wants to produce the same thing as the output. In an autoencoder there is one encoder and one decoder. The encoder takes the input and the decoder gives the output. The encoder encodes the input to some representation, this representation is important because it is fed to the decoder. The decoder upon receiving the encoded representation of the input will decode it back, or try to gauge what the original input was from the encoded input. Hence, it will try to produce something that is like the original input and tries to optimize this procedure. 

## Variational Autoencoders

The encoder-decoder is not a simple identity function, which is taken care of through the representation which the encoder spits out. It can have some compression or can assume some prior distribution. The ones that assume some prior distribution are called VARIATIONAL AUTOENCODERS. The decoders will be trained to reconstruct the input using a prior. The encoder can use the prior distribution to generate realistic data points for the original data space. 

Disdvantage of Variational Autoencoders: 

- An inherent disadvatage is that being based on a mapping there might be some data points that don't have any mapping to the real samples. 

	
## Adversarial Autoencoders	(AAE)

Adversarial Autoencoders do away with the inherent disadvantage of variational autoencoders because the encoder can fill the entire prior distribution. This allows the decoder to generate real looking samples from any data point as long as it is from the prior. 

### Terminology

We observe data x, a generative model G, a discriminative model D. D performs inference on G. 

D wants to give high probability or say that it is truth for samples in x which are actually from the emperical data distribution and give low probability or say that these are false samples and these come from the generative model. 

Emperical data distribution : p<sub>data</sub>(x)

Generative model : p<sub>g</sub>(x)

G wants to fool D into thinking that the samples it is producing are of extremely high quality and hence are the real truth. So it wants to generate data that is identical to or closely resembles the observed data. 

Prior of G : p(z)

Likelihood of G : p(x|z)

Minimax objective between D and G : min<sub>G</sub> max<sub>D</sub> E<sub>p<sub>data</sub>(x)</sub> [log D(x)] + E<sub>p<sub>g</sub>(x)</sub> [log(1-D(x))]

This alternates between D and G. 

First, find the optimal p<sub>g</sub>(x) among all possible G by minimizing the Jensen Shannon Divergence which is : JSD(p<sub>data</sub>(x) || p<sub>g</sub>(x)) = 1/2 (KL ( p<sub>data</sub>(x) || (p<sub>data</sub>(x) + p<sub>g</sub>(x))/2)) +  1/2 (KL ( p<sub>g</sub>(x) || (p<sub>data</sub>(x) + p<sub>g</sub>(x))/2))

This is like MLE because it minimizes : KL(p<sub>data</sub>(x) || p<sub>g</sub>(x))

Advantages of JSD:

- Balanced approximation
- Does not underfit or overfit
- Divergence is based on data distribution for x and NOT the latent variable distribution (z)
- A general divergence measure is being minimized
	
All this was used in GAN (Generative Adversarial Network), now, in Adversarial Autoencoders the divergence is minimized on latent variables (z). 

Reconstruction Error : E<sub>q(z|x)</sub> [-log p(x|z)]

Regularizer :  KL (q(z|x) || p(z))

Having the reconstruction error and regulizer gives : min<sub>q</sub> E<sub>q(z|x)</sub> [-log p(x|z)] + KL (q(z|x) || p(z))

Using this, the minimax becomes : min<sub>G</sub> max<sub>D</sub> E<sub>p(z)</sub> [log D(z)] + E<sub>q(z|x)</sub> [log(1-D(z))]

	Note: Everything is in terms of z or the latent distribution now. 

This alternates between the reconstruction error and the training error. 

Adversarial Autoencoders show visually better results than variational autoencoders. They map the encoders output distribution which is q(z|x) to an arbitrary prior distribution p(z). 

	Note: E denotes Expectation