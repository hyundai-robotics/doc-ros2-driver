# ROS2 Driver Services

## Overview

The `hdr_ros2_driver` provides various ROS2 services for communicating with HD Hyundai Robotics Hi6 controllers.

## Service Categories

| Category | Description |
|----------|-------------|
| **[Control Services](1-control/README.md)** | Robot control, motor power, emergency stop, coordinate systems, I/O management |
| **[Task Management](2-task/README.md)** | Variable assignment, motion execution, program control |
| **[File Management](3-file/README.md)** | File upload/download, directory manipulation |
| **[PLC Communication](4-plc/README.md)** | PLC relay value control |
| **[Console Commands](5-console/README.md)** | Console command execution, system time, log management |
| **[Project Management](6-project/README.md)** | Job information, job deletion/reload |
| **[Version Information](7-version/README.md)** | API version, system version queries |

## Basic Usage

### Check Service List
```bash
# List all HDR driver services
ros2 service list | grep hdr_ros2_driver
```

### Common Service Calls
```bash
# Check API version
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger

# Check motor status
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# Turn on motor power
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger
```