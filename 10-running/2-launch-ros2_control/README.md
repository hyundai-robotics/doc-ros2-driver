# 10.2 ros2_control 系统执行

### 概述

解释 HD 现代机器人机器人的 ros2_control 系统的基本执行方法。

### 基本执行

#### 启动 ros2_control
```bash
# 基本启动
ros2 launch hdr_bringup hdr_control.launch.py robot_model:=ha006b

# 指定 IP 地址
ros2 launch hdr_bringup hdr_control.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

### 控制器

#### 检查控制器状态
```bash
# 列出控制器
ros2 control list_controllers

# 检查硬件接口
ros2 control list_hardware_interfaces

# 检查关节状态
ros2 topic echo /joint_states
```

#### 激活/停用控制器
```bash
# 激活控制器
ros2 control switch_controllers --activate joint_trajectory_controller 

# 停用控制器
ros2 control switch_controllers --deactivate joint_trajectory_controller
```

### 默认控制器配置

ros2_control 提供以下控制器：

- **joint_state_broadcaster**: 发布关节状态
- **joint_trajectory_controller**: 轨迹跟随控制

### 简单测试
#### 关节轨迹测试
```bash
# 简单关节运动测试
ros2 action send_goal /joint_trajectory_controller/follow_joint_trajectory \
    control_msgs/action/FollowJointTrajectory \
    "{
      trajectory: {
        joint_names: ['j1', 'j2', 'j3', 'j4', 'j5', 'j6'],
        points: [
          {
            positions: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
            time_from_start: {sec: 2}
          }
        ]
      }
    }"
```

### 故障排除

#### 常见问题

**连接问题**
- 验证网络连接: `ping 192.168.1.150`
- 确认机器人控制器处于远程模式

**当控制器无法启动时：**
- 验证机器人控制器处于远程模式
- 检查网络连接
- 确认机器人不处于紧急停止状态

**当关节状态未发布时：**
- 检查硬件接口连接状态
- 验证机器人控制器状态

**轨迹执行失败：**
- 检查关节限制
- 验证目标位置是否有效
- 检查控制器错误消息

#### 当机器人不在电机开启和启动模式下操作时
**正常操作**
当两个**电机开启**和**启动模式**都启用时，机器人正常操作。

**当机器人不操作时**
如果在启用**电机开启**的情况下没有激活启动模式，系统将生成错误 "外部命令操作被禁用 (E01554)"。
如果给出不合理的命令值（例如，超出物理限制），可能会发生轴过速错误，导致机器人停止。
在这种情况下，可以通过重新激活**电机开启 + 启动模式**来恢复系统。
### 安全注意事项

- 在实际操作机器人时，始终保持紧急停止按钮可及
- 如果机器人出现意外行为，立即进行紧急停止
- 第一次使用时应以低速进行测试