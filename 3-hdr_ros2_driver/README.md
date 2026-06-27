# 3. ROS2 Driver (`hdr_ros2_driver`)

`hdr_ros2_driver` 包提供了与 HD Hyundai Robotics 的开放 API 接口的核心 ROS2 驱动程序。此驱动程序通过 REST API 使与机器人控制器的全面通信成为可能，支持机器人控制、监控、文件操作和系统管理的服务。

- [源代码] [hdr_ros2_driver] [GitHub 仓库 ↗](https://github.com/hyundai-robotics/hdr_ros2_driver)

### 主要特性

- **机器人状态发布**：通过 `/joint_states` 主题实时关节状态信息
- **运动控制**：通过 ROS2 动作进行关节轨迹控制
- **全面服务**：按功能组织的 30 多个服务端点

### 详细文档

- [启动](1-launch/README.md) - 驱动程序执行的启动文件
- [主题](2-topics/README.md) - 发布的机器人状态信息
- [动作](3-actions/README.md) - 关节轨迹执行和运动控制
- [服务](4-services/README.md) - API 服务参考