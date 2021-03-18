# Landmark-Detection-Tracking

## Landmark Detection and Tracking, Robot Moving and Sensing

In this (udacity) project, we are localizing a robot in a 2D grid world. The basis for simultaneous localization and mapping (SLAM) is to gather information from a robot's sensors and motions over time, and then use information about measurements and motion to re-construct a map of the world. List of resources:

Notebook 1 : Robot Moving and Sensing

Notebook 2 : Omega and Xi, Constraints

Notebook 3 : Landmark Detection and Tracking

robot.py


### Uncertainty
Robot motion and sensors have some uncertainty associated with them. For example, imagine a car driving up hill and down hill; the speedometer reading will likely overestimate the speed of the car going up hill and underestimate the speed of the car going down hill because it cannot perfectly account for gravity. Similarly, we cannot perfectly predict the motion of a robot. A robot is likely to slightly overshoot or undershoot a target location.

### Notebook 1
In notebook 1, we look at the robot class. First, we'll create a robot and move it around a 2D grid world. Then I define a sense function for this robot that allows it to sense landmarks in a given world. Understanding of how this robot moves, senses, and how it keeps track of different landmarks that it sees in a 2D grid world is very important.

<img src="https://github.com/Lumia720/Landmark-Detection-Tracking/blob/main/images/robot_location.png" width="450" height = "300">


### robot.py

### Notebook 2
To implement Graph SLAM, a matrix and a vector (omega and xi, respectively) are introduced. The matrix is square and labelled with all the robot poses (xi) and all the landmarks (Li). Every time you make an observation, for example, as you move between two poses by some distance dx and can relate those two positions, you can represent this as a numerical relationship in these matrices.

It's easiest to see how these work in an example. Below you can see a matrix representation of omega and a vector representation of xi.


Next, let's look at a simple example that relates 3 poses to one another.
<img src="https://github.com/Lumia720/Landmark-Detection-Tracking/blob/main/images/omega_xi_constraints.png">




When you start out in the world most of these values are zeros or contain only values from the initial robot position
In this example, you have been given constraints, which relate these poses to one another. Constraints translate into matrix values
