
[__SOURCE](README.md)
# Hi6 & Hi7 Controller Function Manual - ROS2 Driver

Currently, ROS2-compatible controllers are the Hi6 series, supported from controller software version **v70.00-00** or higher. </br>
Version **v70.00-00** is scheduled for official release in 2Q 2026. Please refrain from using the HD Hyundai Robotics ROS2 driver before the official release. </br>
⚠️ **The Hi7 model is scheduled for release, and the specific support timeline has not yet been finalized. We will provide further details via an official announcement as soon as the formal release schedule is established. Please keep this in mind.**

[__SOURCE](0-about-this-manual/precautions.md)
# Precautions

{% include file="en/precautions.md" %}

[__SOURCE](1-intro/README.md)
# 1. Overview

This manual provides a description of the HD Hyundai Robotics (HDR) ROS2 driver.

The HDR ROS2 driver integrates HD Hyundai Robotics industrial robot controllers (Hi6, Hi7 series) with ROS2 systems to support both simulation environments and real robot control functions.

![](../_assets/0_hdr_main.png)


### Prerequisites
Before using the HDR ROS2 driver, please make sure to check the following items:
- [Supported Controllers](1-controller-models/README.md) - Compatible Hi6, Hi7 series controllers
- [Supported Robot Models](2-robot-models/README.md) - Compatible HD Hyundai Robotics robot models
- [System Requirements](3-requirements/README.md) - Hardware and software requirements
- [ROS2 Version](4-ros2-version/README.md) - Supported ROS2 versions
- [Robot Joint and Link Names](5-hdr-robot/README.md) - Robot joint and link naming conventions in ROS2

### Installation and Initial Setup
After verifying all the above items, please proceed with the ROS2 driver installation and initial setup according to the following procedures:
- [Repository Overview](../2-start/1-repo-overview/README.md) - HDR ROS2 driver repository structure and architecture overview
- [Package Installation](../2-start/2-installation/README.md) - HDR ROS2 driver build and installation method
- [Controller and PC Setup](../2-start/3-initial-setup/README.md) - Initial setup method for using HDR ROS2 driver
- [Installation Verification](../2-start/4-verifying/README.md) - Verify that installation and setup are completed correctly

### Quick Start with ROS2 Driver
After completing all the installation and initial setup processes above, you can start the HDR ROS2 driver and begin robot control through the following procedures:

- [Running ROS2 Driver](../10-running/README.md) - ROS2 driver execution and robot control methods

⚠️ **Please make sure to check the prerequisites and complete all installation and initial setup before proceeding.**

⚠️ **Currently, the HD Hyundai Robotics ROS2 driver is supported on controller software version *v70.00-00* or higher. </br> The *v70.00-00* version is scheduled for official release in 2Q 2026, so please refrain from using the ROS2 driver before the official release.** 

[__SOURCE](1-intro/1-controller-models/README.md)
# 1.1 Supported Controller Models
The HD Hyundai Robotics Hi6 controller models that officially support ROS2 functionality are as follows:

- Hi6-N10
- Hi6-N20
- Hi6-N00(HK)
- Hi6-N00-60(HK)
- Hi6-N30(HK)
- Hi6-N80(HK)
- Hi6-T15

**Controller Requirements**:
- SW Version: **70.00-00** or higher (scheduled for release in October)
- Operation Mode: **REMOTE mode**

The Hi7 controller series, including future model lineups and support schedules, will be updated on this list as soon as they are finalized.

> ⚠️ **Note:** The HD Hyundai Robotics ROS2 driver does **not support** the **Hi5** controller series.

### Next Steps

After confirming controller compatibility, check [Supported Robot Models](../2-robot-models/README.md) to verify that your robot is supported.

[__SOURCE](1-intro/2-robot-models/README.md)
# 1.2 Supported Robot Models

The robot models currently officially supported by the HD Hyundai Robotics driver are as follows:

- ha006b
- hdf7_9
- hdf8_8
- hdr10l_19
- hdr20_17
- hdr50_22
- hdr220_26
- hh020
- hdr35_20

### Model Name Changes

{% hint style="warning" %}
Robot models `hdf7_9`, `hdf8_8`, `hdr20_17`, `hdr50_22`, `hdr220_26`, `hdr35_20` are the renamed versions of models `HH7`, `HH8`, `UH020`, `HH050`, `HS220`, `UH035` respectively.
{% endhint %}

### Contents Included for Each Model

Each supported robot model includes the following:

- **URDF**: Robot URDF with collision meshes
- **Mesh**: 3D models for visualization
- **MoveIt2 Configuration**: Motion planning setup with model-specific soft limits
- **Gazebo Support**: Simulation integration support

### Next Steps

After confirming the robot model, proceed to [System Requirements](../3-requirements/README.md) to verify that your system is properly configured.

[__SOURCE](1-intro/3-requirements/README.md)
# 1.3 System Requirements

This page describes the hardware and software requirements for running the HD Hyundai Robotics ROS2 driver.

### Hardware Requirements

#### Robot Controller
- **Compatible Controllers**: Hi6-N10, Hi6-N20, Hi6-N00(HK), Hi6-N00-60(HK), Hi6-N30(HK), Hi6-N80(HK), Hi6-T15
- **Controller SW Version**: **70.00-00** or higher
- **Operation Mode**: Robot must be set to **REMOTE** mode
- **Network Interface**: Ethernet connection (LAN1, LAN2, or LAN3)

#### Development PC
- **Operating System**: Ubuntu 22.04 LTS or Ubuntu 24.04 LTS
- **Memory**: Minimum 8GB RAM (16GB recommended for simulation)
- **Network**: Ethernet interface for robot communication
- **CPU**: Multi-core processor (4 cores or more recommended)


### Next Steps

