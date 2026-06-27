# 1.4 支持的 ROS2 版本

HD Hyundai Robotics ROS2 驱动程序支持在机器人控制器和仿真环境中经过测试和验证的特定 ROS2 发行版。

### 支持的 ROS2 发行版

- **ROS2 Humble Hawksbill** (Ubuntu 22.04 LTS)
- **ROS2 Jazzy Jalisco** (Ubuntu 24.04 LTS)

### 版本验证

安装后，验证您的 ROS2 设置：

```bash
# 来源 ROS2 环境
source /opt/ros/$ROS_DISTRO/setup.bash

# 检查 ROS2 版本
ros2 doctor
```

### 后续步骤

确认 ROS2 兼容性后，请继续阅读 [Getting Started](../../2-start/README.md) 进行安装。