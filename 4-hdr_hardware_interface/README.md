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
