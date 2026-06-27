# 2.4 安装验证

本指南提供验证程序，以确认 HD Hyundai Robotics ROS2 驱动程序已正确安装、配置并准备好操作。

#### 机器人模式配置

HDR ROS2 驱动程序仅在机器人处于 **REMOTE** 模式时才能工作。

请在运行 ROS2 驱动程序之前，通过将教学挂件 (TP) 上的模式开关切换到 REMOTE 位置来将控制器设置为遥控模式。

![](../../_assets/tp_operate.png)


#### HDR ROS2 驱动程序执行测试

```bash
# 运行 HDR ROS2 驱动程序（确保机器人处于 REMOTE 模式）
ros2 launch hdr_bringup hdr_control.py \
  robot_model:=hdf7_7      # 输入机器人模型（默认：ha006b）


# 在另一个终端验证控制器管理器
ros2 control list_controllers

# 预期输出：
# joint_state_broadcaster[joint_state_broadcaster/JointStateBroadcaster] active
# joint_trajectory_controller[joint_trajectory_controller/JointTrajectoryController] active
```

#### 关节状态发布测试

```bash
# 验证关节状态是否正在发布
ros2 topic list | grep joint_states

# 监控关节状态
ros2 topic echo /joint_states --once

# 检查发布频率
ros2 topic hz /joint_states
```