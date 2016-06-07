---
layout: post
title: "Visual Question Answering Experiments"
description: "Visual Question Answering"
category: [technical]
tags: [deep learning, ml, ai, nlp, word2vec, vqa, qa, summer2016]
---
{% include JB/setup %}


### Toolkit for Visual7W visual question answering dataset



`python predict_baseline.py --dataset visual7w-telling --mode open --topk 100 --split val --result_path results`

`parsed parameters:
{
  "result_path": "results",
  "split": "val", 
  "topk": 100, 
  "mode": "open", 
  "dataset": "visual7w-telling"
}`

`Initializing data provider for dataset visual7w-telling...`

`BasicDataProvider: reading datasets/visual7w-telling/dataset.json`

`writing predictions to results/result_visual7w-telling_open.json...`

--- 

`python evaluate.py --dataset visual7w-telling --mode open --topk 100 --split val --results results/result_visual7w-telling_open.json --verbose 1`

`Initializing data provider for dataset visual7w-telling...`

`BasicDataProvider: reading datasets/visual7w-telling/dataset.json`

`2016-05-26 17:10:20,488 Open-ended QA evaluation`

`2016-05-26 17:10:28,096 Evaluated 10,000 QA pairs...`

`2016-05-26 17:10:28,655 Evaluated 20,000 QA pairs...`

`2016-05-26 17:10:29,124 Done!`

`2016-05-26 17:10:29,124 Evaluated on 28,020 QA pairs with top-100 predictions.`
`2016-05-26 17:10:29,124 Overall accuracy = 0.370`
`2016-05-26 17:10:29,124 Question type "what" accuracy = 0.377 (5011 / 13296)`
`2016-05-26 17:10:29,124 Question type "who" accuracy = 0.377 (1086 / 2879)`
`2016-05-26 17:10:29,124 Question type "when" accuracy = 0.529 (668 / 1262)`
`2016-05-26 17:10:29,125 Question type "how" accuracy = 0.726 (3056 / 4211)`
`2016-05-26 17:10:29,125 Question type "where" accuracy = 0.100 (459 / 4590)`
`2016-05-26 17:10:29,125 Question type "why" accuracy = 0.051 (91 / 1782)`

---

`python predict_baseline.py --dataset visual7w-telling --mode mc --topk 100 --split val  --result_path results`

`parsed parameters:
{
  "result_path": "results", 
  "split": "val", 
  "topk": 100, 
  "mode": "mc", 
  "dataset": "visual7w-telling"
}`

`Initializing data provider for dataset visual7w-telling...`

`BasicDataProvider: reading datasets/visual7w-telling/dataset.json`

`writing predictions to results/result_visual7w-telling_mc.json...`

--- 

`python evaluate.py --dataset visual7w-telling --mode mc --topk 100 --split val --results results/result_visual7w-telling_mc.json --verbose 1`

`Initializing data provider for dataset visual7w-telling...`

`BasicDataProvider: reading datasets/visual7w-telling/dataset.json`

`2016-05-26 17:11:56,391 Multiple-choice QA evaluation`

`2016-05-26 17:11:56,392 top_k is set to 1 for multiple-choice QA`

`2016-05-26 17:11:56,993 Evaluated 10,000 QA pairs...`

`2016-05-26 17:11:57,041 Evaluated 20,000 QA pairs...`

`2016-05-26 17:11:57,081 Done!`

`2016-05-26 17:11:57,081 Evaluated on 28,020 QA pairs with top-1 predictions.`
`2016-05-26 17:11:57,081 Overall accuracy = 0.410`
`2016-05-26 17:11:57,081 Question type "what" accuracy = 0.367 (4886 / 13296)`
`2016-05-26 17:11:57,081 Question type "who" accuracy = 0.511 (1470 / 2879)`
`2016-05-26 17:11:57,081 Question type "when" accuracy = 0.644 (813 / 1262)`
`2016-05-26 17:11:57,081 Question type "how" accuracy = 0.408 (1719 / 4211)`
`2016-05-26 17:11:57,081 Question type "where" accuracy = 0.386 (1773 / 4590)`
`2016-05-26 17:11:57,082 Question type "why" accuracy = 0.465 (828 / 1782)`

---

`python predict_baseline.py --dataset visual7w-pointing --mode mc --split val --result_path results`

`parsed parameters:
{
  "result_path": "results", 
  "split": "val", 
  "topk": 5, 
  "mode": "mc", 
  "dataset": "visual7w-pointing"
}`

`Initializing data provider for dataset visual7w-pointing...`

`BasicDataProvider: reading datasets/visual7w-pointing/dataset.json`

`writing predictions to results/result_visual7w-pointing_mc.json...`

---

`python evaluate.py --dataset visual7w-pointing --mode mc --split val --results results/result_visual7w-pointing_mc.json --verbose 1`

`Initializing data provider for dataset visual7w-pointing...`

`BasicDataProvider: reading datasets/visual7w-pointing/dataset.json`

`2016-05-26 17:18:31,295 Multiple-choice QA evaluation`

`2016-05-26 17:18:31,764 Evaluated 10,000 QA pairs...`

`2016-05-26 17:18:31,811 Evaluated 20,000 QA pairs...`

`2016-05-26 17:18:31,860 Evaluated 30,000 QA pairs...`

`2016-05-26 17:18:31,894 Done!`

`2016-05-26 17:18:31,894 Evaluated on 36,990 QA pairs with top-1 predictions.`
`2016-05-26 17:18:31,894 Overall accuracy = 0.251`
`2016-05-26 17:18:31,894 Question type "which" accuracy = 0.251 (9296 / 36990)`