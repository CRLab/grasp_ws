# grasp_ws

This is the top level git repo for our grasping workspace. This is used for working with PR2, Fetch, and Mico.  The basestation workspace is run off the robot, while the robot_ws is run on the robot.  

## basestation workspace
This ros workspace is for running the user interface, object detection, grasp planning, reachability checking, and grasp execution.

### build
```
git clone git@github.com:CURG/grasp_ws.git  --recursive
cd ~/grasp_ws/basestation_ws/src
source /opt/ros/indigo/setup.bash
catkin_init_workspace
cd ..
catkin_make
source devel/setup.bash
```

## robot workspace
This ros workspace is for running pc_filter and checkerboard detection.  These are run on the robot so that the full images and pointclouds do not need to be streamed off the robot. 

### build
```
cd ~/grasp_ws/robot_ws/src
catkin_init_workspace
cd ..
catkin_make
source devel/setup.bash
```
### Up and running

#### On Robot 
```
ssh username@fetch22.local
cd ~/ros/grasp_ws/
source set_fetch_env.sh
cd ~/ros/grasp_ws/robot_ws # since we are on the robot
source devel/setup.bash
roslaunch vision_launch robot.launch # can be run from anywhere
```


#### On Host Machine (aka Basestation)
```
cd ~/ros/grasp_ws/
source set_fetch_env.sh
cd ~/ros/grasp_ws/basestation_ws # since we are on the host machine
source devel/setup.bash
roslaunch system_launch basestation.launch  # can be run from anywhere
```
#### Drop into console (manual execution mode)
```
source set_fetch_env.sh
cd ~/ros/grasp_ws/basestation_ws # since we are on the host machine
source devel/setup.bash
rosrun grasp_execution manual_grasp_execution_node.py 
```

