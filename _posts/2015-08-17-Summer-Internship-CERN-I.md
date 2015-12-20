---
layout: post
title: "CERN Openlab Summer Internship I"
description: ""
category: [technical, hackathon]
tags: [CERN, ml, data science ]
---
{% include JB/setup %}

## CERN Openlab Project

This summer I was humbled to have been chosen as an intern at the European Council for Nuclear Research, CERN, Canton of Geneva, Switzerland. I was in the Information Technology Databases, which is usually called IT-DB. My project was to evaluate Apache Spark as an analytics framework for CERN as Big Data Analytics Infrastructure. I had never used Apache Spark before. There was an EDx course which was teaching Apache Spark and I enrolled myself for it. I also read some books on Apache Spark, mainly, [Learning Spark](http://shop.oreilly.com/product/0636920028512.do) and [Advanced Analytics with Spark](http://shop.oreilly.com/product/0636920035091.do). 

The goal of this openlab summer student project was to analyse Apache Spark as a framework for the big data analytics framework of CERN. It utilizes MLlib and Spark Streaming along with Python and its libraries such as scikit-learn and scipy. The objective was to determine if the metadata of CMS can be analysed efficiently, in terms of CPU usage and time for completion of the job using Apache Spark. Apache Spark is a framework providing speedy and parallel processing of distributed data in real time. Additionally it provides powerful cache and
persistence capabilities. Because of these features Apache Spark is applied to data analytics problems. Components of Spark like Spark Streaming and MLlib (Spark native machine learning library) make analysis possible.

My mentors, Tony Wildish, Valentin Kuznetsov, Manuel Martin Marquez and Antonio Romero Marin were extremely helpful. They explained in great detail every single part of the project. We used to have continued discussions about the methodology, which algorithm to use and why, and this contributed greatly to my learning experience. I had not done 'atom smashing' with machine learning before. But I must say, I enjoyed it thoroughly and learnt a lot.

I will be describing in detail my project and the evaluation of Apache Spark for streamlining predictive models which use information from CMS data-services. The models are used to predict which datasets will become popular over time. This will help to replicate the datasets that are most heavily accessed, which hopefully will improve the efficiency of physics analysis in CMS. Analysing this data leads to useful
information about the physical processes. Reproducibility is necessary so that any process can be simulated just like the original in software at different times. Besides this, some process may be researched more by users and hence it needs to be made easily accessible to all the users. Accessibility is possible using replicas of data at some specified data centers. The user can then obtain the data from the nearest data center. Creating numerous replicas of every dataset is not feasible because of the datasets size. Maintaining and mirroring such vast datasets is an expensive job hence, the need of predicting which dataset might become popular is necessary.

The aim is to solve a classification problem which finds if a dataset will become popular or not. It includes calculating binary values of popular (1 / TRUE) or unpopular (0 / FALSE) of the 2013, 2014 and the currently producing 2015 data. The process of predicting popularity of datasets, hence which datasets' replicas should be created, is a machine learning problem. Hence, the aim of the problem is to use machine learning to predict which dataset will become popular and when. After finding which dataset is popular, it must be found out which machine learning algorithm suits the procedure the best. For this purpose three algorithms are employed, namely, Naive Bayes, Stochastic Gradient Descent and Random Forest. Additionally, these models are combined into an ensemble to check which algorithm offers the best true positive, true negative, false positive or false negative value. All this will lead to analysis of Apache Spark as a framework for parallel, real time processing of the distributed data that is abundantly available in CMS.

## Aims 

1. Define the popularity index.
	1. The target goal is to find the popular datasets, but what is a popular dataset?
	2. Which parameters define popularity of the dataset?
2. Apply machine learning algorithms for prediction of popularity.
3. Find the hardware configuration that gives the relatively best run of a machine learning algorithm.
4. Benchmarking of algorithms and hardware configuration that they support.
5. Generalize machine learning algorithms so that they can streamline CMS data without much data formatting. Create a pipeline or command line program that performs complete analysis with just the minimum configuration changes.
6. Develop ensemble of used algorithms.
7. Evaluate Apache Spark as an alternate framework for the complete analysis procedure.
8. Plot graphs displaying accuracy against time scale.



My interview also got published on [Internfeel](http://internfeel.com/europe/internship-experience-siddha-ganju-cern/).

Code [here](https://github.com/sidgan/LHCDataAnalysis)

## References
[Presentation regarding project](https://indico.cern.ch/event/365073/contribution/0/material/slides/1.pdf)
