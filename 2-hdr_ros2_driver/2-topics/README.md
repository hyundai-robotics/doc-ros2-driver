# Provided Topics

## Overview

The ROS2 driver publishes real-time robot data through standardized ROS2 topics. These topics provide joint states, robot status information, and diagnostic data for monitoring and control applications.

## Published Topics

### Joint State Information

#### `/joint_states` (sensor_msgs/msg/JointState)
**Description**: Real-time joint position data

**Message Fields**:
```yaml
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
string[] name          # Joint names matching URDF
float64[] position     # Joint positions in radians
float64[] velocity     # NULL (not currently supported)
float64[] effort       # NULL (not currently supported)
```

**Publishing Frequency**: 50 Hz (configurable via `publish_rate` parameter)