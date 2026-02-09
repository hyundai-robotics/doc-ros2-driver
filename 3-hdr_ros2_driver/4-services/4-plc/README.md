# 3.4.4 PLC Communication Services

### Overview

PLC communication related ROS2 services provided by `hdr_ros2_driver`.

### PLC Communication Services

#### Relay Value Control

```bash
# Get relay value
ros2 service call /hdr_ros2_driver/plc/get/relay_value hdr_msgs/srv/IoplcGet "{name: 'M', st: 100, len: 10}"

# Set relay value
ros2 service call /hdr_ros2_driver/plc/post/relay_value hdr_msgs/srv/IoplcPost "{name: 'fb1.do0', value: 1}"
```
