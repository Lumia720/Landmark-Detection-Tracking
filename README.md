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

It's easiest to see how these work in a simple example that relates 3 poses to one another.
<img src="https://github.com/Lumia720/Landmark-Detection-Tracking/blob/main/images/omega_xi_constraints.png">


### Notebook 3 : Landmark Detection and Tracking

Here we 
1) create the world.
In a real SLAM problem, we are given a map that contains information about landmark locations, and in excersize example, we make our own data using the "make_data" function, which generates a world grid with landmarks in it and then generates data by placing a robot in that world and moving and sensing over some numer of time steps. The "make_data" function relies on a correct implementation of robot move/sense functions, which, at this point, should be complete and in the robot_class.py file. The data is collected as an instantiated robot moves and senses in a world.

2) initiate constraints for a 2D world (robot poses as Px, Py and landmark positions as Lx, Ly) 

3) implement SLAM inputs. In addition to data (p.1), slam function takes in:

  N - The number of time steps that a robot will be moving and sensing
  num_landmarks - The number of landmarks in the world
  world_size - The size (w/h) of your world
  motion_noise - The noise associated with motion; the update confidence for motion should be 1.0/motion_noise
  measurement_noise - The noise associated with measurement/sensing; the update weight for measurement should be 1.0/measurement_noise
  
  

### What to Expect
The data that is generated is random, but we did specify the number, N, or time steps that the robot was expected to move and the num_landmarks in the world (which an implementation of slam should see and estimate a position for. The robot should also start with an estimated pose in the very center of your square world, whose size is defined by world_size).

With these values in mind, we see a result that displays two lists:

1) Estimated poses, a list of (x, y) pairs that is exactly N in length since this is how many motions your robot has taken. The very first pose should be the center of your world, i.e. [50.000, 50.000] for a world that is 100.0 in square size.

2) Estimated landmarks, a list of landmark positions (x, y) that is exactly num_landmarks in length.


Landmark Locations
If we refer back to the printout of exact landmark locations when this data was created, you should see values that are very similar to those coordinates, but not quite (since slam must account for noise in motion and measurement).

## Conclusion - see Notebook 3 for visualization of constructed world
Due to noise in measurement and motion, the True Landmarks and Robot positions are a bit different from the Estimated Landmarks and Robot position.

If we move more, it is not clear if we get any more accurate measurements, the noise of measurement and movement will still make estimations of positions approximate. I have tried to increase number of steps from 20 to 2000 and calculate MSE, there was no consistent improvement. If we reduce both noise in movement and measurement thus increasing our confidence of each new update, then more steps would produce more accurate estimates.
