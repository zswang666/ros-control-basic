# ros-control-basic

### Description:

This is a simple implementation of building a robot model ([robotiq-c2 gripper](https://robotiq.com/products/2-finger-adaptive-robot-gripper)) in rviz and Gazebo with control interface given only robot description files (.urdf) and their meshes. There will be a tutorial coming out that teaches you how to do that from the beginning.

### Prerequisite:
- [ros kinectic](http://wiki.ros.org/kinetic/Installation)

### How To Run:
- build the workspace
```
# open up a new terminal
$ cd $ROS_CONTROL_BASIC_HOME
$ mv src/robotiq_c2_gazebo . # since robotiq_c2_gazebo package has dependencies on other packages, we build others first
$ catkin_make
$ source devel/setup.bash
$ mv robotiq_c2_gazebo src
$ catkin_make
```
- robot in rviz
```
# open up a new terminal
$ cd $ROS_CONTROL_BASIC_HOME
$ source devel/setup.bash
$ roslaunch robotiq_c2_description robotiq_c2_rviz.launch # there will be a pop-up GUI to control the gripper
```
- robot in gazebo
```
# open up a new terminal
$ cd $ROS_CONTROL_BASIC_HOME
$ source devel/setup.bash
$ roslaunch robotiq_c2_gazebo robotiq_c2_world.launch
$ rostopic pub -1 /robotiq_c2/robotiq_85_left_knuckle_joint_position_controller/command std_msgs/Float64 "data: 0.2" # you can change the number 0.2 to other numbers that ranges from 0. to about 0.7
```

### Resources:
- gripper's urdf and meshes are from [ros-industrial/robotiq](https://github.com/ros-industrial/robotiq/tree/jade-devel/robotiq_c2_model_visualization)
- gazebo mimicjoint plugin is from [roboticsgroup/roboticsgroup_gazebo_plugins](https://github.com/roboticsgroup/roboticsgroup_gazebo_plugins)

### To Be Done:
- a tutorial
- an easier-to-use interface to control robot in gazebo with ros
