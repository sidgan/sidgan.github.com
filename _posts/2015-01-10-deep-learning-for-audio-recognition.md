---
layout: post
title: "Deep Learning for Audio Recognition"
description: ""
category: [technical]
tags: [deep learning]
---
{% include JB/setup %}

<h1> Deep Learning </h1>
Deep learning is also called deep structural learning or hierarchical learning. It is a set of algorithms in machine learning that attempts to model high-level abstractions in data by using model architectures composed of multiple non-linear transformations. It is
the part of a broader family of machine learning methods based on learning representations of data. Various deep learning architectures such as deep neural networks, convolutional deep neural networks, and deep belief networks have been applied to fields like computer vision, automatic speech recognition, natural language processing, and music/audio signal recognition and these have produced state-of-the-art results on various tasks.

Recently, I learnt about [Deep Speech](http://www.forbes.com/fdc/welcome_mjx.shtml) developed by [Baidu](http://www.baidu.com/). They employed a much bigger data set on powerful algorithm and a recurrent neural network. They have used a massive GPU based deep learning infrastructure to train a data set of 100,000 hours of speech data especially for noisy situations.

The main objective of this project is to make an automatic audio recognition system which can sense and interpret the appropriate sounds from the surrounding and show the text, displaying the kind of sound perceived. It is basically classification of sounds and displaying the spoken words on screen in case of speech using deep learning. The work in this project is divided into two parts:
<ul>
<li>
Classification of sounds
</li>
<ul>
<li>
Classification based on human and non-human sounds
</li>
</ul>
<li>
Displaying the spoken words
</li>
<ul>
<li>
Display the words that can be interpreted, if they are of human origin
</li>
</ul>
</ul>


<h2>Data Collection </h2>
The data which includes the .wav audio files have been downloaded from various sources on the internet. These are available under free license of Creative Commons. .wav files are used because they have all the features present in the files and are not compresses
unlike other file formats.
Sites:
<ul>
<li>
Soundjay.com
</li>
<li>
Wavsource.com
</li>
<li>
Freesound.org
</li>
</ul>

<h2>Spectrograms</h2>

A spectrogram is a visual representation of the spectrum of frequencies in a sound or other signal as they vary with time or some other variable. Spectrograms are sometimes called spectral waterfalls, voiceprints, or voice grams. Spectrograms can be used to identify spoken words phonetically, and to analyses the various calls of animals. They are used extensively in the development of the fields of music, sonar, radar, and speech processing, seismology, etc. The instrument that generates a spectrogram is called a spectrograph. 


<h2>Generation of Spectrograms</h2>

Using the a [Fast Fourier Transform](http://en.wikipedia.org/wiki/Fast_Fourier_transform) (FFT) algorithm to compute the [Discrete Fourier Transform](http://en.wikipedia.org/wiki/Discrete_Fourier_transform) (DFT) and its inverse. Fourier analysis converts time (or space) to frequency and vice versa; an FFT rapidly computes such transformations by factorizing the DFT matrix into a product of sparse (mostly zero) factors. As a result, fast Fourier transforms are widely used for many applications in engineering, science, and mathematics. The basic ideas were popularized in 1965, but some FFTs had been previously known as early as 1805. Fast Fourier transforms have been described as "the most important numerical algorithm of our lifetime". The spectrograms generated in this module follow the normal convention of having frequency (in Hertz) on the vertical axis and time on the horizontal axis. Intensity is denoted by the darkness, saturation and hue of the colors. It is best to convert the audio files into spectrograms because they maintain all the properties such as bandwidth, frequency, pitch, resonance and the variation of frequency with bandwidth can be visualized. In this project we have utilized the pyaudio packages for producing the spectrograms.

<h3>Using Timeside for Spectrogram generation</h3>

TimeSide is a set of python components enabling low and high level audio analysis, imaging, and transcoding (conversion of one digital code to another) and streaming. Its high-level API is designed to enable complex processing on large datasets of audio and
video assets of any format. Its simple plug-in architecture can be adapted to various use cases. TimeSide also includes a smart interactive HTML5 player which provides various streaming playback functions, formats selectors, fancy audio visualizations, segmentation and semantic labeling synchronized with audio events. It is embeddable in any web application. In the generated spectrogram which is a representation of the spectrum frequencies in a sound.
<ul>
<li>
Horizontal axis represents time
</li>
<li>
Vertical axis represents frequency
</li>
<li>
Color represents amplitude
</li>
</ul>

<h3>Using pylab and audiolab</h3>

<h3>Using pylab as an alternative method</h3>

Classification of sounds using Deep Learning involves spoken language understanding (SLU) which can be classified into the following majors:
<ul>
<li>
Domain classification
</li>
<li>
Intent detection
</li>
<li>
Semantic slot filling
</li>
</ul>

A major hurdle in performing SLU is the huge variability of spoken language.

<h3>Domain and intent classification </h3>
This is included within semantic utterance classification (SUC) such that, C=argmax(c)P(C|X) Where, C=c1, ....cm belong to one of the M semantic categories (e.g., domain or intent) and X is the input utterance. SUC handles n-gram as raw features. N-grams are based
on the phonetics and common occurrence of two alphabets together. As an example, a bi-gram set would include “th”, “at”, “in”, and several others. Similarly, a tri-gram set will include “ing”, “ion”, “eat” among others. These are necessary for POS tagging. The
classifiers that are used in SUC are logistic regression, boosting and support vector machines (SVM). 

<h3>Semantic slot filling</h3>

It is a sequential tagging problem. POS tagging is part-of-speech tagging and tags a word to its part of speech, hence creating a mapping of words with a set as {noun, verb, adverb, pronoun}.

<h2>Algorithms used</h2>

<ul>
<li>
AdaBoost
</li>
<li>
Naïve Bayes Classification
</li>
<li>
Random Forest Classifier
</li>
<li>
Gradient Boosting
</li>
<li>
SGD regression
</li>
<li>
KN classification
</li>
<li>
Decision tree classifier
</li>
<li>
Logistic Regression
</li>
</ul>
