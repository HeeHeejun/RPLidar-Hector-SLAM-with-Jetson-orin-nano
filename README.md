# RPLidar-Hector-SLAM-with-Jetson-orin-nano
Hector SLAM without odometry data on a ROS with the RPLidar A1 and Jetson Orin Nano

## Purpose
This guide aims to provide a simple setup for testing Hector SLAM on a Jetson Orin Nano with RPLidar A1 in a JetPack 5.1.3 environment using ROS Noetic.

## Environment
- **Device**: Jetson Orin Nano  
- **Sensor**: RPLidar A1  
- **OS**: Ubuntu 20.04 (via JetPack 5.1.3)  
- **ROS Version**: ROS Noetic  

## Hector SLAM Setup

### Step 1: Prerequisites

#### 1.1 Configure System to Accept Software from packages.ros.org
```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

#### 1.2 Set Up Keys
```bash
sudo apt install curl  # Install curl if not already available
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```

#### 1.3 Update the Package Index
```bash
sudo apt update
```

#### 1.4 Install ROS Noetic (Full Desktop Version)
```bash
sudo apt install ros-noetic-desktop-full
```

#### 1.5 Add ROS Environment Variables to Shell Configuration
```bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### Step 2: Build the Catkin Workspace

#### 2.1 Create a Catkin Workspace
```bash
mkdir ~/catkin_ws && mkdir ~/catkin_ws/src
```

#### 2.2 Clone the Hector SLAM Repository
```bash
git clone https://github.com/HeeHeejun/RPLidar-Hector-SLAM-with-Jetson-orin-nano.git
```

#### 2.3 Build the Workspace Using catkin_make
```bash
cd ~/catkin_ws
catkin_make
```

#### 2.4 Source the Setup Script
```bash
source ./devel/setup.bash
```

#### 2.5 Set Permissions for the USB Port
```bash
sudo chmod 666 /dev/ttyUSB0
```

#### 2.5 Set Permissions for the USB Port
```bash
sudo chmod 666 /dev/ttyUSB0
```

### Step 3: Launch Hector SLAM

#### 3.1 Launch the RPLidar Node
```bash
roslaunch rplidar_ros rplidar.launch
```

#### 3.2 Launch the Hector SLAM Node in a New Terminal
```bash
roslaunch hector_slam_launch tutorial.launch
```

### References
- [ROS Noetic Documentation](https://wiki.ros.org/noetic)
- [ROS Tutorials](https://wiki.ros.org/ROS/Tutorials)
