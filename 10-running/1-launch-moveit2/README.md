# 10.1 使用 MoveIt2 运作

### 概述

使用 MoveIt2 运行 HD Hyundai Robotics 机器人的基本程序。

### 启动前准备

#### 硬件准备
- 开启机器人控制器并设置为远程模式
- 确保紧急停止按钮可达
- 验证网络连接（ping 192.168.1.150）
- 确认工作空间没有障碍物

#### 软件准备
- 设置 ROS2 环境：`source ~/ros2_ws/install/setup.bash`
- 验证机器人模型

### 基本启动程序

#### 1. 启动 MoveIt2
```bash
# 基本 MoveIt2 启动
ros2 launch hdr_moveit_config hdr_moveit.launch.py robot_model:=ha006b

# 使用指定 IP 地址启动
ros2 launch hdr_moveit_config hdr_moveit.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

#### 2. 验证连接状态
```bash
# 检查关节状态
ros2 topic echo /joint_states --once

# 检查 MoveIt2 服务
ros2 service list | grep move_group
```

### 支持的机器人模型

- ha006b
- hdf7_9
- hdf8_8
- hdr10l_19
- hdr20_17
- hdr50_22
- hdr220_26
- hh020
- hdr35_20

### 安全注意事项

#### 紧急停止
- 始终保持硬件紧急停止按钮可达

#### 安全关机
1. 停止所有运动
2. 将机器人移动到安全位置
3. 终止 MoveIt2 节点
4. 关闭机器人控制器电源

### 常见故障排除

**连接问题**
- 验证网络连接：`ping 192.168.1.150`
- 确认机器人控制器处于远程模式

**当控制器无法启动时：**
- 验证机器人控制器处于远程模式
- 检查网络连接
- 确认机器人未处于紧急停止状态

**当关节状态未发布时：**
- 检查硬件接口连接状态
- 验证机器人控制器状态

**轨迹执行失败：**
- 检查关节限制
- 验证目标位置有效
- 检查控制器错误消息

#### 当机器人在电机开启和启动模式下不工作
**正常操作**
当同时启用 **Motor ON** 和 **Start Mode** 时，机器人正常运行。

**当机器人不工作**
如果在启用 **Motor ON** 时未激活 Start Mode，系统会生成错误 "外部命令操作已禁用 (E01554)。"
如果给出不可行的命令值（例如，超出物理限制），可能会发生轴超速错误，导致机器人停止。
在这种情况下，可以通过重新激活 **Motor ON + Start Mode** 来恢复系统。