# Jetson-Nano

- Jetson Nano Image
지상 관제 컴퓨터에 ubuntu 22.04 humble - ros2가 설치되어 있다.
ROS2 통신의 편리함을 위해 젯슨나노에 ros2 foxy를 설치하였다.
ros2 foxy는 공식적으로 우분투 20.04에서 구동가능하다.
하지만 젯슨 나노는 공식적으로 우분투 20.04를 지원하지 않기 때문에 개인이 개발한 이미지를 통해서 ros2 foxy가 설치된 우분투 20.04 이미지를 통해 설치한다.

https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image

- ZED SDK
와이파이를 통해 제드 정보를 주고받기 위해 ZED SDK를 설치할 필요가 있다. 이를 위해 JETPACK 버전을 업그래이드 해야한다.

https://docs.nvidia.com/jetson/archives/l4t-archived/l4t-3271/index.html#page/Tegra%20Linux%20Driver%20Package%20Development%20Guide/updating_jetson_and_host.html

dpkg error 가 발생한다면, var/lib/dpkg 에 있는 파일들을 삭제하여 해결할 수 있다.


- ROS2 pkg
터틀봇에 사용되는 기본적인 패키지들을 설치한다.
turtlebot3 ROBOTIS E-MANUAL > 3. Quick STart Guide > 3.2 SBC setup > Foxy


- Run pkg
set appropriate agent name like follower1/2 or somehting in bashrc    
this will be the namespace of the agent   
ex) export AENT_NAME='f1'   

팔로워2의 경우 UWB메시지를 읽고 출판하는 노드가 추가된다.
