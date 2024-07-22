# Launch-TurtleBot3-navigation

- NOTE: I am using Ubuntu 20.04 and ROS1 Noetic Ninjemys.

## Download and Install Ubuntu on PC

1-Download the proper Ubuntu 20.04 LTS Desktop image for your PC from the links : https://releases.ubuntu.com/20.04/

2-Follow the instruction below to install Ubuntu on PC

https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview

## Install ROS on Remote PC
````
$ sudo apt update
$ sudo apt upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh
$ chmod 755 ./install_ros_noetic.sh 
$ bash ./install_ros_noetic.sh
````

## Install Dependent ROS Packages
````
$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
````


## Install TurtleBot3 Packages
````
$ sudo apt install ros-noetic-dynamixel-sdk
$ sudo apt install ros-noetic-turtlebot3-msgs
$ sudo apt install ros-noetic-turtlebot3
````
## Catkin workspace
````
$ cd ~/catkin_ws/src/
$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
````
## Launch Simulation World

- Empty World
- TurtleBot3 World
- TurtleBot3 House

for me, i have choose the second one so i will run this command
````
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
````
<img width="931" alt="Screen Shot 2024-07-22 at 6 25 31 AM" src="https://github.com/user-attachments/assets/36b19017-5ee4-44d5-87da-57e238561459">

## Opening SLAM
````
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
````
<img width="836" alt="Screen Shot 2024-07-22 at 6 30 49 AM" src="https://github.com/user-attachments/assets/a8de6876-7635-4a20-a3b9-236c00ca06b7">

create a map and save it
````
rosrun map_server map_saver -f ~/map
````
then run this command:
````
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
````

<img width="823" alt="Screen Shot 2024-07-22 at 6 31 48 AM" src="https://github.com/user-attachments/assets/a52d495c-06e0-4009-819c-57c2e5acaf6c">

## navigation

start the navigation and load the saved map, using this command:
````
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:='/home/muh/map.yaml'
````

<img width="585" alt="90" src="https://github.com/user-attachments/assets/308a42e4-aaf7-45d9-be9f-dfd693290f67">

now You can then move the robot !

<img width="440" alt="image" src="https://github.com/user-attachments/assets/ea6b0965-98b3-4cbf-a873-f97680e73edc">



