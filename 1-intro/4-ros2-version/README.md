# 1.4 支持的 ROS2 版本

HD 现代机器人 ROS2 驱动程序支持在机器人控制器和仿真环境中经过测试和验证的特定 ROS2 发行版。

### 支持的 ROS2 发行版

- **ROS2 Humble Hawksbill** (Ubuntu 22.04 LTS)
- **ROS2 Jazzy Jalisco** (Ubuntu 24.04 LTS)

### 版本验证

安装后，验证您的 ROS2 设置：

```bash
# Source ROS2 environment
source /opt/ros/$ROS_DISTRO/setup.bash

# Check ROS2 version
ros2 doctor
```

### 后续步骤

在确认 ROS2 兼容性后，请继续查看 [Getting Started](../../1-start/README.md) 以进行安装。