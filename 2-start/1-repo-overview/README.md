# 2.1 仓库概述

HD Hyundai Robotics ROS2 驱动程序由多个相互连接的包组成，这些包共同提供机器人控制、仿真和运动规划功能。

### 仓库架构

```
HD Hyundai Robotics ROS2 Driver

hdr_ros2_driver            # 主仓库
   hdr_bringup             # 机器人集成和控制启动文件
   hdr_ros2_driver         # 核心通信驱动
   hdr_hardware_interface  # ros2_control 集成
   hdr_moveit_config       # MoveIt 配置
   hdr_msgs                # HD Robotics 自定义消息定义

hdr_client_driver          # C++ 客户端库

hdr_description            # 机器人 URDF 模型和网格

hdr_simulation_gz          # Gazebo 仿真集成
```

### 仓库内的包详情

- **[ROS2 驱动程序 (`hdr_ros2_driver`)](../../3-hdr_ros2_driver/README.md)** </br>
提供机器人控制、文件管理、I/O 操作和系统监控服务的主要 ROS2 节点

- **[HDR 客户端驱动程序 (`hdr_client_driver`)](../../7-hdr_client_driver/README.md)** </br>
实现与 HD Hyundai Robotics 控制器的 TCP/UDP 通信协议的 C++ 库

- **[ROS2 控制集成 (`hdr_hardware_interface`)](../../4-hdr_hardware_interface/README.md)** </br>
与标准 ROS2 控制框架集成的 ros2_control SystemInterface

- **[机器人描述 (`hdr_description`)](../../5-hdr_description/README.md)** </br>
支持的机器人模型的 URDF/XACRO、碰撞/视觉网格和 RViz 配置

- **[MoveIt2 配置 (`hdr_moveit_config`)](../../6-hdr_moveit_config/README.md)** </br>
特定于机器人模型的 MoveIt2 配置，包括 SRDF、软限制、运动学和运动规划设置

- **[Gazebo 仿真 (`hdr_simulation_gz`)](../../8-hdr_simulation_gz/README.md)** </br>
Gazebo Ignition 仿真集成

- **[自定义消息 (`hdr_msgs`)](../../9-hdr_msgs/README.md)** </br>
与 HD Hyundai Robotics 控制器通信的自定义 ROS2 服务和消息定义


### 下一步

1. 查看上述链接的各个包文档。
2. 前往 [安装](../2-installation/README.md) 来构建包。
3. 在 [初始设置](../3-initial-setup/README.md) 中配置机器人连接。