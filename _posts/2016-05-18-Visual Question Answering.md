---
layout: post
title: "Visual Question Answering"
description: ""
category: [technical]
tags: [vqa, qa, deep learning]
---
{% include JB/setup %}


# Does knowing the question help in image understanding?

#### Dataset

MS COCO VQA dataset 

#### Format

Image followed by its three questions-answers pairs.

#### Example

![](/images/coco1.png)

- Question: What is the mustache made of ?
- Inference: A male is present who has a mustache
- Truth: Girl is wearing banana mustache
- Other question: What color are her eyes? (Female with mustache can be inferred from this)

![](/images/coco2.png)

- Question: Do you like this house?
- Inference: Outdoor scene showing a house. 
- Truth: No help while answering other questions.
- Other questions: Who is riding a bike?, Is the boy on a skateboard?

#### Observations

- If the questions are independent then they dont help each other but maybe they can help in image understanding.
- Make a BOW model with the questions and then derive inferences to make one single description. This description can be appended to the image features.
- Use Stanford CoreNLP to convert question to description, this description might give some more information about image
- Use a captioning system to generate some assumed truth about the system and compare this with the questions. This will generate a different feature set. 
- If we use a BOW model, then we will need a vocabulary consisting of all possible words. Maybe a word embedding approach will work here. 
- How to use the given question categories (64)



