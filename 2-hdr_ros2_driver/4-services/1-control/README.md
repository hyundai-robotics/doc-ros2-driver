# Robot Control Services

## Overview

Robot control related ROS2 services provided by `hdr_ros2_driver`.

## Robot Control Services

### Motor Status and Control

```bash
# Get motor status
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# Turn on motor power
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger

# Emergency stop
ros2 service call /hdr_ros2_driver/robot/post/emergency_stop std_srvs/srv/Trigger
```

### Position and Tool Management

```bash
# Get current robot position
ros2 service call /hdr_ros2_driver/robot/get/po_cur hdr_msgs/srv/PoseCur

# Get current tool information
ros2 service call /hdr_ros2_driver/robot/get/cur_tool std_srvs/srv/Trigger

# Get available tool list
ros2 service call /hdr_ros2_driver/robot/get/tools std_srvs/srv/Trigger

# Get specific tool information
ros2 service call /hdr_ros2_driver/robot/get/tools_t hdr_msgs/srv/Number "{data: 0}"

# Set tool number
ros2 service call /hdr_ros2_driver/robot/post/tool_no hdr_msgs/srv/Number "{data: 0}"

# Set coordinate system
ros2 service call /hdr_ros2_driver/robot/post/crd_sys hdr_msgs/srv/Number "{data: 0}"
```

## System Control Services

### Operating Conditions

```bash
# Get operating conditions
ros2 service call /hdr_ros2_driver/control/get/op_cnd std_srvs/srv/Trigger

# Set operating conditions
ros2 service call /hdr_ros2_driver/control/put/op_cnd hdr_msgs/srv/OpCnd "{playback_mode: 1, step_goback_max_spd: 130, ucrd_num: 2}"

# Get user coordinate system numbers
ros2 service call /hdr_ros2_driver/control/get/ucs_nos std_srvs/srv/Trigger
```

### Digital I/O

```bash
# Read digital input
ros2 service call /hdr_ros2_driver/control/get/ios/di hdr_msgs/srv/IoRequest "{type: 'di', blk_no: 1, sig_no: 1}"

# Read digital output
ros2 service call /hdr_ros2_driver/control/get/ios/do hdr_msgs/srv/IoRequest "{type: 'do', blk_no: 1, sig_no: 1}"

# Read serial I/O
ros2 service call /hdr_ros2_driver/control/get/ios/sio hdr_msgs/srv/IoRequest "{type: 'sio', blk_no: 1, sig_no: 1}"

# Set digital I/O
ros2 service call /hdr_ros2_driver/control/post/ios/dio hdr_msgs/srv/IoRequest "{type: 'do', blk_no: 1, sig_no: 1, val: 1}"
```