Once your system meets all requirements, check [Supported ROS2 Versions](../4-ros2-version/README.md).

[__SOURCE](1-intro/4-ros2-version/README.md)
# 1.4 Supported ROS2 Versions

The HD Hyundai Robotics ROS2 driver supports specific ROS2 distributions that have been tested and validated in robot controller and simulation environments.

### Supported ROS2 Distributions

- **ROS2 Humble Hawksbill** (Ubuntu 22.04 LTS)
- **ROS2 Jazzy Jalisco** (Ubuntu 24.04 LTS)

### Version Verification

After installation, verify your ROS2 setup:

```bash
# Source ROS2 environment
source /opt/ros/$ROS_DISTRO/setup.bash

# Check ROS2 version
ros2 doctor
```

### Next Steps

After confirming ROS2 compatibility, proceed to [Getting Started](../../2-start/README.md) for installation.

[__SOURCE](1-intro/5-hdr-robot/README.md)
# 1.5 Robot Joint and Link Names

HD Hyundai Robotics robots follow the joint and link naming conventions as shown below within the URDF.


### Joint Names

|joint no|joint name </br>(URDF)|joint name </br>(TP)|
|:------:|:---:|:---:|
|1|j1|S|
|2|j2|H|
|3|j3|V|
|4|j4|R2|
|5|j5|B|
|6|j6|R1|


### Link Names

|link No|link Name|
|:------:|:---:|
|0|base_link|
|1|lower_frame_link|
|2|upper_frame_link|
|3|arm_link|
|4|wrist_body_link|
|5|wrist_holder_link|
|6|flange_link|


### Link Relationships

|link No|link Name|joint|parent link|joint type|note|
|:------:|:---:|:---:|:------:|:---:|:---:|
||world||||||
|0|base_link|world_joint|world|fixed|||
|1|lower_frame_link|j1|base_link|revolute||
|2|upper_frame_link|j2|lower_frame_link|revolute||
|3|arm_link|j3|upper_frame_link|revolute||
|4|wrist_body_link|j4|arm_link|revolute||
|5|wrist_holder_link|j5|wrist_body_link|revolute||
|6|flange_link|j6|wrist_holder_link|revolute||
||flange|flange_link-flange|flange_link|fixed|ROS-Industrial standard coordinate system|
||tool0|flange-tool0|flange|fixed|ROS-Industrial standard coordinate system|

[__SOURCE](2-start/README.md)
# 2. Getting Started

This section provides step-by-step instructions for installation, configuration, and execution of the HD Hyundai Robotics ROS2 driver. Follow this guide to set up your development environment and establish communication with the robot.

### Installation and Setup Process

1. [Repository Overview](1-repo-overview/README.md) - Understanding package structure and relationships
2. [Installation](2-installation/README.md) - Repository cloning and build
3. [Initial Setup](3-initial-setup/README.md) - Networking configuration setup
4. [Installation Verification](4-verifying/README.md) - Installation testing

[__SOURCE](2-start/1-repo-overview/README.md)
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

- **[ROS2 Driver (`hdr_ros2_driver`)](../../3-hdr_ros2_driver/README.md)** </br>
Primary ROS2 node providing services for robot control, file management, I/O operations, and system monitoring

- **[HDR Client Driver (`hdr_client_driver`)](../../7-hdr_client_driver/README.md)** </br>
C++ library implementing TCP/UDP communication protocols with HD Hyundai Robotics controllers

- **[ROS2 Control Integration (`hdr_hardware_interface`)](../../4-hdr_hardware_interface/README.md)** </br>
ros2_control SystemInterface for integration with standard ROS2 control framework

- **[Robot Description (`hdr_description`)](../../5-hdr_description/README.md)** </br>
URDF/XACRO, collision/visual mesh, and RViz configuration for supported robot models

- **[MoveIt2 Configuration (`hdr_moveit_config`)](../../6-hdr_moveit_config/README.md)** </br>
Robot model-specific MoveIt2 configuration including SRDF, soft limits, kinematics, and motion planning settings

- **[Gazebo Simulation (`hdr_simulation_gz`)](../../8-hdr_simulation_gz/README.md)** </br>
Gazebo Ignition simulation integration

- **[Custom Messages (`hdr_msgs`)](../../9-hdr_msgs/README.md)** </br>
Custom ROS2 service and message definitions for communication with HD Hyundai Robotics controllers


### Next Steps

1. Review the individual package documentation linked above.
2. Proceed to [Installation](../2-installation/README.md) to build the packages.
3. Configure robot connection in [Initial Setup](../3-initial-setup/README.md).

[__SOURCE](2-start/2-installation/README.md)
# 2.2 Package Build and Installation
This section covers the installation process of the HD Hyundai Robotics ROS2 driver, including repository cloning, dependencies installation, and package build.

### Workspace Setup

#### Create ROS2 Workspace

```bash
# Create workspace directory
mkdir -p ~/hdr_ws/src
cd ~/hdr_ws
```

#### Clone Source Repositories

```bash
cd ~/hdr_ws/src

# HDR core driver and client library
git clone https://github.com/hyundai-robotics/hdr_ros2_driver.git
git clone https://github.com/hyundai-robotics/hdr_client_driver.git

# HDR description package
git clone https://github.com/hyundai-robotics/hdr_description.git

# Gazebo simulation
git clone https://github.com/hyundai-robotics/hdr_simulation_gz.git
```

### Dependencies Installation

#### Install ROS2 Dependencies

```bash
cd ~/hdr_ws

# Update package database
rosdep update

# Install all dependencies for HDR packages
rosdep install --from-paths src --ignore-src --rosdistro $ROS_DISTRO -y
```

### Build Process

#### Standard Build

```bash
cd ~/hdr_ws

# Build all packages with optimization
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Release
```

