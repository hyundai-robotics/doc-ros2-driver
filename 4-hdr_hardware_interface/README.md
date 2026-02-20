# 4. ROS2 控制集成 (`hdr_hardware_interface`)

### 概述

`hdr_hardware_interface` 包提供 `ros2_control` SystemInterface，以将 HD 现代机器人基于开放 API 的控制器与 ROS2 控制框架连接。它将关节位置状态和命令接口映射到基于 HTTP 的机器人服务，处理控制器生命周期和实时姿态跟踪。

### 包结构

| 目录                               | 描述                                                                     |
| ---------------------------------- | ------------------------------------------------------------------------ |
| `include/`                         | 包含 `HDRRobotHardware` 和工具助手的 C++ 头文件                            |
| `src/`                             | SystemInterface 逻辑实现                                                |
| `launch/`                          | 用于执行 `ros2_control` 接口的启动文件                                   |
| `config/`                          | 控制器和运动学设置的 YAML 配置文件                                        |
| `hdr_hardware_interface_plugin.xml` | 插件库的元数据                                                           |

---

### 用法

###### 使用 ros2_control 启动 HDR 硬件接口

```bash
ros2 launch hdr_hardware_interface ros2_control.launch.py \
  robot_model:=hdf7_9 \
  openapi_ip:=192.168.1.150 \
  openapi_port:=8888
```

###### 插件配置
要启用硬件接口，请在 URDF 或 xacro 中包含它到 `<ros2_control>` 内

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

##### 配置选项

| 参数                         | 类型    | 默认                              | 描述                                                                   |
|---------------------------|---------|----------------------------------|------------------------------------------------------------------------|
| `robot_model`             | 字符串  | `"ha006b"`                       | 机器人型号名称                                                       |
| `openapi_ip`              | 字符串  | `"192.168.1.150"`                | 机器人控制器的 HTTP API IP 地址                                      |
| `command_start_time`   | 浮点数  | `-1.0`                           | 命令执行时间（-1.0 表示立即执行）                                      |
| `command_buffer_size`  | int    | ` (5)`                             | 命令数据缓冲区大小                                 |
| `use_sim`                 | bool   | `false`                         | 启用使用`gz_ros2_control/GazeboSimSystem`插件的仿真模式，通常用于与Ignition Gazebo的集成<br>`use_sim_time`参数也设置为true以与仿真时间同步     |
| `use_mock_hardware`       | bool   | `false`                         | 启用使用`mock_components/GenericSystem`的虚拟硬件接口，以在没有机器人的情况下进行测试   |
| `initial_positions_file`  | string | `""`                            | 可选的YAML文件，指定初始关节位置                       |
| `controllers_config_package` | string | `"hdr_hardware_interface"`     | 包含配置YAML的包名称                                       |
| `controllers_file`        | string | `"default_controllers.yaml"`   | 控制器配置YAML文件名                                     |
| `kinematics_file`         | string | `"default_kinematics.yaml"`    | 运动学插件配置YAML文件名                              |


##### Topics

| Topic Name                   | Message Type                   | Description                               |
| ---------------------------- | ------------------------------ | ----------------------------------------- |
| `/joint_states`              | sensor_msgs::msg::JointState | 发布当前关节状态，包括位置信息 |
| `/controller_manager/status` | lifecycle_msgs::msg::State   | ros2_control管理器的生命周期状态 |

##### Actions

| Action Name                                            | Action Type                                   | Description                                |
| ------------------------------------------------------ | --------------------------------------------- | ------------------------------------------ |
| `/joint_trajectory_controller/follow_joint_trajectory` | control_msgs::action::FollowJointTrajectory | 通过ROS2动作执行关节轨迹命令 |

##### Services

| Service Name                                   | Service Type                                         | Description                         |
| ---------------------------------------------- | ---------------------------------------------------- | ----------------------------------- |
| `/controller_manager/list_controllers`         | controller_manager_msgs/srv/ListControllers        | 返回活动控制器列表     |
| `/controller_manager/list_hardware_interfaces` | controller_manager_msgs/srv/ListHardwareInterfaces | 返回可用的关节命令和状态接口 |
| `/controller_manager/switch_controller`        | controller_manager_msgs/srv/SwitchController       | 激活或停用控制器  |
| `/controller_manager/load_controller`          | controller_manager_msgs/srv/LoadController         | 加载控制器             |
| `/controller_manager/unload_controller`        | controller_manager_msgs/srv/UnloadController       | 卸载指定的控制器。    |