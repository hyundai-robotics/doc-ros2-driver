# Running with MoveIt2

## Overview

Basic procedures for running HD Hyundai Robotics robots with MoveIt2.

## Pre-launch Preparations

### Hardware Preparation
- Power on robot controller and set to REMOTE mode
- Ensure emergency stop button is accessible
- Verify network connection (ping 192.168.1.150)
- Confirm workspace is clear of obstacles

### Software Preparation
- Set up ROS2 environment: `source ~/ros2_ws/install/setup.bash`
- Verify robot model

## Basic Launch Procedures

### 1. Launch MoveIt2
```bash
# Basic MoveIt2 launch
ros2 launch hdr_moveit_config hdr_moveit.launch.py robot_model:=ha006b

# Launch with specified IP address
ros2 launch hdr_moveit_config hdr_moveit.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

### 2. Verify Connection Status
```bash
# Check joint states
ros2 topic echo /joint_states --once

# Check MoveIt2 services
ros2 service list | grep move_group
```

## Supported Robot Models

- ha006b
- hdf7_9
- hdf8_8
- hdr10l_19
- hdr20_17
- hdr50_22
- hdr220_26
- hh020

## Safety Precautions

### Emergency Stop
- Always keep hardware emergency stop button accessible

### Safe Shutdown
1. Stop all motion
2. Move robot to safe position
3. Terminate MoveIt2 nodes
4. Power off robot controller

## Common Troubleshooting

### Connection Issues
- Verify network connection: `ping 192.168.1.150`
- Confirm robot controller is in REMOTE mode

### Planning Failures
- Verify target position is within workspace
- Check collision detection settings
- Verify joint limits

### Execution Issues
- Confirm robot is not in emergency stop state
- Check controller error status
- Verify ROS2 topic connection status