#### Build Configuration Options
```bash
# Build with debug symbols
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Debug
```

#### Environment Setup

```bash
cd ~/hdr_ws
source install/setup.bash

echo "source ~/hdr_ws/install/setup.bash" >> ~/.bashrc
```

### Next Steps

After successful package installation and build:
1. Proceed to [Initial Setup](../3-initial-setup/README.md) for controller and PC configuration
2. Run [Installation Verification](../4-verifying/README.md) tests

[__SOURCE](2-start/3-initial-setup/README.md)
# 2.3 Controller and PC Communication Setup

This guide covers the configuration of network interfaces on your development PC for communication with HD Hyundai Robotics robot controllers.

### Prerequisites
⚠️ Please verify the following before starting setup:
- **Robot Controller SW Version**: Hi6, Hi7 series controller with SW version **70.00-00** or higher

### Network Configuration Overview

The PC must be configured to communicate with the robot controller via Ethernet. The default configuration uses a 192.168.1.x subnet with the controller at 192.168.1.150.

### Default Network Configuration (Using LAN1)

| Component | Parameter | Default Value |
|-----------|-----------|---------------|
| **PC IP Address** | Static IP | 192.168.1.x (user configured)|
| **Robot Controller IP** | Static IP | 192.168.1.150 |
| **Subnet Mask** | Network Mask | 255.255.255.0 |
| **Gateway** | Default Gateway | 192.168.1.1  |

### Cable Connection

![](../../_assets/controller.png)

1. **Locate Robot Controller Ethernet Port**
   - **Hi6-N Controller**: Ethernet port on top of main module
   - **Hi6-T Controller**: Ethernet port on controller front panel

2. **Connect Ethernet Cable**
   - Use Cat5e or Cat6 Ethernet cable
   - **Recommendation**: Use LAN1 (typically pre-configured to 192.168.1.x)
   - LAN2, LAN3 ports are also available with different default controller IPs: </br>
      LAN2: 192.168.4.150 → PC needs to be configured to 192.168.4.x range </br>
      LAN3: 192.168.3.150 → PC needs to be configured to 192.168.3.x range

3. **Verify Physical Connection**
   - Ensure cable connection is secure
   - Check network port LED indicators (if available)


### PC Network Interface Configuration

![](../../_assets/LAN_com.png)

#### Using Network Manager GUI

##### Ubuntu Desktop (GNOME)

1. **Open Network Settings**
   - Click on the network icon in the top-right corner
   - Select "Wired Settings" or go to Settings → Network

2. **Configure Wired Connection**
   - Click the gear icon next to the wired connection
   - Navigate to the "IPv4" tab

3. **Set Static IP Configuration (Using LAN1)**
   - **Method**: Manual
   - **Address**: 192.168.1.100
   - **Netmask**: 255.255.255.0
   - **Gateway**: 192.168.1.1

4. **Apply Settings**
   - Click "Apply" and disconnect then reconnect the network interface

![](../../_assets/ip_setup.png)

### Verification

#### Verify Network Configuration

```bash
# Test network connectivity
ping -c 4 192.168.1.150
```

![](../../_assets/ping_test.png)

[__SOURCE](2-start/4-verifying/README.md)
# 2.4 Installation Verification

This guide provides verification procedures to confirm that the HD Hyundai Robotics ROS2 driver is properly installed, configured, and ready to operate.


#### Robot Mode Configuration

The HDR ROS2 driver operates only when the robot is in **REMOTE** mode.

Please set the controller to remote control mode by switching the mode switch on the teach pendant (TP) to the REMOTE position before running the ROS2 driver.

![](../../_assets/tp_operate.png)


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

[__SOURCE](3-hdr_ros2_driver/README.md)
# 3. ROS2 Driver (`hdr_ros2_driver`)

The `hdr_ros2_driver` package provides a core ROS2 driver for interfacing with HD Hyundai Robotics' Open API. This driver enables comprehensive communication with robot controllers through REST API, supporting services for robot control, monitoring, file operations, and system management.

### Key Features

- **Robot State Publishing**: Real-time joint state information via `/joint_states` topic
- **Motion Control**: Joint trajectory control through ROS2 actions
- **Comprehensive Services**: Over 30 service endpoints organized by functionality


### Detailed Documentation

- [Launch](1-launch/README.md) - Launch files for driver execution
- [Topics](2-topics/README.md) - Published robot state information
- [Actions](3-actions/README.md) - Joint trajectory execution and motion control
- [Services](4-services/README.md) - API service reference

[__SOURCE](3-hdr_ros2_driver/1-launch/README.md)
# 3.1 HDR ROS2 Driver launch

This section covers how to launch the HDR ROS2 driver.

### Basic Launch

#### HDR ROS2 Driver Launch
```bash
# Launch with default parameters
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py
```

This will start the driver with:
- Default IP: 192.168.1.150
- Default Port: 8888

### Custom Configuration

#### Custom IP and Port
```bash
# Launch with custom network settings
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py \
  openapi_ip:=192.168.0.10 \
  openapi_port:=8080
```

### Launch Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `openapi_ip` | string | `192.168.1.150` | Robot controller server IP address |
| `openapi_port` | int | `8888` | Controller server port number |
| `robot_model` | string | `ha006b` | Robot model name |

### Verification

After launch, verify the driver is running:

```bash
# Check if driver node is active
ros2 node list | grep hdr_ros2_driver

# List available services
ros2 service list | grep hdr_ros2_driver

# Test basic connection
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger
```

### Network Setup Prerequisites

Before launching, ensure proper network configuration:

1. **Ethernet Connection**: Connect PC to robot controller via LAN1, LAN2, or LAN3
2. **Controller IP**: Default 192.168.1.150 (configurable through teaching pendant)
3. **PC IP**: Set to 192.168.1.x range (x ≠ 150)
4. **REMOTE Mode**: Ensure robot controller is in REMOTE mode

