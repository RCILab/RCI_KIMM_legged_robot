# RCI KIMM Wheel Legged Robot
This repository contains the URDF model and software for a humanoid robot with wheels on its knees, enabling it to switch between walking and driving modes.

## Overview
This repository contains the software and models for a unique legged robot developed in collaboration with the Korea Institute of Machinery and Materials (KIMM). The robot is a bipedal humanoid with an innovative design: wheels are integrated into its knees, allowing it to seamlessly switch between two modes of locomotion: walking and driving.

https://github.com/user-attachments/assets/bf0ed73e-b05b-43fd-bd33-afee59358275

## Dependencies
- ROS 2 Humble (>= 2022.05)  
- Python 3.10 / C++17  

## Installation
1. **Clone the Repository:** Create a workspace and clone this repository recursively.
```bash
mkdir -p ~/kimm_wheel_legged_robot_ws/src && cd ~/kimm_wheel_legged_robot_ws/src
git clone https://github.com/RCILab/RCI_KIMM_legged_robot.git
```

2. **Build the Workspace:** Install dependencies and build the packages.
```bash
cd ~/kimm_wheel_legged_robot_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

3. **Source the Environment:** Source the workspace's setup file to make the packages available in your environment.
```bash
echo "source ~/kimm_wheel_legged_robot_ws/install/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

## Usage

### 1. Check Robot Model in RViz
To visualize the robot and interact with its joints:
```bash
ros2 launch kimm_wheel_legged_robot_viz joint_state_publisher_gui.launch.py
```

### 2. Run Robot in Gazebo
To spawn the robot in Gazebo and start simulation:
```bash
ros2 launch kimm_wheel_legged_robot_bringup kimm_gazebo.launch.py
```

This will load the robot model into Gazebo and start the bringup process for driving and locomotion testing.  

### 3. Drive the Robot in Gazebo
You can control the robot using the keyboard teleoperation node:
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r cmd_vel:=/diff_drive_base_controller/cmd_vel_unstamped
```

This will allow you to send velocity commands to the robot for driving in Gazebo.  

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact
**Maintainer:** Hyunho Cho (`chohh7391@khu.ac.kr`), Kangmin Lee (`khukmin99@khu.ac.kr`)  
**Lab**: [RCI Lab @ Kyung Hee University](https://rcilab.khu.ac.kr)
