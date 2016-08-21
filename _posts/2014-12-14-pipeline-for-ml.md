---
layout: post
title: "Pipeline for ML"
description: ""
category: [technical]
tags: [machine learning]
---
{% include JB/setup %}

## Command Line Pipeline for Machine Learning Problems

This project deals with aggregating methods for machine learning. Machine learning is a broad spectrum term. It involves churn prediction, recommendation systems and time series analysis just to name a few.  

Initially I had to work on [Kaggle](http://www.kaggle.com/) problems trying to gain first hand experience at cleaning data and figuring out what are the most efficient algorithms on which kinds of problems. The first problem that I started on was the Titanic Trainer Challenge. My first prediction lay at a mere 50\%, barely, just touching the last position. However, continually working on the predictions and using the scikit package provided by Python I was able to come up to the 191st position. Through this exercise I learnt the intricacies of data cleaning and that multiple imputation is extremely vital. 

<br/>
<img src ="/images/first_submission.png" style="width:600px;height=500px">
<br/>
<img src ="/images/spot.png" style="width:600px;height=500px" >
<br/>
<img src ="/images/final_submission.png" style="width:600px;height=500px">
<br/>

This exercise was actually fun. I played around with the python scikit packages and learnt a lot. While working on the problem, I found myself devoting time to data cleaning more than expected. Afterwards, hours on experimental tuning. I came across a few articles and blogs on the net which shared these thoughts as well. Some even provided an outline of such an 'automated pipeline'. I was intrigued and decided to get my hands dirty.  In order to make an automated pipeline the only thing that could be done automatically, was to take the output from one machine learning stage and provide it as input to another. Data Cleaning cannot be performed automatically and efficiently as of now because this requires user intervention. However, in this module the user can manually enter the labels of those columns which are categorical and thus, these can be converted into numerical values. The remaining text data from which no structure can be inferred e.g. 'Name' cannot be used, unless it is parsed first, and then the salutations extracted. A way around this is to use dummy variables, given by the function get_dummies(). Other methods include using One Hot Encoding.

In order to build a simple command line application initially, I used the optparse package with Python. I had to take in the options using the command line and process each of them to see what kind of a problem the user had specified. The user would input 'clu' for 'clustering', 'c' for 'classification', 'd' for 'dimensionality reduction', 'r' for 'regression' and accordingly. I would pass the input data into the pipeline. Other options included imputation method, by mean or by median. Also, if the user does not provide the options, then he is asked to input the options separately.

It is possible to adapt Machine Learning with command line, because output of one stage serves as the input of the next. There are no changes required to be performed on the output. Also, the main steps in any machine learning problem are pretty much the same. Now, with minimum configuration changes, it will be possible to run almost any problem. The performance of this process is as good as the data that is being provided to it. If data is clean and devoid of NaN values, then prediction quality will be better. 

I started by building a simple command line application. Initially, I used the optparse package with Python. Python is a fun language to work with. It has numerous packages thanks to the great open source community and ample help is provided on several forums. The work seemed good. I had to take in the options using the command line and process each of them to see what kind of a problem the user had specified. The user could say 'clustering', 'classification', 'dimensionality reduction', 'regression' and accordingly I would pass the input data into the pipeline. Other options included imputation method, by mean or by median. 

It worked out pretty well because in machine learning output of one stage serves as the input of the next. Also, the main steps in any machine learning problem are pretty much the same. Elucidating, first is the training of the algorithm, then testing and finally cross validation. Now, with minimum configuration changes, it will be possible to run almost any problem. This gets as good as the data that is being provided to it. If data is clean and devoid of nan values then definitely better prediction will take place. By doing this project I even learnt the various methods of detecting the sources of nan values. These can be random, independent. This was by far the most daunting task. Once, I ended by experimenting so wickedly that all I had in the end was nan values. Columns full of just nan values. I somehow (due to an error in the code) managed to turn the originally non-nan values into nan. What a nightmare that was! 

It seemed a good idea to produce a report from each phase and based on the data produced manually add/remove any parameter. I listened to talks from PyCon, KDD, Texata and a lot of them emphasised the importance of giving clean data. The algorithm gives the best results when you provide it with the best data. I don't think that I have been able to achieve that level of efficacy in data cleaning that I would be able to make a machine do the cleaning automatically. But, its the algorithm tuning part that the computer can do efficiently, so let the machine do what it's best at and the rest, a person can handle. 

It is definitely easier to work with a graphical user interface and that is where I am headed. Further development will entail a GUI, which will be cross platform. 