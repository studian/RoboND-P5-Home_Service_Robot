
# RoboND-P5-Home_Service_Robot

The goal of this project is to program a robot than can autonomously map an environment and navigate to pick up and drop off virtual objects. List of the steps in this project :

* Design a simple environment with the Building Editor in Gazebo.
* Teleoperate your robot and manually test SLAM.
* Use the ROS navigation stack and manually commands your robot using the 2D Nav Goal arrow in rviz to move to 2 different desired positions and orientations.
* Write a pick_objects node that commands your robot to move to the desired pickup and drop off zones.
* Write an add_markers node that subscribes to your robot odometry, keeps track of your robot pose, and publishes markers to rviz.

![alt text](results/results1.PNG)
![alt text](results/results2.PNG)

-   Result Link: https://youtu.be/GOLqsiI4hB8

## Prerequisites

### Install xterm, Python with pip, dependencies
```
$ sudo apt-get install xter
$ sudo apt-get install python-pip
$ sudo apt-get update && sudo apt-get upgrade -y
$ sudo apt-get install ros-${ROS_DISTRO}-map-server
$ sudo apt-get install ros-${ROS_DISTRO}-amcl
$ sudo apt-get install ros-${ROS_DISTRO}-move-base
$ sudo apt-get install ros-${ROS_DISTRO}-slam-gmapping
```

### Basic Setting
```
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
$ catkin_init_workspace
$ cd ..
$ catkin_make
$ sudo apt-get update
$ cd ~/catkin_ws/src
$ git clone https://github.com/ros-perception/slam_gmapping
$ git clone https://github.com/turtlebot/turtlebot
$ git clone https://github.com/turtlebot/turtlebot_interactions
$ git clone https://github.com/turtlebot/turtlebot_simulator
$ cd ~/catkin_ws/
$ source devel/setup.bash
$ rosdep -i install gmapping
$ rosdep -i install turtlebot_teleop
$ rosdep -i install turtlebot_rviz_launchers
$ rosdep -i install turtlebot_gazebo
$ catkin_make
$ source devel/setup.bash
```

## Clone and Initialize

```
$ mkdir catkin_ws && cd catkin_ws
$ git clone https://github.com/studian/RoboND-P5-Home_Service_Robot.git src
$ cd src && catkin_init_workspace
```

## Build the Project (from catkin_ws folder)
```
$ cd ..
$ catkin_make
```

## Run the home_service script
Step 1 is sourcing, 2 is creating permissions and 3 is running the script.
```
1 $ source devel/setup.bash
2 $ chmod 777 ./src/scripts/*.sh
3 $ ./src/scripts/home_service.sh
```

## Running the other scripts

For mapping use:
```
$ cd catkin_ws
$ source devel/setup.bash
$ ./src/scripts/test_slam.sh
```

For navigation testing
```
$ cd catkin_ws
$ source devel/setup.bash
$ ./src/scripts/test_navigation.sh
```

For add_markers testing
```
$ cd catkin_ws
$ source devel/setup.bash
$ ./src/scripts/add_markers.sh
```

For pick_objects testing
```
$ cd catkin_ws
$ source devel/setup.bash
$ ./src/scripts/pick_objects
```

## Catkin workspace should look something like this:
```
catkin_ws/src
    ├── slam_gmapping                  # gmapping_demo.launch file                   
    │   ├── gmapping
    │   ├── ...
    ├── turtlebot                      # keyboard_teleop.launch file
    │   ├── turtlebot_teleop
    │   ├── ...
    ├── turtlebot_interactions         # view_navigation.launch file      
    │   ├── turtlebot_rviz_launchers
    │   ├── ...
    ├── turtlebot_simulator            # turtlebot_world.launch file 
    │   ├── turtlebot_gazebo
    │   ├── ...
    ├── world                          # world files
    │   ├── ...
    ├── scripts                        # shell scripts files
    │   ├── ...
    ├──RvizConfig                      # rviz configuration files
    │   ├── ...
    ├──pick_objects                    # pick_objects C++ node
    │   ├── src/pick_objects.cpp
    │   ├── ...
    ├──add_markers                     # add_marker C++ node
    │   ├── src/add_markers.cpp
    │   ├── ...
    ├──add_markers_test                # add_markers_test C++ node
    │   ├── src/add_markers_test.cpp
    │   ├── ...
    └──
```

## Official ROS Packages
* gmapping: With the gmapping_demo.launch file, you can easily perform SLAM and build a map of the environment with a robot equipped with laser range finder sensors or RGB-D cameras.  

* turtlebot_teleop: With the keyboard_teleop.launch file, you can manually control a robot using keyboard commands.   

* turtlebot_rviz_launchers: With the view_navigation.launch file, you can load a preconfigured rviz workspace. You’ll save a lot of time by launching this file, because it will automatically load the robot model, trajectories, and map for you.   

* turtlebot_gazebo: With the turtlebot_world.launch you can deploy a turtlebot in a gazebo environment by linking the world file to it.   

## Simple Pacakges Explaination
* turtlebot : provides underlying drivers and specifications for the Turtlebot 2 in ROS Kinetic, and also keyboard control functionality for this project.   

* simulator : connects the Turtlebot packages with the Gazebo environment.   

* interactions : supporting user side interactions with the turtlebot.   

* slam_gmapping : provides SLAM capability in conjunction with the gmapping package.   


