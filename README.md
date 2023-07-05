# Jetson-Nano

- Jetson Nano Image   
In order to install ros2 foxy, Ubuntu 20.04 is required.   
Since Jetson Nano does not support Ubuntu 20.04 officially, following link kindof workaround is used.   

https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image

In order to setup ZED SDK for streaming video via wifi, jetpack version might need to be upgraded.

follow this link, and other dpkg error could be arised. It can be handled by deleting the list of the file in var/lib/dpkg   

https://docs.nvidia.com/jetson/archives/l4t-archived/l4t-3271/index.html#page/Tegra%20Linux%20Driver%20Package%20Development%20Guide/updating_jetson_and_host.html

- ZED SDK


- ROS2 pkg

- Installation 
turtlebot3 ROBOTIS E-MANUAL > 3. Quick STart Guide > 3.2 SBC setup > Foxy




- Run pkg
set appropriate agent name like follower1/2 or somehting in bashrc    
this will be the namespace of the agent   
ex) export AENT_NAME='f1'   
