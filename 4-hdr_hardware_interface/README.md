# 4. ROS2 Control Integration (`hdr_hardware_interface`)

### Overview

The `hdr_hardware_interface` package provides a `ros2_control` SystemInterface to connect HD Hyundai Robotics' Open API-based controllers with the ROS2 control framework. It maps joint position state and command interfaces to HTTP-based robot services, handling controller lifecycle and real-time pose tracking.

### Package Structure

| Directory                           | Description                                                                 |
| ----------------------------------- | ----------------------------------------------------------------------------|
| `include/`                          | C++ 头文件，包括 `HDRRobotHardware` 和工具助手               |
| `src/`                              | SystemInterface 逻辑实现                                     |
| `launch/`                           | 执行 `ros2_control` 接口的启动文件             |
| `config/`                           | 控制器和运动学设置的 YAML 配置文件   |
| `hdr_hardware_interface_plugin.xml` | 插件的元数据                                               |

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
要启用硬件接口，请将其包含在 URDF 或 xacro 的 `<ros2_control>` 中

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
| `robot_model`             | string | `"ha006b"`                      | 机器人模型名称                               |
| `openapi_ip`              | string | `"192.168.1.150"`               | 机器人控制器的 HTTP API IP 地址                                  |
| `command_start_time`   | float  | `-1.0`                          | 命令执行时间 (-1.0 表示立即执行)             |
| `command_buffer_size`  | int    | `5`                             | 命令数据缓冲区大小                                 |
| `use_sim`                 | bool   | `false`                         | 启用使用 `gz_ros2_control/GazeboSimSystem` 插件的仿真模式，通常用于与 Ignition Gazebo 的集成<br>`use_sim_time` 参数也设置为 true，以便与仿真时间同步     |
| `use_mock_hardware`       | bool   | `false`                         | 启用使用 `mock_components/GenericSystem` 的模拟硬件接口，以便在没有机器人时进行测试   |
| `initial_positions_file`  | string | `""`                            | 可选的 YAML 文件，用于指定初始关节位置                       |
| `controllers_config_package` | string | `"hdr_hardware_interface"`     | 包含配置 YAML 的包名称                                       |
| `controllers_file`        | string | `"default_controllers.yaml"`   | 控制器配置 YAML 文件名                                     |
| `kinematics_file`         | string | `"default_kinematics.yaml"`    | 运动学插件配置 YAML 文件名                              |


##### Topics

| Topic Name                   | Message Type                   | Description                               |
| ---------------------------- | ------------------------------ | ----------------------------------------- |
| `/joint_states`              | sensor_msgs::msg::JointState | 发布当前关节状态，包括位置信息 |
| `/controller_manager/status` | lifecycle_msgs::msg::State   | ros2_control 管理器的生命周期状态 |

##### Actions

| Action Name                                            | Action Type                                   | Description                                |
| ------------------------------------------------------ | --------------------------------------------- | ------------------------------------------ |
| `/joint_trajectory_controller/follow_joint_trajectory` | control_msgs::action::FollowJointTrajectory | 通过 ROS2 动作执行关节轨迹命令 |

##### Services

| Service Name                                   | Service Type                                         | Description                         |
| ---------------------------------------------- | ---------------------------------------------------- | ----------------------------------- |
| `/controller_manager/list_controllers`         | controller_manager_msgs/srv/ListControllers        | 返回活动控制器的列表     |
| `/controller_manager/list_hardware_interfaces` | controller_manager_msgs/srv/ListHardwareInterfaces | 返回可用的关节命令和状态接口 |
| `/controller_manager/switch_controller`        | controller_manager_msgs/srv/SwitchController       | 激活或停用控制器  |
| `/controller_manager/load_controller`          | controller_manager_msgs/srv/LoadController         | 加载控制器             |
| `/controller_manager/unload_controller`        | controller_manager_msgs/srv/UnloadController       | 卸载指定的控制器。    |

---