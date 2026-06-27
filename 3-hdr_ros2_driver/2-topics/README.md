# 3.2 提供的主题

### 概述

ROS2 驱动程序通过标准化的 ROS2 主题发布实时机器人数据。这些主题提供关节状态、机器人状态信息和用于监控和控制应用的诊断数据。

### 发布的主题

#### 关节状态信息

##### `/joint_states` (sensor_msgs/msg/JointState)
**描述**：实时关节位置数据

**消息字段**：
```yaml
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
string[] name          # 与 URDF 匹配的关节名称
float64[] position     # 以弧度表示的关节位置
float64[] velocity     # 以弧度/秒表示的关节速度
float64[] effort       # 以扭矩表示的关节努力
```

**发布频率**：50 Hz（可通过 `publish_rate` 参数配置）