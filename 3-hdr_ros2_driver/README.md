# 3. ROS2 Driver (`hdr_ros2_driver`)

The `hdr_ros2_driver` package provides a core ROS2 driver for interfacing with HD Hyundai Robotics' Open API. This driver enables comprehensive communication with robot controllers through REST API, supporting services for robot control, monitoring, file operations, and system management.

### Key Features

- **Robot State Publishing**: Real-time joint state information via `/joint_states` topic
- **Motion Control**: Joint trajectory control through ROS2 actions
- **Comprehensive Services**: Over 30 service endpoints organized by functionality


### Detailed Documentation

- [Launch Instructions](1-launch/README.md) - Launch files for driver execution
- [Configuration Parameters](2-parameters/README.md) - Available parameters within launch
- [Provided Topics](3-topics/README.md) - Published robot state information
- [Available Actions](4-actions/README.md) - Joint trajectory execution and motion control
- [Supported ROS2 Services](5-services/README.md) - API service reference
