# 3. ROS2 驱动程序 (`hdr_ros2_driver`)

`hdr_ros2_driver` 包提供了一个核心 ROS2 驱动程序，用于与 HD 现代机器人公司的开放 API 进行接口。这种驱动程序通过 REST API 实现与机器人控制器的全面通信，支持机器人控制、监控、文件操作和系统管理的服务。

### 关键特性

- **机器人状态发布**：通过 `/joint_states` 主题提供实时关节状态信息
- **运动控制**：通过 ROS2 动作进行关节轨迹控制
- **全面服务**：按功能组织的超过 30 个服务端点


### 详细文档

- [启动说明](1-launch/README.md) - 驱动程序执行的启动文件
- [配置参数](2-parameters/README.md) - 启动中可用的参数
- [提供的话题](3-topics/README.md) - 发布的机器人状态信息
- [可用的动作](4-actions/README.md) - 关节轨迹执行和运动控制
- [支持的 ROS2 服务](5-services/README.md) - API 服务参考