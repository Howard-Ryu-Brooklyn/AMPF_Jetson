# AMPF — Onboard (Jetson Nano)

[AMPF_MATLAB](https://github.com/Howard-Ryu-Brooklyn/AMPF_MATLAB)의 편대 제어 알고리즘을 실제
Turtlebot3에 태우기 위한 온보드 배포 코드입니다. Jetson Nano가 공식 지원하지 않는 Ubuntu
20.04·ROS2 Foxy 환경을 직접 구성해 로봇 구동, LiDAR, UWB 센서를 통합했습니다.

## 구성

- **`turtlebot3`, `turtlebot3_msgs`** — Turtlebot3 구동 스택 (burger 모델)
- **`ld08_driver`** — LiDAR(LD08) 드라이버
- **`uwb`** — UWB 기반 거리 측정 노드. follower2에는 이 UWB 메시지를 읽는 노드가 추가로 붙어,
  측정치 결손 시나리오([AMPF_MATLAB](https://github.com/Howard-Ryu-Brooklyn/AMPF_MATLAB) 4장)를
  실기에서 재현합니다.
- **`my_interfaces`** — 편대 제어에 필요한 커스텀 메시지 정의 (편대 목표, 상대 위치, UWB 등)

## 관련 저장소

| 저장소 | 역할 |
|---|---|
| [AMPF_MATLAB](https://github.com/Howard-Ryu-Brooklyn/AMPF_MATLAB) | 알고리즘 이론·시뮬레이션·학위논문 |
| [AMPF_GC](https://github.com/Howard-Ryu-Brooklyn/AMPF_GC) | 지상 관제 PC — ROS2 편대 제어기, 비전 센싱 |
| AMPF_Jetson (이 저장소) | 로봇 온보드 — 구동, LiDAR/UWB |

## 환경

Jetson Nano, Ubuntu 20.04, ROS2 Foxy. 공식 미지원 조합이라 커스텀 이미지가 필요합니다
([Qengineering/Jetson-Nano-Ubuntu-20-image](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image)).

------------------

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
