# tello-drone-obstacle-course
Group 06 - TIERS lab , University of Turku



> Go to https://github.com/TIERS/drone_racing_ros2 and follow the instructions. 

> After completing that, add the folder of "drone_racer" at ...\drone_racing_ros2_ws\src\

> Open a three new terminals at drone_racing_ros2_ws

>  Terminal No. 01:

source /opt/ros/galactic/setup.bash

colcon build

source install/setup.bash

ros2 launch tello_driver teleop_launch.py



>  Terminal No. 02 

source /opt/ros/galactic/setup.bash

colcon build

source install/setup.bash

ros2 run drone_racer perception_node



>  Terminal No. 03

source /opt/ros/galactic/setup.bash

colcon build

source install/setup.bash

ros2 run drone_racer controller_sm




> In case of any obnormality, please land the drone safely by using the following commands in a new terminal at drone_racing_ros2_ws


source /opt/ros/galactic/setup.bash

colcon build

source install/setup.bash

ros2 service call /drone1/tello_action tello_msgs/TelloAction '{cmd: 'land'}'

## Team and credits

Common project (drone racing) for the course Aerial Robotics and Multi Robot Systems (DTEK2084) at the University of Turku, spring 2025, by Group 06 in the TIERS lab. It builds on the TIERS drone_racing_ros2 workspace (https://github.com/TIERS/drone_racing_ros2) and runs on ROS 2 Galactic with a DJI Tello.

* `perception_node`: finds green gates in the camera image (HSV colour mask, contour area and polygon checks) and an ArUco stop marker, then publishes the gate target to the controller.
* `controller_sm`: a state machine that takes off, climbs, searches for a gate, aligns horizontally and then vertically, flies through the gate, recovers to search for the next one, and lands at the stop marker.
* Result: the drone finished the course in simulation and completed the gate course within the time limit in the live demo.

Team (equal contributions): Ameer Moavia, Ayana Guruge and Syed Mehdi.

* Ameer Moavia: environment setup, perception and navigation nodes for the simulation.
* Ayana Guruge: perception and navigation nodes for the simulation, and adapting them to real world flights.
* Syed Mehdi: adapting the code to real world flights and finalising the drone functions.

This repository is a copy of the team repository on Ameer Moavia's GitHub account, with the original commit history, dates and authors kept.
