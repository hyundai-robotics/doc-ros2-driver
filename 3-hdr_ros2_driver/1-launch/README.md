# 3.1 HDR ROS2 驱动程序启动

本节介绍如何启动 HDR ROS2 驱动程序。

### 基本启动

#### HDR ROS2 驱动程序启动
```bash
# 使用默认参数启动
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py
```

这将启动驱动程序，使用：
- 默认 IP：192.168.1.150
- 默认端口：8888

### 自定义配置

#### 自定义 IP 和端口
```bash
# 使用自定义网络设置启动
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py \
  openapi_ip:=192.168.0.10 \
  openapi_port:=8080
```

### 启动参数

| 参数 | 类型 | 默认 | 描述 |
|------|------|------|------|
| `openapi_ip` | 字符串 | `192.168.1.150` | 机器人控制器服务器 IP 地址 |
| `openapi_port` | 整数 | `8888` | 控制器服务器端口编号 |
| `robot_model` | 字符串 | `ha006b` | 机器人型号名称 |

### 验证

启动后，验证驱动程序是否正在运行：

```bash
# 检查驱动程序节点是否活动
ros2 node list | grep hdr_ros2_driver

# 列出可用服务
ros2 service list | grep hdr_ros2_driver

# 测试基本连接
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger
```

### 网络设置前提条件
在启动之前，请确保正确的网络配置：

1. **以太网连接**：通过LAN1、LAN2或LAN3将PC连接到机器人控制器
2. **控制器IP**：默认192.168.1.150（可通过教学挂件配置）
3. **PC IP**：设置为192.168.1.x范围（x ≠ 150）
4. **远程模式**：确保机器人控制器处于远程模式

### 故障排除

#### 常见问题

1. **连接超时**
   - 验证机器人IP和端口：`ping 192.168.1.150`
   - 检查以太网电缆连接

2. **服务不可用**
   - 验证驱动程序是否成功启动
   - 检查ROS2环境是否已被引入
   - 检查启动输出中的错误信息
   - 确保机器人处于远程模式
   - 验证控制器软件版本为**60.32-00**或更高