# Landmark-Detection-Tracking

## Landmark Detection and Tracking, Robot Moving and Sensing

In this (udacity) project, we are localizing a robot in a 2D grid world. The basis for simultaneous localization and mapping (SLAM) is to gather information from a robot's sensors and motions over time, and then use information about measurements and motion to re-construct a map of the world. List of resources:

Notebook 1 : Robot Moving and Sensing

Notebook 2 : Omega and Xi, Constraints

Notebook 3 : Landmark Detection and Tracking

robot.py


### Uncertainty
Robot motion and sensors have some uncertainty associated with them. For example, imagine a car driving up hill and down hill; the speedometer reading will likely overestimate the speed of the car going up hill and underestimate the speed of the car going down hill because it cannot perfectly account for gravity. Similarly, we cannot perfectly predict the motion of a robot. A robot is likely to slightly overshoot or undershoot a target location.

In notebook 1, we look at the robot class. First, we'll create a robot and move it around a 2D grid world. Then I define a sense function for this robot that allows it to sense landmarks in a given world. Understanding of how this robot moves, senses, and how it keeps track of different landmarks that it sees in a 2D grid world is very important.

![alt text](https://github.com/Lumia720/Landmark-Detection-Tracking/blob/main/images/robot_world.png)


