---
layout: post
title: "Learning Knowledge Graphs for Question Answering through Conversational Dialog"
description: ""
category: [technical]
tags: [ai , ml, image captioning, paper review]
---
{% include JB/setup %}

## Learning Knowledge Graphs for Question Answering through Conversational Dialog

The open dialog system (called KNOWBOT) can learn about a domain by relating concepts in science question to propositions in a fact corpus (a knowledge base) and can store new concepts and relations within a knowledge graph. The knowledge is acquired from open and natural language dialogs without any knowledge of what the user might say. Hence, it is without any fixed ontology or structure or any domain model. This dialog learning is built on top of a question answering system that is able to refine knowledge from other sources. 

KNOWBOT is an open dialog system because a user utterance may progress the dialog task even though that underlying action is not explicitly represented in a dialog model. This helps in bootstrapping domain knowledge from the user without any of the engineering overload (which would have been in making the ontology or feature engineering). The features are dialog driven which means that each dialog gives its effective relations without annotations. This process is improved with each interaction. 

The dataset consists of science questions from 4th grade New York Regents exam. 

A concept keyword is a word in a sentence or a user utterance, which is not a stopword and adds some important information to the dialog. Concepts keywords are usually a related via a common root. Porter or Korvetz stemmers can be used to find keywords of the same family. In KNOWBOT, Porter Stemmer is being used. 

A relation is a pair of concepts that represent some semantic correspondence. These indicate some kind of relationship between the different keywords. These require a predetermined ontology to link salient features in the question to the words in the answer. The user usually provides any missing salient words in their answers which helps to re-enforce the confidence in the relations. These relations are arranged as a knowledge graph such that the nodes are the concepts and the edges are the relations. This knowledge graph grows with each dialog and develops commonsense semantic relations in open conversational dialogs. KNOWBOT uses task progress to drive NLU. This process is useful because as the dialog proceeds the confidence on the users chosen answer also increase. 

Sentence Alignments give the alignment score between the "ith" question answering statement and its supporting knowledge base sentence. It is the normalized number of relations between the concepts. This is the practical semantic similarity score that generalizes to different knowledge representations. 

The knowledge graphs are built at three levels: 

    - Utterance Level Knowledge Graph
    - Dialog Level Knowledge Graph
    - Global Knowledge Graph
    
### Utterance Level Knowledge Graph

All the concept pairs are related and pruned aggressively based on alignment and adjacency. The user explanation is converted to a fully connected knowledge graph which is noisy, because users don't purposely make relations between every pair of words they use. To get rid of this noise, pruning is done as: 

    - Alignment 
        + An edge can relate a question concept to a support concept.
    - Adjacency
        + An edge cant relate those concepts that are adjacent in the utterance. 

Singleton relations are pruned. This supports the fact that if any information is provided by the users, then it must be reiterated more than once, and hence we can conclude that important information and its relations are present more than once. 

### Dialog Level Knowledge Graph

An empty dialog level knowledge graph is initialized withe each starting conversation. After each users turn, edges are developed through the features and information that is learnt during the current turn. These new edges are added first to the utterance level knowledge graph and then to the dialog level knowledge graph. The dialog terminates when the system has accumulated enough information about the domain. This means that the system is able to converse about that topic and has built enough knowledge bases and graphs about that domain.  

### Global Knowledge Graph

It combines all the relations learnt from all the KNOWBOT's dialogs. This graph focuses on redundancy and aggressive pruning to remove noisy relations. Relations that re-occur again are salient to the problem. This again emphasis the fact that a feature said only once means that it has less significance. Hence, Global Knowledge graphs also ignore singletons. 

How many users at once can operate the system and provide conversational inputs