### Troubleshooting

#### Common Issues

1. **Connection Timeout**
   - Verify robot IP and port: `ping 192.168.1.150`
   - Check ethernet cable connection

2. **Service Unavailable**
   - Verify driver launched successfully
   - Check ROS2 environment is sourced
   - Check launch output for error messages
   - Ensure robot is in REMOTE mode
   - Verify controller SW version is **70.00-00** or higher
   
[__SOURCE](3-hdr_ros2_driver/2-topics/README.md)
# 3.2 Provided Topics

### Overview

The ROS2 driver publishes real-time robot data through standardized ROS2 topics. These topics provide joint states, robot status information, and diagnostic data for monitoring and control applications.

### Published Topics

#### Joint State Information

##### `/joint_states` (sensor_msgs/msg/JointState)
**Description**: Real-time joint position data

**Message Fields**:
```yaml
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
string[] name          # Joint names matching URDF
float64[] position     # Joint positions in radians
float64[] velocity     # Joint velocity in radians/sec
float64[] effort       # Joint effort in torque
```

**Publishing Frequency**: 50 Hz (configurable via `publish_rate` parameter)

[__SOURCE](3-hdr_ros2_driver/3-actions/README.md)
# 3.3 Available Actions

### Overview

The ROS2 driver provides action interfaces for robot joint trajectory control. Actions enable asynchronous operations with progress feedback and cancellation capabilities.

### Joint Trajectory Control Action

#### `/joint_trajectory_controller/follow_joint_trajectory` (control_msgs/action/FollowJointTrajectory)

**Description**: Executes joint trajectory control.

**action_goal**:
```yaml
trajectory_msgs/JointTrajectory trajectory
  std_msgs/Header header
  actionlib_msgs/GoalID goal_id
    time stamp
    string id
  control_msgs/FollowJointTrajectoryGoal goal
    trajectory_msgs/JointTrajectory trajectory
      std_msgs/Header header
      string[] joint_names
      trajectory_msgs/JointTrajectoryPoint[] points
    control_msgs/JointTolerance[] path_tolerance
      string name
      float64 position
      float64 velocity
      float64 acceleration
    control_msgs/JointTolerance[] goal_tolerance
      string name
      float64 position
      float64 velocity
      float64 acceleration
    duration goal_time_tolerance
```

**action_feedback**:
```yaml
std_msgs/Header header
string[] joint_names
trajectory_msgs/JointTrajectoryPoint desired
trajectory_msgs/JointTrajectoryPoint actual
trajectory_msgs/JointTrajectoryPoint error
```

**action_result**:
```yaml
std_msgs/Header header
actionlib_msgs/GoalStatus status
control_msgs/FollowJointTrajectoryResult result
```

[__SOURCE](3-hdr_ros2_driver/4-services/README.md)
# 3.4 ROS2 Driver Services

### Overview

The `hdr_ros2_driver` provides various ROS2 services for communicating with HD Hyundai Robotics Hi6 controllers.

### Service Categories

| Category | Description |
|----------|-------------|
| **[Control Services](1-control/README.md)** | Robot control, motor power, emergency stop, coordinate systems, I/O management |
| **[Task Management](2-task/README.md)** | Variable assignment, motion execution, program control |
| **[File Management](3-file/README.md)** | File upload/download, directory manipulation |
| **[PLC Communication](4-plc/README.md)** | PLC relay value control |
| **[Console Commands](5-console/README.md)** | Console command execution, system time, log management |
| **[Project Management](6-project/README.md)** | Job information, job deletion/reload |
| **[Version Information](7-version/README.md)** | API version, system version queries |

### Basic Usage

#### Check Service List
```bash
# List all HDR driver services
ros2 service list | grep hdr_ros2_driver
```

#### Common Service Calls
```bash
# Check API version
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger

# Check motor status
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# Turn on motor power
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger
```

[__SOURCE](4-hdr_hardware_interface/README.md)
# 4. ROS2 Control Integration (`hdr_hardware_interface`)

### Overview

The `hdr_hardware_interface` package provides a `ros2_control` SystemInterface to connect HD Hyundai Robotics' Open API-based controllers with the ROS2 control framework. It maps joint position state and command interfaces to HTTP-based robot services, handling controller lifecycle and real-time pose tracking.

### Package Structure

| Directory                           | Description                                                                 |
| ----------------------------------- | ----------------------------------------------------------------------------|
| `include/`                          | C++ headers including `HDRRobotHardware` and utility helpers                |
| `src/`                              | SystemInterface logic implementation                                     |
| `launch/`                           | Launch files for executing the `ros2_control` interface             |
| `config/`                           | YAML configuration files for controller and kinematics settings   |
| `hdr_hardware_interface_plugin.xml` | Metadata for pluginlib                                               |

---

### Usage

###### Launch HDR hardware interface with ros2_control

```bash
ros2 launch hdr_hardware_interface ros2_control.launch.py \
  robot_model:=hdf7_9 \
  openapi_ip:=192.168.1.150 \
  openapi_port:=8888
```

###### Plugin Configuration
To enable the hardware interface, include it within the `<ros2_control>` in URDF or xacro

```xml
<ros2_control name="HDRRobotHardware" type="system">
  <hardware>
    <plugin>hdr_hardware_interface/HDRRobotHardware</plugin>
    <param name="robot_model">ha006b</param>
    <param name="openapi_ip">192.168.1.150</param>
    <param name="openapi_port">8888</param>
  </hardware>
</ros2_control>
```

##### Configuration Options

