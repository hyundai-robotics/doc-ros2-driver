# ros2_control System Execution

## Overview

Explains basic execution methods for the ros2_control system for HD Hyundai Robotics robots.

## Basic Execution

### Launch ros2_control
```bash
# Basic launch
ros2 launch hdr_bringup hdr_control.launch.py robot_model:=ha006b

# Specify IP address
ros2 launch hdr_bringup hdr_control.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

## Controllers

### Check Controller Status
```bash
# List controllers
ros2 control list_controllers

# Check hardware interfaces
ros2 control list_hardware_interfaces

# Check joint states
ros2 topic echo /joint_states
```

### Activate/Deactivate Controllers
```bash
# Activate controller
ros2 control switch_controllers --activate joint_trajectory_controller 

# Deactivate controller
ros2 control switch_controllers --deactivate joint_trajectory_controller
```

## Default Controller Configuration

ros2_control provides the following controllers:

- **joint_state_broadcaster**: Publishes joint states
- **joint_trajectory_controller**: Trajectory following control

## Simple Testing

### Joint Trajectory Test
```bash
# Simple joint movement test
ros2 action send_goal /joint_trajectory_controller/follow_joint_trajectory \
    control_msgs/action/FollowJointTrajectory \
    "{
      trajectory: {
        joint_names: ['j1', 'j2', 'j3', 'j4', 'j5', 'j6'],
        points: [
          {
            positions: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
            time_from_start: {sec: 2}
          }
        ]
      }
    }"
```

## Troubleshooting

### Common Issues

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


## Safety Precautions

- Always keep emergency stop button accessible when working with actual robots
- Immediately emergency stop if robot exhibits unexpected behavior
- Test at low speeds when using for the first time