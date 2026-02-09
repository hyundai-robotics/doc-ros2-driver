# 10.1 Running with MoveIt2

### Overview

Basic procedures for running HD Hyundai Robotics robots with MoveIt2.

### Pre-launch Preparations

#### Hardware Preparation
- Power on robot controller and set to REMOTE mode
- Ensure emergency stop button is accessible
- Verify network connection (ping 192.168.1.150)
- Confirm workspace is clear of obstacles

#### Software Preparation
- Set up ROS2 environment: `source ~/ros2_ws/install/setup.bash`
- Verify robot model

### Basic Launch Procedures

#### 1. Launch MoveIt2
```bash
# Basic MoveIt2 launch
ros2 launch hdr_moveit_config hdr_moveit.launch.py robot_model:=ha006b

# Launch with specified IP address
ros2 launch hdr_moveit_config hdr_moveit.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

#### 2. Verify Connection Status
```bash
# Check joint states
ros2 topic echo /joint_states --once

# Check MoveIt2 services
ros2 service list | grep move_group
```

### Supported Robot Models

- ha006b
- hdf7_9
- hdf8_8
- hdr10l_19
- hdr20_17
- hdr50_22
- hdr220_26
- hh020
- hdr35_20

### Safety Precautions

#### Emergency Stop
- Always keep hardware emergency stop button accessible

#### Safe Shutdown
1. Stop all motion
2. Move robot to safe position
3. Terminate MoveIt2 nodes
4. Power off robot controller

### Common Troubleshooting

**Connection Issues**
- Verify network connection: `ping 192.168.1.150`
- Confirm robot controller is in REMOTE mode

**When controllers fail to start:**
- Verify robot controller is in REMOTE mode
- Check network connection
- Confirm robot is not in emergency stop state

**When joint states are not published:**
- Check hardware interface connection status
- Verify robot controller status

**Trajectory execution failures:**
- Check joint limits
- Verify target position is valid
- Check controller error messages

#### When the robot does not operate in Motor ON & Start Mode
**Normal Operation**
When both **Motor ON** and **Start Mode** are enabled, the robot operates normally.

**When the robot does not operate**
If Start Mode is not activated while **Motor ON** is enabled, the system generates the error "External Command Operation Disabled (E01554)."
If an infeasible command value is given (e.g., beyond physical limits), an axis overspeed error may occur, causing the robot to stop.
In such cases, the system can be recovered by reactivating **Motor ON + Start Mode**.