| Parameter                      | Type   | Default                         | Description                                                                 |
|---------------------------|--------|----------------------------------|-----------------------------------------------------------------------------|
| `robot_model`             | string | `"ha006b"`                      | Robot model name                               |
| `openapi_ip`              | string | `"192.168.1.150"`               | HTTP API IP address of the robot controller                                  |
| `command_start_time`   | float  | `-1.0`                          | Command execution time (-1.0 for immediate execution)             |
| `command_buffer_size`  | int    | `5`                             | Command data buffer size                                 |
| `use_sim`                 | bool   | `false`                         | Enable simulation mode using the `gz_ros2_control/GazeboSimSystem` plugin, typically used for integration with Ignition Gazebo<br>The `use_sim_time` parameter is also set to true for synchronization with simulation time     |
| `use_mock_hardware`       | bool   | `false`                         | Enable mock hardware interface using `mock_components/GenericSystem` for testing without a robot   |
| `initial_positions_file`  | string | `""`                            | Optional YAML file specifying initial joint positions                       |
| `controllers_config_package` | string | `"hdr_hardware_interface"`     | Package name containing config YAML                                       |
| `controllers_file`        | string | `"default_controllers.yaml"`   | Controller configuration YAML filename                                     |
| `kinematics_file`         | string | `"default_kinematics.yaml"`    | Kinematics plugin configuration YAML filename                              |


##### Topics

| Topic Name                   | Message Type                   | Description                               |
| ---------------------------- | ------------------------------ | ----------------------------------------- |
| `/joint_states`              | sensor_msgs::msg::JointState | Publishes current joint states including position information |
| `/controller_manager/status` | lifecycle_msgs::msg::State   | Lifecycle state of the ros2_control manager |

##### Actions

| Action Name                                            | Action Type                                   | Description                                |
| ------------------------------------------------------ | --------------------------------------------- | ------------------------------------------ |
| `/joint_trajectory_controller/follow_joint_trajectory` | control_msgs::action::FollowJointTrajectory | Execute joint trajectory commands through ROS2 action |

##### Services

| Service Name                                   | Service Type                                         | Description                         |
| ---------------------------------------------- | ---------------------------------------------------- | ----------------------------------- |
| `/controller_manager/list_controllers`         | controller_manager_msgs/srv/ListControllers        | Return list of active controllers     |
| `/controller_manager/list_hardware_interfaces` | controller_manager_msgs/srv/ListHardwareInterfaces | Return available joint command and state interfaces |
| `/controller_manager/switch_controller`        | controller_manager_msgs/srv/SwitchController       | Activate or deactivate controllers  |
| `/controller_manager/load_controller`          | controller_manager_msgs/srv/LoadController         | Load a controller             |
| `/controller_manager/unload_controller`        | controller_manager_msgs/srv/UnloadController       | Unload the specified controller.    |

---

[__SOURCE](5-hdr_description/README.md)
# 5. Robot URDF (`hdr_description`)

The `hdr_description` package contains robot URDF, meshes, and visualization configurations for HD Hyundai Robotics robots in ROS2. This package provides essential URDF/XACRO definitions needed for simulation, visualization, and motion planning.

### Key Features

- **Robot Model-Specific URDF**: URDF/XACRO files for all supported robot models
- **3D Meshes**: Collision and visual meshes for accurate simulation
- **RViz Integration**: Pre-configured visualization settings
- **ros2_control Integration**: Joint interface definitions

### Package Structure

| Directory | Contents | Purpose |
|-----------|----------|----------|
| `urdf/` | Robot URDF files | URDF/XACRO definitions |
| `meshes/` | 3D model mesh files | Collision and visual representation |
| `launch/` | Visualization launch files | RViz display configuration |
| `rviz/` | RViz configuration files | Display settings and plugins |

### URDF Configuration

#### Main Files
- **`hdr.urdf.xacro`**: Top-level macro including all components
- **`hdr.ros2_control.xacro`**: ros2_control hardware interface macro

#### Robot-Specific Files
Each robot model has its own directory under `urdf/robots/`:
- `ha006b.urdf.xacro`
- `hdf7_9.urdf.xacro`
- `hdf8_8.urdf.xacro`
- `hdr10l_19.urdf.xacro`
- `hdr20_17.urdf.xacro`
- `hdr50_22.urdf.xacro`
- `hdr220_26.urdf.xacro`
- `hh020.urdf.xacro`
- `hdr35_20.urdf.xacro`

### Usage Examples

#### Visualization in RViz
```bash
ros2 launch hdr_description display_robot.launch.py robot_model:=ha006b
```

#### Launch Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `robot_model` | string | `ha006b` | Robot model to display |
| `description_package` | string | `hdr_description` | Package containing URDF files |
| `description_file` | string | `hdr.urdf.xacro` | Main URDF/XACRO file |

### Mesh Quality

The package provides two types of meshes for each robot:

#### Visual Meshes
- High-resolution meshes for realistic visualization
- Detailed surface textures and materials
- Used for visual representation in RViz and Gazebo

#### Collision Meshes
- Simplified meshes for collision detection
- Optimized for computational efficiency
- Used by physics engines and motion planners

For model-specific details, see [Supported Robot Models](../1-intro/2-robot-models/README.md).

[__SOURCE](6-hdr_moveit_config/README.md)
# 6. MoveIt2 Configuration (`hdr_moveit_config`)

The `hdr_moveit_config` package provides MoveIt2 configuration packages for controlling HD Hyundai Robotics robots in both real and simulation environments. This package includes robot-specific motion planning configurations with SRDF definitions, joint limits, and controller settings.

### Key Features

- **Robot-Specific Configuration**: Individual MoveIt2 settings for each supported robot model
- **SRDF Definitions**: Semantic robot description with planning groups and poses
- **Joint Limits Management**: Velocity and acceleration scaling for safe operation
- **Kinematics Integration**: Forward/inverse kinematics solver configuration
- **Controller Integration**: ros2_control and trajectory execution setup

