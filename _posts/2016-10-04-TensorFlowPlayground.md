---
layout: post
title: "TensorFlow Playground"
description: ""
category: [technical]
tags: [ai , ml, tensorflow]
---
{% include JB/setup %}

Legend: 

Blue is a positive weight 

Orange is a negative weight

The dashed lines represent the weight matrix, in the interactive version one can hover over the inputs and outputs to see the magnitude of the weights learnt. 

Initialization of weights is completely random so it is not possible to reproduce these experiments under the exact same conditions. 


If we give input features as below, give abundant hidden units in one hidden layer and have two outputs as we have two kinds of inputs. Lets see what we can learn. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h1 | x1w1 - x2w2 |
| h2 | - x1w1 + x2w2 |
| h3 | x1w1 - x2w2 |
| h4 | x1w1 - x2w2 |

| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| -h1 -h2 +h3 -h4 |
|h22| +h1 +h2 -h3 +h4 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | -h21 + h22 |


![Image here](../images/12.png =550x)

Making the test samples more visible. The test samples have a solid outline of the same color. 


 <img src="../images/11.png" height="300" width="600"> 

Changing the regularization to L1 we notice that 


 <img src="../images/10.png" height="300" width="600"> 

Changing the regularization to L2 we notice that 

So, L2 can be considered a good regularizer for this data distribution. 


 <img src="../images/9.png" height="300" width="600"> 

Now we decrease the number of hidden units to just one. Given the data distribution we dont expect it to learn much because one single line or a linear classifier cant distinguish four clusters. 

 <img src="../images/8.png" height="300" width="600"> 


By increasing the number of output units we are not helping in learning and this is shown in the diagram below. 


 <img src="../images/7.png" height="300" width="600"> 

Increasing the number of hidden units does not help a lot because


 <img src="../images/6.png" height="300" width="600"> 

Experimenting on a different data distribution. Slightly more interesting data distribution. The learned classifier is not bad. It shows where the different test data points are clearly. 


 <img src="../images/5.png" height="300" width="600"> 

Now with two sinusoidal input distributions which are perpendicular to each other. The result is not a linear classifier but it classifies the test datapoints. 


 <img src="../images/4.png" height="300" width="600"> 

This distribution is like a x1 * x2


 <img src="../images/3.png" height="300" width="600"> 

By increasing the number of hidden units there is no increase or change in the classifiers. 


 <img src="../images/2.png" height="300" width="600"> 

By increasing the focus on some parts of the data distribution we can get a better classification. 


 <img src="../images/1.png" height="300" width="600"> 







| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h1 | + x1w1 + x2w2 |
| h2 | + x1w1 + x2w2 |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| -h1 -h2|


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | -h21 |


 <img src="../images/13.png" height="300" width="600"> 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h1 | + x1w1 + x2w2 |
| h2 | - x1w1 - x2w2 |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| -h1 -h2|


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | +h21|



 <img src="../images/14.png" height="300" width="600"> 



| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h1 | - x1w1 - x3w3 |
| h2 | +x1w1  - x2w2 |
| h3 | - x1w1 + x2w2 |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| -h1 -h2 -h3 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | -h21|




 <img src="../images/15.png" height="300" width="600"> 
 
 <img src="../images/16.png" height="300" width="600"> 



 <img src="../images/17.png" height="300" width="600"> 


 <img src="../images/18.png" height="300" width="600"> 



 <img src="../images/19.png" height="300" width="600"> 



 <img src="../images/23.png" height="300" width="600"> 




 <img src="../images/20.png" height="300" width="600"> 


 <img src="../images/21.png" height="300" width="600"> 

Just to check for the possible outputs. 

 <img src="../images/22.png" height="300" width="600"> 





This is an ongoing process and new interesting insights will be added. Most of these might be obvious to a lot of people, but I am noting them here because all these nitty grittes are really important in knowing how to fine tune the actual network. How the inputs get translated to the outputs and how the weights are being assigned. 