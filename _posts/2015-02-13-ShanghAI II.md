---
layout: post
title: "ShanghAI II"
description: ""
category: technical
tags: [robotics, ai, shanghai]
---
{% include JB/setup %}

<p align="justify" >
The initial ideas that we started out with were worked upon, implemented on WebBots and along the way got modified slightly. The end result, I believe is full of better ideas and implementations. Robotics derives a lot of inspiration from animal behaviour and this iteration of ShanghAI is all about how robotics is coupled with animal behaviour. The act of evolution has perfected almost every task and we just need to learn from it[1].
</p>

## Initial Ideas
<p align="justify" >
<ul>
<li>
Machine learning to calculate the optimum numerical values of all parameters viz. pitch, yaw.
</li>
<ul>
<li>
Adaptive boosting for finding the best values of the parameters and their appropriate weightage.
</li>
<li>
Grid Search CV for hyper parameter optimization.
</li>
</ul>
<li>
Neural networks
</li>
<ul>
<li>
Find and mark cubes and use neural networks to inform other robots to collect cubes.
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
Supervisor controller obtains information about robots' and cubes' absolute position from the controller program and transmits this information to the robot. Hence, it keeps track of several robots simultaneously.
</li>
<li>
This communication enables the robots to understand how they should manoeuvre their movement to get to the appropriate cube at the right location.
</li>
</ul>
</ul>
</p>

## Morphology

### Swiss Robots

<p align="justify" >
Each robot has its own coordinate system where the origin is the position of the first cube found. The current position is relative to the cluster point and is calculated using a method called path integration. Swiss robots are extremely simple robots and no not rely heavily on communication. The robots develop themselves to understand how to move and in which direction to move. They need to distinguish between other robots, walls and cubes. The wall is distinguished from cubes and robots by its width. The walls have a greater width. Now, to differentiate between cubes and robots the ability of communication comes into place. Only the robots can communicate, so, if communication is carried out successfully then it is a robot, else a cube.
</p>

### Distance Sensors

<p align="justify" >
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
These are based on binary threshold, so transmit only when the total signal is above some threshold limit. These transmit the signal when a collision takes place.
</li>
</ul>
<li>
Light Sensors
</li>
<ul>
<li>
These direct the bot to move in the direction in which light falls.
</li>
</ul>
<li>
Infrared Sensors
<br/>
<br/>
<img src ="/images/Infrared-sensors.jpg" style="width:300px;height=200px">
<br/>
</li>
<br/>
<li>
Touch Sensors
<p>
<br/>
<img src ="/images/Touch-sensors.jpg" style="width:300px;height=200px" >
</p>
</li>
</ul>
</p>

### Locomotion

+ Using Wheels
	- Wheels are driven by electrical motors.
	- If both wheels turn at equal speed, the robot moves straight.
	- If the right wheel is stopped and only the left wheel moves, the robot will turn to the right side.
	- If both wheels move in opposite direction with equal speed, hence the left wheel moves forward and right moves backward or vice versa, the robot turns on spot.
 
+ Using Infrared Sensors
	- The age of the cluster point is exchanged while communicating. After evaluation of this cluster point the robot with the older cluster point sends its current coordinates to the other bots which adopt the older ones coordinates. Finally, this procedure leads to one oldest and global cluster point.
 

## Experiment

<p align="justify" >
All the experiments were done with my team mate Elena Okhapkina and primary teaching assistant Martin F. Stoelen along with secondary TA Yijiang Ren. 
</p>

### Robots and animal behaviour[1]

+ Evolution has perfected the task and we just need to learn from it
+ Cognition and behavior are a function of the environment, the body, and the brain.
+ We need to find how the swiss robots resemble an animal in some specific environment
	- Swiss robots may be treated as ants and the cubes as the ants food.

### References 
[1] [Send in the Bots](http://www.the-scientist.com/?articles.view/articleNo/37635/title/Send-in-the-Bots/ ) by Jef Akst, The Scientist Magazine, October 1, 2013. 
