# grasp_ws

This is the top level git repo for our grasping workspace. This is used for working with PR2, Fetch, and Mico.  The basestation workspace is run off the robot, while the robot_ws is run on the robot.  

## basestation workspace
This ros workspace is for running the user interface, object detection, grasp planning, reachability checking, and grasp execution.

### build
```
git clone git@github.com:CURG/grasp_ws.git
cd ~/grasp_ws/basestation_ws/src
catkin_init_ws
wstool update
cd ..
catkin_make
source devel/setup.bash
```

## robot workspace
This ros workspace is for running pc_filter and checkerboard detection.  These are run on the robot so that the full images and pointclouds do not need to be streamed off the robot. 

### build
```
cd ~/grasp_ws/robot_ws/src
catkin_init_ws
wstool update
cd ..
catkin_make
source devel/setup.bash
```
