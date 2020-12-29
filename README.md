# awsrobomakertestapp
This app creates a differential drive robot and simulate the robot to create a map in a corridor world. The differntial drive robot code was mostly from https://github.com/NRottmann/ROS_Gazebo_Tutorial

Make sure you change  s3 bucket and IAM role in simualtion job configuration



#  Download Source
```
sudo apt install python3-vcstools
git clone -b navigation  https://github.com/lbaitemple/awsrobomakertestapp
```

## terminal commands

### Simulation
```
cd ~/environment/awsrobomakertestapp/simulation_ws
rosws update
rosdep install --from-paths src --ignore-src -r -y
colcon build
colcon bundle
```

### Running Simulation Application 

```
cd ~/environment/awsrobotmakertestapp/simulation_ws
source ./install/local_setup.sh
roslaunch simulation_gazebo combine.launch
```

## Run configuration
1. try to switch roboconfig in run configuration
1. in simulation configuration, modify s3 buket, role ARN, and VPC subnets (use available zones a,b,c) & security group id
1. after colcon build, colcon bundle, you can lauch simulation in run configuration

### Terminal teleop control
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```


### Robot
```
cd ~/environment/awsrobomakertestapp/robot_ws
rosws udpate
rosdep install --from-paths src --ignore-src -r -y
colcon build
colcon bundle
```

### Running Robot Application 

```
cd ~/environment/awsrobotmakertestapp/robot_ws
source ./install/local_setup.sh
roslaunch robot_mapping navigation.launch
```



## Navigation
```
sudo apt-get install ros-melodic-amcl ros-melodic-move-base ros-melodic-global-planner ros-melodic-teb-local-planner -y
```
