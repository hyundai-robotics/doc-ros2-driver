# 3.4.4 PLC通信服务

### 概述

由`hdr_ros2_driver`提供的与PLC通信相关的ROS2服务。

### PLC通信服务

#### 继电器值控制

```bash
# 获取继电器值
ros2 service call /hdr_ros2_driver/plc/get/relay_value hdr_msgs/srv/IoplcGet "{name: 'M', st: 100, len: 10}"

# 设置继电器值
ros2 service call /hdr_ros2_driver/plc/post/relay_value hdr_msgs/srv/IoplcPost "{name: 'fb1.do0', value: 1}"
```