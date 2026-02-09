# 2.4 Installation Verification

This guide provides verification procedures to confirm that the HD Hyundai Robotics ROS2 driver is properly installed, configured, and ready to operate.


#### Robot Mode Configuration

The HDR ROS2 driver operates only when the robot is in **REMOTE** mode.

Please set the controller to remote control mode by switching the mode switch on the teach pendant (TP) to the REMOTE position before running the ROS2 driver.

![ip_setup](../../_assets/tp_operate.png)


#### HDR ROS2 Driver Execution Test

```bash
# Run HDR ROS2 driver (ensure robot is in REMOTE mode)
ros2 launch hdr_bringup hdr_control.py \
  robot_model:=hdf7_7      # Enter robot model (default: ha006b)


# Verify controller manager in another terminal
ros2 control list_controllers

# Expected output:
# joint_state_broadcaster[joint_state_broadcaster/JointStateBroadcaster] active
# joint_trajectory_controller[joint_trajectory_controller/JointTrajectoryController] active
```

#### Joint State Publishing Test

```bash
# Verify joint state is being published
ros2 topic list | grep joint_states

# Monitor joint state
ros2 topic echo /joint_states --once

# Check publishing frequency
ros2 topic hz /joint_states
```
