# awsrobomakertestapp
This app creates a differential drive robot and simulate the robot to create a map in a corridor world. The differntial drive robot code was mostly from https://github.com/NRottmann/ROS_Gazebo_Tutorial

Make sure you change  s3 bucket and IAM role in simualtion job configuration



#  Download Source
```
sudo apt install python3-vcstools
git clone -b navigation  https://github.com/lbaitemple/awsrobomakertestapp
```



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

### Terminal teleop control
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

## Navigation
```
sudo apt-get install ros-melodic-amcl ros-melodic-move-base ros-melodic-global-planner ros-melodic-teb-local-planner -y
```
