---
layout: post
title: "TensorFlow Playground"
description: ""
category: [technical]
tags: [ai , ml, tensorflow]
---
{% include JB/setup %}

## TensorFlow Playground

This post is an effort to understand how neural networks work. The visualizations  are images obtained by experiments using [TensorFlow Playground](http://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.53049&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false). Kudos to TensorFlow for making such an amazing framework! 

Right now, I have added the experiments that I found the most interesting. Learning is an ongoing process and new interesting insights will be added. Most of these might be obvious to a lot of people, but, I am noting them here because all these nitty grittes are really important in knowing how to fine tune the actual network, or in other words, how the inputs get translated to the outputs and how the weights are being assigned. If there are any errors please point them out and I will fix them. 

Note that the initialization of weights is completely random so it is not possible to reproduce these experiments under the exact same conditions but similar results might be possible.  

### Legend for experiments

Blue is a positive weight or input. (Understand as overlap)

Orange is a negative weight or input.  (Understand as intersection)

The dashed lines represent the weight matrix, in the interactive version one can hover over the inputs and outputs to see the magnitude of the weights learnt. 

The tables give the learnt equations for:

- Input units (x1, x2, sin(x1), sin(x2), x1x2 which is denoted as x3, x1^2, x2^2)
- Weights for Input units (w1.....wn)
- Hidden units in First hidden layer (h11...h1n)
- Weights for First hidden layer (w11.....w1n)
- Hidden units in Second hidden layer (h21.....h2n)
- Weights for Second hidden layer (w21.....w2n)
- Output units (o1.....on)

These equations are useful for predicting what you think the output should look like and what the neural network outputs. This is a good thought experiment so I have included the equations that I came up with as well. I used the equations using simple digital logic rules and gates. 

### Understanding Overlap

Here's how I understood the overlap idea, manually using paper and pen(cil), draw the distributions, remove the ones that have negative weight by performing an intersection of sets, and similarly, when there is positive or overlap add those distributions. 

### Experiments

#### 1

If we give input features as below, give abundant hidden units in two hidden layers and have two outputs as we have two kinds of inputs. Lets see what we can learn. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h11 | x1w1 - x2w2 |
| h12 | - x1w1 + x2w2 |
| h13 | x1w1 - x2w2 |
| h14 | x1w1 - x2w2 |

| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| -h11w11 -h12w12 +h13w13 -h14w14 |
|h22| h11w11 +h12w12 -h13w13 +h14w14 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | -h21w21 + h22w22 |

 <img src="/images/12.png" height="300" width="600"> 



#### 2

Making the test samples more visible. The test samples now have a solid outline of the same color which helps in better understanding. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h11 | x1w1 - x2w2 |
| h12 | - x1w1 + x2w2 |
| h13 | x1w1 - x2w2 |
| h14 | x1w1 - x2w2 |

| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| -h11w11 -h12w12 +h13w13 -h14w14 |
|h22| h11w11 +h12w12 -h13w13 +h14w14 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | -h21w21 + h22w22 |


 <img src="/images/11.png" height="300" width="600"> 
 

#### 3

Changing the regularization to L1 we notice that only one part of the data distribution can be identified by the classifier. This was expected because L1 acts like a rectifier and keeps only the positive parts alive. L1 is a measure of the least absolute deviation from the target values. L1 gives a smaller magnitude of error and is robust, however it will not try to fit the errors. 


| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h11 | - x1w1 + x2w2 |
| h12 |  x1w1 + x2w2 |
| h13 | x1w1 + x2w2 |
| h14 | - x1w1 - x2w2 |

| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 -h12w12 -h13w13 -h14w14 |
|h22| - h11w11 - h12w12 -h13w13 +h14w14 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | +h21w21 - h22w22 |


 <img src="/images/10.png" height="300" width="600"> 
 

#### 4

Changing the regularization to L2 which minimizes the least square error, we notice that the output is much better classified. This again was as expected because the L2 loss penalizes the outliers and because of the square term outputs an even larger loss value. So, L2 can be considered a good regularizer for this data distribution and this also serves as a confirmation that the L2 loss is sensitive to outliers. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | + x1w1 - x2w2 |
| h12 | - x1w1 - x2w2 |
| h13 | - x1w1 + x2w2 |
| h14 | - x1w1 + x2w2 |

| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 - h12w12 - h13w13 - h14w14 |
|h22| - h11w11 + h12w12 + h13w13 - h14w14 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | +h21w21 - h22w22 |


 <img src="/images/9.png" height="300" width="600"> 
 

 
#### 5




Now, we decrease the number of hidden units to just one. Given the data distribution we dont expect it to learn much because one single line or a linear classifier cant distinguish four clusters. 


| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h11 | + x1w1 + x2w2 |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 |



| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21 |


 <img src="/images/8.png" height="300" width="600"> 



#### 6

By increasing the number of hidden units in the second layer we are not helping in learning and this is confirmed as shown in the diagram below. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | - x1w1 - x2w2 |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| - h11w11  |
|h22| - h11w11  |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | + h21w21 + h22w22 |


 <img src="/images/7.png" height="300" width="600"> 
 
 


#### 7

A similar experiment by increasing the number of hidden units in the first hidden layer. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | - x1w1 - x2w2 |
| h12 | - x1w1 + x2w2 |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 - h12w12 |
|h22| - h11w11 - h12w12 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | + h21w21 + h22w22 |

 <img src="/images/6.png" height="300" width="600"> 
 
 
 

#### 8

Now, we experiment on a different data distribution. Slightly more interesting data distribution. The learned classifier is not bad. It shows where the different test data points are clearly. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | - sin(x1)w1  |
| h12 | - sin(x1)w1  |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 + h12w12  |
|h22| - h11w11 - h12w12  |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21 + h22w22 |


 <img src="/images/5.png" height="300" width="600"> 
 


#### 9

Now, with two sinusoidal input distributions which are perpendicular to each other. The result is not a linear classifier but it classifies the test datapoints. This I find very interesting because it confirms the fact that a neural network is like an complex network which can solve problems in which the data is not linearly separable. 


| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | - sin(x1)w1   - sin(x2)w2  |
| h12 | + sin(x1)w1   + sin(x2)w2 |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| - h11w11 + h12w12  |
|h22| - h11w11 - h12w12  |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | + h21w21 + h22w22 |


 <img src="/images/4.png" height="300" width="600">
 


#### 10 

This data distribution is like a x1 * x2, so let this be denoted be x3 and its corresponding weight by w3. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | - x3w3 |
| h12 | - x3w3  |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 - h12w12  |
|h22| - h11w11 - h12w12  |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21 - h22w22 |


 <img src="/images/3.png" height="300" width="600"> 
 


#### 11

By increasing the number of hidden units, there is no increase or change in the classifiers which is as expected through the equations. 


| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | - x3w3 |
| h12 | + x3w3  |
| h13 | + x3w3  |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| - h11w11 + h12w12  + h13w13|
|h22| + h11w11 + h12w12  - h13w13|



| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21 + h22w22 |


 <img src="/images/2.png" height="300" width="600"> 
 
 


#### 12

By increasing the focus on some parts of the data distribution we can get a better classification. Think about this as an overlap between the two inputs x2 and x3. 



| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | - x2w2 + x3w3 |
| h12 | - x2w2 + x3w3  |



| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 - h12w12  |




| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21  |






 <img src="/images/1.png" height="300" width="600"> 
 
 


#### 13

This is for a new series of experiments with a slightly cleaner data distribution. The inputs are x1 and x2, there are two hidden layers. The test loss and training loss are both 0.0! A good case of overfitting! The model is being fitted on an easy and linearly separable dataset with too many hidden units and hidden layers. Its good to remember that a general thought experiement is to overfit on the training set just to make sure that we are able to learn. 

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


 <img src="/images/13.png" height="300" width="600"> 
 


#### 14

Changing the data distribution helps to add a little noise (I'm not sure if noise is the right word here), it adds some sort of disturbance but not noise in the actual sense of bad input. 


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



 <img src="/images/14.png" height="300" width="600"> 





#### 15

With the same data distribution we aim at building a better classifier. The experiments for these are below: 
 

#### 16

To aid in this process, lets use another hidden unit in the first layer. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h11 | - x1w1 - x3w3 |
| h12 | + x1w1  - x2w2 |
| h13 | - x1w1 + x2w2 |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| - h11w11 - h12w12 - h13w13 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21|



 <img src="/images/15.png" height="300" width="600"> 

 


#### 17

Now, remove the added unit as it does not seem to help and add another unit to the second hidden layer. This might help because its like adding another level of knowledge on top of the first hidden layer. Using the visualizations we see that the hunch was correct and it has helped. 
 
 
| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h11 | - x1w1 + x2w2 |
| h12 | + x1w1  - x2w2 |



| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 + h12w12  |
|h21| - h11w11 - h12w12  |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | + h21w21  - h21w21  |


 <img src="/images/16.png" height="300" width="600"> 




#### 18

But were the better results because of adding the extra hidden unit ? or just decreasing the hidden unit from the first hidden layer? Also what is the minimum number of units per layer that we can use to learn this data distribution. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
|  h11 | + x1w1 + x2w2 |
| h12 | - x1w1  - x2w2 |



| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 + h12w12  |



| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21  |


 <img src="/images/17.png" height="300" width="600"> 



#### 19

Now we change the input features again. Focus on the training and test loss and see that both undergo oscillations but still the test error is still alright in comparison to the training error. What I mean by this is that the test error is almost near the ceiling created by the training error. The weight of x1^2 is given by w3. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | + x1w1 - x2w2 - x1^2w3|
| h12 | - x1w1  - x2w2   + x1^2w3 |



| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| - h11w11 - h12w12  |



| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21  |



 <img src="/images/18.png" height="300" width="600"> 



#### 20 

Focus on the training and test loss and see that both undergo a lot of oscillations. This is expected because if we try to overlap the three inputs we see that the distribution of the blue weights or positive data points is almost everywhere which will confuse the classifier and cause it to oscillate a lot. Recall how a perceptron works and in the end each is a linear classifier.  


| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | + x1w1 - x2w2 - x1^2w3|
| h12 | - x1w1  - x2w2   + x1^2w3 |



| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| - h11w11 - h12w12  |
|h22| + h11w11 + h12w12  |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21 + h22w22 |



 <img src="/images/19.png" height="300" width="600"> 



#### 21

Add x2^2 as well, weight denoted by w4. 


| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | + x1w1 - x2w2 + x1^2w3 - x2^2w4 |
| h12 | + x1w1  + x2w2   + x1^2w3  + x2^2w4|



| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 + h12w12  |
|h22| + h11w11 - h12w12  |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | - h21w21 + h22w22 |


 <img src="/images/23.png" height="300" width="600"> 




#### 22

Keeping the same distribution, we remove the x1^2 and x2^2. We should get something similar to the experiments we have already seen before. 

| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | - x1w1 + x2w2 |
| h12 | + x1w1  - x2w2 |



| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| + h11w11 + h12w12  |
|h22| - h11w11 - h12w12  |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | + h21w21 - h22w22 |




 <img src="/images/20.png" height="300" width="600"> 



#### 23

This part was just to check for the possible outputs. The input distribution is *really* hard!!!! The test loss is much higher and does not decrease as much as the training loss does, which is as expected. 

- x3 denotes x1x2 and weight is by w3
- w1 denotes weights for sin(x1)
- w2 denotes weights for sin(x2)

| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | - x3w3 - sin(x1)w1 - sin(x2)w2 |
| h12 | - x3w3 + sin(x1)w1 + sin(x2)w2 |
| h13 | - x3w3 - sin(x1)w1 - sin(x2)w2 |


| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| - h11w11 - h12w12 - h13w13 |
|h22| + h11w11 - h12w12 - h13w13 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | + h21w21 + h22w22 |

 <img src="/images/21.png" height="300" width="600"> 
 


#### 24

What happens if we decrease the hidden units from the first hidden layer, lets check it out. Intuitively I dont think it will make any difference because the data distribution is too hard to learn. 

- x3 denotes x1x2 and weight is by w3
- w1 denotes weights for sin(x1)
- w2 denotes weights for sin(x2)

| First Hidden Layer | Equation |
| ------------- |:-------------:|
| h11 | + x3w3 - sin(x1)w1 + sin(x2)w2 |
| h12 | - x3w3 + sin(x1)w1 + sin(x2)w2 |



| Second Hidden Layer | Equation |
| ------------- |:-------------:|
|h21| - h11w11 + h12w12 |
|h22| - h11w11 + h12w12 |


| Output Layer | Equation |
| ------------- |:-------------:|
| o1 | + h21w21 - h22w22 |

 <img src="/images/22.png" height="300" width="600"> 

As expected it does not learn as much and the training error is much higher in comparison to experiment 23. 

I have more experiments by using just a single layer neural network which has one hidden layer. All the above experiments were for two hidden layers which I thought would be more interesting to post. 

