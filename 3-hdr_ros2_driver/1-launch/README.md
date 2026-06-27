# 3.1 HDR ROS2 Driver 启动

本节介绍如何启动 HDR ROS2 驱动程序。

### 基本启动

#### HDR ROS2 驱动程序启动
```bash
# 使用默认参数启动
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py
```

这将使用以下配置启动驱动程序：
- 默认 IP：192.168.1.150
- 默认端口：8888

### 验证

启动后，验证驱动程序是否正在运行：

```bash
# 检查驱动节点是否处于活动状态
ros2 node list | grep hdr_ros2_driver

# 列出可用服务
ros2 service list | grep hdr_ros2_driver

# 测试基本连接
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger
```

### 网络设置前提条件

在启动之前，请确保正确的网络配置：

1. **以太网连接**：通过 LAN1、LAN2 或 LAN3 将 PC 连接到机器人控制器
2. **控制器 IP**：默认 192.168.1.150（通过教学挂件可配置）
3. **PC IP**：设置为 192.168.1.x 范围（x ≠ 150）
4. **REMOTE 模式**：确保机器人控制器处于 REMOTE 模式

### 故障排除

#### 常见问题

1. **连接超时**
   - 验证机器人 IP 和端口：`ping 192.168.1.150`
   - 检查以太网电缆连接

2. **服务不可用**
   - 验证驱动程序成功启动
   - 检查 ROS2 环境是否已导入
   - 检查启动输出是否有错误信息
   - 确保机器人处于 REMOTE 模式
   - 验证控制器软件版本为 **70.00-00** 或更高