### Package Organization

Each robot model has its own MoveIt2 configuration package:

- `ha006b_moveit_config/`
- `hdf7_9_moveit_config/`
- `hdf8_8_moveit_config/`
- `hdr10l_19_moveit_config/`
- `hdr20_17_moveit_config/`
- `hdr50_22_moveit_config/`
- `hdr220_26_moveit_config/`
- `hh020_moveit_config/`
- `hdr35_20_moveit_config/`

### Configuration Files

Each robot configuration includes:

#### Core Configuration
- **SRDF Files**: Semantic robot description with planning groups
- **joint_limits.yaml**: Velocity and acceleration limits with scaling factors
- **kinematics.yaml**: Kinematics solver plugin configuration
- **controllers.yaml**: ros2_control trajectory controller settings

#### Advanced Settings
- **ompl_planning.yaml**: OMPL motion planner configuration
- **pilz_cartesian_limits.yaml**: Cartesian motion limits for Pilz planner
- **sensors_3d.yaml**: 3D sensor integration (if applicable)
- **initial_positions.yaml**: Default starting poses

### Safety Considerations

#### Velocity Scaling
**≤ 0.5** scaling factors are recommended for stable operation:

```yaml
default_velocity_scaling_factor: 0.5
default_acceleration_scaling_factor: 0.5
```

#### Joint Limits
The `joint_limits.yaml` file defines:
- Maximum joint velocities
- Maximum joint accelerations
- Software position limits
- Scaling factors for motion planning

### Launch

```bash
ros2 launch hdr_bringup hdr_moveit.launch.py robot_model:=ha006b
```

![](../_assets/hdr_moveit.png)

### Planning Groups

Typical SRDF planning group configuration:

```xml
<group name="manipulator">
    <chain base_link="base_link" tip_link="link6"/>
</group>

<group_state name="home" group="manipulator">
    <joint name="j1" value="0"/>
    <joint name="j2" value="0"/>
    <joint name="j3" value="0"/>
    <joint name="j4" value="0"/>
    <joint name="j5" value="0"/>
    <joint name="j6" value="0"/>
</group_state>
```


### Customization

To modify motion planning behavior:
1. Edit `joint_limits.yaml` for velocity/acceleration limits (cannot exceed maximum velocities defined per joint in URDF)
2. Modify `ompl_planning.yaml` for planner-specific settings
3. Update SRDF for new planning groups or poses
4. Adjust controller parameters in `controllers.yaml`

[__SOURCE](7-hdr_client_driver/README.md)
# 7. HD Hyundai Robotics Client Driver

The HDR client driver provides a comprehensive C++ library for communicating with HD Hyundai Robotics robot controllers via HTTP (Open API) and socket (TCP/UDP) interfaces. This library abstracts both communication layers and provides object-oriented interfaces for robot control and monitoring, file management, real-time command execution, and integration with ROS2.

{% hint style="warning" %}
All REST API-based communication requires the robot to be in REMOTE mode.
{% endhint %}

### Package Structure

| Directory | Description |
|-----------|-------------|
| `include/` | Header files for the HDR client driver library |
| `src/` | Source implementation of client driver functions |
| `src/functions/` | API category implementations for various robot controller functions |
| `examples/` | Example programs demonstrating how to use the driver APIs |

[__SOURCE](7-hdr_client_driver/1-api-categories/README.md)
# 7.1 API Categories

The HDR client driver supports the following API categories:

### Supported API Categories

The HDR client driver provides the following API categories corresponding to various functions of the robot controller:

- **[Control](1-control/README.md)** - Basic robot control operations
- **[Robot](2-robot/README.md)** - Robot motion and status management
- **[Project](3-project/README.md)** - Project and job management
- **[File](4-file/README.md)** - File system operations
- **[I/O](5-io/README.md)** - Input/output control
- **[Task](6-task/README.md)** - Task execution and variable management
- **[Miscellaneous](7-etc/README.md)** - System utilities

[__SOURCE](7-hdr_client_driver/1-api-categories/1-control/README.md)
# 7.1.1 Control API

### Overview

The Control API category provides basic robot control operations including motor management, coordinate system handling, and motion mode control. These APIs form the foundation for all robot operations.

### Available Control APIs

| Function | Description |
|----------|-------------|
| `GetControlOpCnd` | Retrieve robot controller's execution condition configuration (playback mode, step back maximum speed, user coordinate number) |
| `GetControlIosDio` | Read specific digital I/O signal values (supported types: "di", "dib", "diw", "dil", "dif", "do", "dob", "dow", "dol", "dof") |
| `GetControlIosSio` | Query special I/O (SIO) signal values (input types: "si", "sib" etc., output types: "so", "sob" etc.) |
| `GetControlUcsNos` | Retrieve list of available user coordinate system (UCS) numbers for motion programming |
| `PostControlIosDio` | Set digital output (DO) signal values (type, block number, signal number, value) |
| `PutControlOpCnd` | Update operation condition parameters (playback mode, reverse motion maximum speed, user coordinate system) |

[__SOURCE](7-hdr_client_driver/1-api-categories/2-robot/README.md)
# 7.1.2 Robot API

### Overview

The Robot API category handles core robot operations including motion control, position management, tool configuration, and safety systems. These APIs provide direct control over robot movement and status monitoring.

### Available Robot APIs

