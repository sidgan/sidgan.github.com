---
layout: post
title: "ShanghAI II"
description: ""
category: technical
tags: [robotics, ai]
---
{% include JB/setup %}


We worked on our initial solutions and finally came to the end result. 

## Ideas
<ul>
<li>
Machine learning to calculate the optimum numerical values of all parameters viz. pitch, yaw. 
</li>
<ul>
<li>
Adaptive boosting for finding the best values of the parameters and their appropriate weightage.
</li>
<li>
Grid Search CV for hyper parameter optimization
</li>
</ul>
<li>
Neural networks
</li>
<ul>
<li>
Find and mark cubes and use neural network to inform other robots to collect cubes.
</li>
<li>
Robots tell other robots if cubes have been collected or have already been marked by communication. 
</li>
</ul>
<li>
Global Position System node to model a Global Positioning Sensor (GPS) 
</li>
<ul>
<li>
Supervisor controller obtains information about robots and cubes absolute position from the controller program and transmits this information to the robot. Hence, keeps track of several robots simultaneously. 
</li>
<li>
This communication enables the robots to understand how they should manuoevre their movement to get to the appopriate cube at the right location. 
</li>
</ul>
</ul>


## Morphology

### Swiss Robots 

### Distance Sensors
These sensors are used for communication and help in determining the distance. 

<ul>
<li>
Proximity Sensors
</li>
<ul>
<li>
These are distributed over the front half of the bot and each one is connected to a node in the neural network. 
</li>
</ul>
<li>
Collision Sensors
</li>
<ul>
<li>
These are based on binay threshold, so transmit only when the total signal is above some thrhhold limit. These transmit the signal when a collision takes place.
</li>
</ul>
<li>
Light Sensors
</li>
<ul>
<li>
These direct the bot to moves in the direction in which light falls. 
</li>
</ul>
<li>
Infrared Sensors
<p>
<img src ="/images/Infrared-sensors.jpg">
</p>
</li>
<li>
Touch Sensors
<p>
<img src ="/images/Touch-sensors.jpg">
</p>
</li>
</ul>

### Locomotion 
<ul>
<li>
Using Wheels
</li>
<ul>
<li>
Wheels are driven by electrical motors.
</li>
<ul>
<li>
If both wheels turn at equal speed, the robot moves straight
</li>
<li>
If the right wheel is stopped and only the left wheel moves, the robot will turn to the right side
</li>
<li>
If both wheels move in opposite direction with equal speed, hence the left wheel moves forward and right moves backward or vice versa, the robot turns on spot. 
</li>
</ul>
</ul>
<li>
Using Infrared Sensors
</li>
<ul>
<li>
The age of the cluster point is exchanged while communicating. After evaluvation of this cluster point the robot with the older cluster point sends its current coordinates to the other bots which adopt the older ones coordinates. Finally, this procedure leads to one oldest and global cluster point. 
</li>
</ul>
</ul>

## Experiment 

### Robots and animal behaviour

<ul>
<li>
Evolution has perfected the task and we just need to learn from it.
</li>
<li>
Cognition and behavior are a function of the environment, the body, and the brain.
</li>
<li>
We need to find how the swiss robots resemble an animal in some specific 
<ul>
<li>
Swiss Robots may be treated as ants and the cubes as the ants food. 
</li>
</ul>
</li>
</ul>
