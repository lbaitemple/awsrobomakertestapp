# awsrobomakertestapp
This app creates a differential drive robot and simulate the robot to create a map in a corridor world. The differntial drive robot code was mostly from https://github.com/NRottmann/ROS_Gazebo_Tutorial

Make sure you change  s3 bucket and IAM role in simualtion job configuration



#  Download Source
```
git clone https://github.com/lbaitemple/awsrobomakertestapp
```

### Robot
```
cd ~/environment/awsrobotmakertestapp/robot_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build
colcon bundle
```

### Simulation
```
cd ~/environment/awsrobotmakertestapp/simulation_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build
```

### Running Simulation Application 

#### if you are running gazebo in virtual machine, you will need to include the following line in .bashrc

```
echo 'export export SVGA_VGPU10=0' >> ~/.bashrc 
```

```
cd ~/environment/awsrobotmakertestapp/simulation_ws
source ./install/local_setup.sh
roslaunch simulation_gazebo view_combine.launch
```

### Running Robot Application 

```
cd ~/environment/awsrobotmakertestapp/robot_ws
source ./install/local_setup.sh
roslaunch robot_mapping map.launch
```

### Terminal teleop control
```
 rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```