| Function | Description |
|----------|-------------|
| `GetRobotMotorState` | Check robot servo motor power status (ON/OFF), useful for checking motion command readiness |
| `GetRobotPoCur` | Current robot pose (position and orientation) with various options (job index, coordinate system, etc.) |
| `GetRobotCurTool` | Retrieve currently selected tool information (TCP configuration, weight, etc.) |
| `GetRobotTools` | Retrieve list of all tools registered in the system (TCP offsets, weights, etc.) |
| `GetRobotToolsT` | Query specific tool's detailed information by tool number (0-31) |
| `GetJointTrajBuffAvail` | Get the available size of the trajectory buffer |
| `PostRobotMotorPower` | Turn robot motor power ON or OFF |
| `PostRobotOperation` | Start or stop robot program execution |
| `PostRobotToolNo` | Set active tool number to use (0-31) |
| `PostRobotCrdSys` | Specify coordinate system to use for motion and I/O (-1: default, 0: base, 1: tool, 2: user1, 3: user2) |
| `PostRobotEmergencyStop` | Immediate emergency stop of all robot motion for safety response |
| `PostInitJointTrajectory` | Initialize the joint trajectory buffer |
| `PostInsertJointTrajectoryPoints` | Insert joint trajectory points into the controller buffer for motion execution |

[__SOURCE](7-hdr_client_driver/1-api-categories/3-project/README.md)
# 7.1.3 Project API

### Overview

The Project API category provides project and job management functions for the HD Hyundai Robotics controller. These APIs enable monitoring project execution status, querying job information, and managing jobs.

### Available Project APIs

| Function | Description |
|----------|-------------|
| `GetProjectRgen` | Query current project execution status (0: not running, 1: running, 2: paused) |
| `GetProjectJobsInfo` | Retrieve metadata of all jobs registered in the project (name, path, modification status) |
| `PostProjectReloadUpdateJobs` | Reload and synchronize externally modified jobs to update in-memory job status |
| `PostProjectDeleteJob` | Delete specified job file from project path |

[__SOURCE](7-hdr_client_driver/1-api-categories/4-file/README.md)
# 7.1.4 File API

### Overview

The File API category provides file system operations for the HD Hyundai Robotics controller. These APIs enable remote file management, file upload/download, and directory management.

### Available File APIs

| Function | Description |
|----------|-------------|
| `GetFiles` | Retrieve list of files and folders at specified path |
| `GetFileInfo` | Query metadata of file or directory (size, timestamp, type) |
| `GetFileList` | Retrieve filtered list including files only, directories only, or all |
| `GetFileExist` | Check existence of specified file or directory |
| `PostRenameFile` | Rename or move file or directory from one path to another |
| `PostMkdir` | Create new directory at specified path |
| `PostFiles` | Upload local file to specified location on controller |
| `PostDeleteFile` | Delete file or directory on controller |

[__SOURCE](7-hdr_client_driver/1-api-categories/5-io/README.md)
# 7.1.5 I/O API

### Overview

The I/O API category provides PLC communication functions for the HD Hyundai Robotics controller. These APIs enable querying and setting relay values in the Hi6, Hi7 PLC.

### Available I/O APIs

| Function | Description |
|----------|-------------|
| `GetRelayValue` | Query relay values from Hi6, Hi7 PLC using "FB{index}.{relay_type}" format or simple formats like "M", "S" |
| `SetRelayValue` | Set specific relay values in the robot controller's internal PLC. Supports various data type suffixes |

[__SOURCE](7-hdr_client_driver/1-api-categories/6-task/README.md)
# 7.1.6 Task API

### Overview

The Task API category provides task execution and variable management functions for the HD Hyundai Robotics controller. These APIs enable variable assignment, wait state release, program counter control, expression evaluation, and direct motion command execution.

### Available Task APIs

| Function | Description |
|----------|-------------|
| `PostAssignVar` | Assign variables to task using expressions or JSON values (supports local/global scope and persistence) |
| `PostReleaseWait` | Release task[0] from WAIT state to resume paused task |
| `PostSetCurPcIdx` | Manually set program counter (PC) index for task[0] (useful for debugging or jumping to specific logic) |
| `PostSolveExpr` | Evaluate expressions within task scope (supports math, logic, and variable access) |
| `PostExecuteMove` | Execute direct movement commands in robot task (L, P, SP, etc.) |

[__SOURCE](7-hdr_client_driver/1-api-categories/7-etc/README.md)
# 7.1.7 Miscellaneous API

### Overview

The Miscellaneous API category provides additional utility and system management functions for the HD Hyundai Robotics controller. These APIs include system time management and log query capabilities.

### Available Miscellaneous APIs

| Function | Description |
|----------|-------------|
| `GetDateTime` | Query current system date and time from robot controller (year, month, day, hour, minute, second) |
| `PutDateTime` | Set system date and time on robot controller (includes input validation) |
| `GetLogManager` | Query controller logs with filtering options (entry count, categories E,W,N,S,O,I,P,H,C,M, ID range, timestamp range) |

[__SOURCE](8-hdr_simulation_gz/README.md)
# 8. Gazebo Simulation (`hdr_simulation_gz`)

The `hdr_simulation_gz` package provides a ROS2 + Gazebo (Ignition) simulation environment for HD Hyundai Robotics industrial robots. This package enables development, testing, and validation of robotic applications without physical hardware.

### Key Features

- **Gazebo Integration**: Ignition Gazebo simulation support
- **Physics Simulation**: Realistic robot dynamics and collision detection
- **MoveIt2 Compatibility**: Motion planning in simulation environment
- **ros2_control Integration**: Uses `gz_ros2_control/GazeboSimSystem` plugin

### Package Structure

| Directory | Contents | Purpose |
|-----------|----------|----------|
| `launch/` | Simulation launch files | Robot spawning and controller setup |
| `config/` | Controller configuration files | ros2_control YAML files |

### Launch Files

#### Robot Spawning
```bash
# Spawn robot with ros2_control in Gazebo
ros2 launch hdr_simulation_gz hdr_gz_spawn.launch.py robot_model:=ha006b
```

