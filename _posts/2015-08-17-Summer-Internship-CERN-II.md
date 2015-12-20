---
layout: post
title: "CERN Openlab Summer Internship II"
description: ""
category: [technical, hackathon]
tags: [CERN, ml, data science ]
---
{% include JB/setup %}

## Dataset

A dataset describes a process completely. A process is any interaction taking place in the LHC.
An example would be proton-proton collision in the LHC, taking place at a single vertex. A
single process may be composed of many collisions taking place at the same vertex. The weekly
collection of data is uniquely represented by the name of the dataset. It describes which weeks
data it contains, 20140101 - 20140107 will describe the first week of year 2014.
A datasets format is defined by three distinct parts process/software/tier, where:

- process: is a process type, examples include Higgs Process, TopQuark, ttbq
- software: is the software used and its version/release number. It is important for reproducing results.
- tier: defines the tier. There are many different tiers but the most important ones are: {AOD, AODSIM, MINIAOD, MINIAODSIM, USER}

CMS produces nearly 300 Mb of data per second. That is a lot of data that might need to be processed. However, only a part of this data requires analysis. The important data that requires processing is stored for future reference. This data consists of relatively important information that is new and has not been obtained before. The data from one week is recorded as a dataframe. Each data frame name is unique and is recorded with the week in which it is produced in. One dataframe is defined by its attributes. These are approximately 84 features. After selecting relevant features, the feature list comes down to 26. Relevant features are selected by removing sparse columns. The final list of the 26 features comes out to be: id, cpu, creator, dataset, dbs, dtype, era, naccess, nblk, nevt, nfiles, nlumis, nrel, nsites, nusers, parent, primds, proc_evts, naccess, rnusers, rtotcpu, size, tier, totcpu and wct. Feature extraction is essential because not all the columns contribute towards making a dataset popular. Features remain consistent irrespective of frames. Using these features a dataframe can be identified uniquely. It is necessary to note that for this analysis metadata of the CMS data is being used.


It is necessary to define numeric values for naccess, nusers, totcpu for popularity metrics. Popularity is defined as which datasets are used for research most of the time. These are considered “popular” because they are demanded by many agencies and hence must be replicated at various data centres around the world. Popularity can be found by making plots for naccess, nusers, totcpu distributions. These explain the distribution of naccess, nusers and totcpu with the remaining parameters. Plots are made on the log scale so that all values can be plotted on a small scale Y axis. Plots are superimposed to know the correlation between different parameters. After calculating the value of the cut, apply that cut to facilitate conversion to a classification problem. Cut will help in deciding which is popular and which not popular category is. Cuts need to be applied to naccess, nusers, totcpu. Cuts act as threshold values and indicate a set is popular if its value is above the threshold cut value and not popular otherwise.

Conclusion for cuts:

- threshold_nusers = 5
- threshold_naccess = 10

Both these cuts are applied together. In the code they are implemented with a logical AND. The plot below describe the popularity metric “naccess”



## Popular Datasets

### Why are popular datasets necessary?
- Help in providing expeditious access to datasets that might be required
- Help in finding which might become the ‘hot topics’ in high energy physics. 

### What is a popular dataset ? 
Based on the data collected, some parameters such as nusers, naccesses and tot_cpu can be said to define popularity because the curve between all the parameters and popularity is mostly dependent on them. To find the numerical value of the threshold limit beyond which a dataset is termed popular, a graph is plotted. This graph is plotted on the log scale so that all values can be plotted within the region represented by the graph.

The access to files from all CMS analysis centres is recorded in a central database (PopularityDB). This data is pulled out in week-sized chunks for analysis, and stored in a dataframe as the input to the ML algorithms. Currently used popularity metrics as reported by the PopularityDB are:

- naccess - number of accesses to a dataset
- totcpu - number of CPU hours utilized to access a dataset
- nusers - number of users times days when the dataset was accessed

### Classification Problem

Based on the values of naccess and nusers, a classification problem can be developed. The target column gets a value of 1 (popular) when naccess is greater than 10 and nusers is greater than 5.

````
def convert(def):
	threshold_naccess = 10
	threshold_nusers = 5
	return df['naccess'] > threshold_naccess and df['nusers'] > threshold_nusers
````
