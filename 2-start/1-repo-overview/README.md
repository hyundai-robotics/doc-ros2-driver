# 2.1 Repository Overview

The HD Hyundai Robotics ROS2 driver consists of multiple interconnected packages that work together to provide robot control, simulation, and motion planning capabilities.

### Repository Architecture

```
HD Hyundai Robotics ROS2 Driver

hdr_ros2_driver            # Main repository
   hdr_bringup             # Robot integration and control launch files
   hdr_ros2_driver         # Core communication driver
   hdr_hardware_interface  # ros2_control integration
   hdr_moveit_config       # MoveIt configuration
   hdr_msgs                # HD Robotics custom message definitions

hdr_client_driver          # C++ client library

hdr_description            # Robot URDF models and mesh

hdr_simulation_gz          # Gazebo simulation integration
```

### Package Details within Repository

- **[ROS2 Driver (`hdr_ros2_driver`)](../../2-hdr_ros2_driver/README.md)** </br>
Primary ROS2 node providing services for robot control, file management, I/O operations, and system monitoring

- **[HDR Client Driver (`hdr_client_driver`)](../../6-hdr_client_driver/README.md)** </br>
C++ library implementing TCP/UDP communication protocols with HD Hyundai Robotics controllers

- **[ROS2 Control Integration (`hdr_hardware_interface`)](../../3-hdr_hardware_interface/README.md)** </br>
ros2_control SystemInterface for integration with standard ROS2 control framework

- **[Robot Description (`hdr_description`)](../../4-hdr_description/README.md)** </br>
URDF/XACRO, collision/visual mesh, and RViz configuration for supported robot models

- **[MoveIt2 Configuration (`hdr_moveit_config`)](../../5-hdr_moveit_config/README.md)** </br>
Robot model-specific MoveIt2 configuration including SRDF, soft limits, kinematics, and motion planning settings

- **[Gazebo Simulation (`hdr_simulation_gz`)](../../6-hdr_simulation_gz/README.md)** </br>
Gazebo Ignition simulation integration

- **[Custom Messages (`hdr_msgs`)](../../7-hdr_msgs/README.md)** </br>
Custom ROS2 service and message definitions for communication with HD Hyundai Robotics controllers


### Next Steps

1. Review the individual package documentation linked above.
2. Proceed to [Installation](../2-installation/README.md) to build the packages.
3. Configure robot connection in [Initial Setup](../3-initial-setup/README.md).