#### MoveIt2 Integration
```bash
# Run simulation with MoveIt2 motion planning
ros2 launch hdr_simulation_gz hdr_gz_moveit.launch.py robot_model:=hdr50_22
```

### Configuration Options

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `robot_model` | string | `ha006b` | Robot model to simulate |
| `use_sim` | bool | `true` | Enable Gazebo simulation mode |
| `runtime_config_package` | string | `hdr_simulation_gz` | Controller configuration package |
| `controllers_file` | string | `hdr_controllers.yaml` | Controller configuration file |
| `description_package` | string | `hdr_description` | URDF package name |
| `description_file` | string | `hdr.urdf.xacro` | Robot description file |
| `initial_positions_file` | string | `initial_positions.yaml` | Initial joint positions |
| `kinematics_file` | string | `kinematics.yaml` | Kinematics solver configuration |


### Future Improvements
- Sensor and tool simulation support
- World and example scenario support

[__SOURCE](9-hdr_msgs/README.md)
# 9. HD Hyundai Robotics ROS2 Messages

### Overview

The `hdr_msgs` package defines custom ROS2 message types used in the HD Hyundai Robotics software stack.


### ROS2 Messages

| Message Type          | Description                                           |
|-----------------------|-------------------------------------------------------|
| `srv/DateTime.srv`    | Gets or sets the system time of the robot controller. Input includes full date/time fields (year, mon, day, hour, min, sec). |
| `srv/Emergency.srv`   | Tests emergency stop logic using step parameters (step_no, stop_at, stop_mode). Used for simulation/testing scenarios. |
| `srv/ExecuteCmd.srv`  | Executes console commands as a list of string lines with configurable execution intervals. Useful for raw low-level commands like rl.stop. |
| `srv/ExecuteMove.srv` | Executes robot movement commands using string-based statements. Example: "move L,spd=1sec,tool=1 [0, 0, 0, 0, 90, 0]". task_no identifies the task index (typically 0). |
| `srv/FileList.srv`    | Queries directory contents on the robot. Can filter to include files or directories through boolean values. |
| `srv/FilePath.srv`    | Sends or queries file paths for operations like reading, deletion, or existence checking. |
| `srv/FileRename.srv`  | Renames or moves files in the robot controller's file system. |
| `srv/FileSend.srv`    | Uploads files from local PC to robot controller. Requires source and destination paths. |
| `srv/IoplcGet.srv`    | Reads PLC memory (e.g., relays, M, S, R). Supports both direct addressing and name-based signal addressing. |
| `srv/IoplcPost.srv`   | Writes to PLC memory (relays) using symbolic names such as M, S, R, or FBx.y. |
| `srv/IoRequest.srv`   | Used to access digital, serial, or user I/O. The type field specifies I/O kind like 'di', 'do', 'si', or 'so'. blk_no and sig_no specify block and signal indices. The 'val' field is used when setting I/O values and ignored during read operations. |
| `srv/JointTrajecotryPoints.srv` | Provides trajectory points for executing motion |
| `srv/LogManager.srv`  | Queries log entries using category (E, W, etc.), ID ranges, and timestamp filters. |
| `srv/Number.srv`      | General-purpose service for sending/receiving integers. Used for tool numbers, coordinate systems, index settings, etc. |
| `srv/OpCnd.srv`       | Reads or writes operating conditions such as playback mode or user coordinate systems. |
| `srv/PoseCur.srv`     | Gets current robot pose (position + orientation) in joint space or workspace according to internal configuration. |
| `srv/ProgramCnt.srv`  | Sets program execution pointer (pno, sno, fno, etc.) to move to specific positions in task logic. |
| `srv/ProgramVar.srv`  | Reads or assigns variables. Can specify scope (local/global), expressions, and persistence. |

[__SOURCE](10-running/README.md)
# 10. ROS2 Driver Execution and Robot Control

### Overview

This section provides a comprehensive guide for operating HD Hyundai Robotics robots using the ROS2 driver.

The HD Hyundai Robotics ROS2 system provides the following control methods:

- **MoveIt2 Integration**: Motion planning and execution
- **ros2_control**: Hardware interface control
- **ROS2 Services**: Controller API access

### Next Steps

- [MoveIt2 Launch Procedures](1-launch-moveit2/README.md)
- [Direct ros2_control Control](2-launch-ros2_control/README.md)

[__SOURCE](10-running/1-launch-moveit2/README.md)
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

[__SOURCE](10-running/2-launch-ros2_control/README.md)
# 10.2 ros2_control System Execution

### Overview

Explains basic execution methods for the ros2_control system for HD Hyundai Robotics robots.

### Basic Execution

#### Launch ros2_control
```bash
# Basic launch
ros2 launch hdr_bringup hdr_control.launch.py robot_model:=ha006b

# Specify IP address
ros2 launch hdr_bringup hdr_control.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

### Controllers

#### Check Controller Status
```bash
# List controllers
ros2 control list_controllers

# Check hardware interfaces
ros2 control list_hardware_interfaces

# Check joint states
ros2 topic echo /joint_states
```

#### Activate/Deactivate Controllers
```bash
# Activate controller
ros2 control switch_controllers --activate joint_trajectory_controller 

# Deactivate controller
ros2 control switch_controllers --deactivate joint_trajectory_controller
```

### Default Controller Configuration

ros2_control provides the following controllers:

- **joint_state_broadcaster**: Publishes joint states
- **joint_trajectory_controller**: Trajectory following control

### Simple Testing

#### Joint Trajectory Test
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

### Troubleshooting

#### Common Issues

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

### Safety Precautions

- Always keep emergency stop button accessible when working with actual robots
- Immediately emergency stop if robot exhibits unexpected behavior
- Test at low speeds when using for the first time
