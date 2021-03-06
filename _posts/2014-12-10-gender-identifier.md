---
layout: post
title: "Gender Identifier"
description: ""
category: [technical]
tags: [nlp, nltk, ml]
---
{% include JB/setup %}

## Name based gender identification using NLTK

This project is based on a simple idea that usually the female names end in vowels like 'a', 'e' and 'i', whereas male names usually end in 'k', 'o', 'r', 's' and 't'. Using this feature, we can generate a confidence value if the input name belongs to a male or a female. So far, I have not found any such study on Indian names and so decided to do one. The study on English names can be found [here](http://www.nltk.org/book/ch06.html). The English name corpus has been included in the 'names' package of NLTK. It can be used by:

<code>
from nltk.corpus import names
</code>

Indian names entail a much bigger challenge because sometimes same names are given to both girls and boys. My very name, 'Siddha' is both a girls and a boys name. Similar names include 'Harpreet'. The only way to gauge the gender for these cases is to rely on better training. 

### NLTK

Natural Language Processing though quite intense and arduous becomes manageable with the [Natural Language Tool Kit](http://www.nltk.org/), originally authored by Steven Bird, Edward Loper and Ewan Klein.

## Procedure

### Data Collection

I started by scraping a few websites that provided names of boys and girls and formatted the data into a csv file. Two separate data corpuses were made, one for the male and the second for female.

### Feature Extraction

The last alphabet of the word is the major distinguishing factor, hence, only that alphabet is extracted and used by the classifier.

### Technique

It's a supervised classification technique. In the training data set labels are provided that help to learn the classification. Naive Bayes Classifier has been used.

### Cross Validation

When provided with a data set, it is advisable to reserve part of it as a test data set so that the generated hypothesis can be tested. Usually a 70/30 or 60/40 division is used. So, 70/60 of the data is used in training and 30/40 in testing. Based on a similar analogy cross validation is implemented which enables the hypothesis generated from the training data set to be validated and worked upon to create a better and efficient hypothesis. For this a division of 60/20/20 is used. Training data constitutes 60%, cross validation set 20% and the testing data set another 20%. Cross validation is much in use because it provides a chance to fine tune the feature vector.

### Accuracy

Based on the test set we can measure the precision of the classifier using:

<code> print nltk.classify.accuracy(classifier, test_set) </code>

Initially we had a hypothesis stating that female names usually end in vowels like 'a', 'e' and 'i'. Whereas male names usually end in 'k', 'o', 'r', 's' and 't'. This was based on prior experience. Now let's see if this is actually true or not. Based on the corpus of data provided to the classifier it has generated its own hypothesis. It tells us based on which letters is it performing the classification.

<code> print classifier.show_most_informative_features(5) </code>
