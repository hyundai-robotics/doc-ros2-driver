# 3.4.1 机器人控制服务

### 概述

由 `hdr_ros2_driver` 提供的与机器人控制相关的 ROS2 服务。

### 机器人控制服务

#### 电机状态和控制

```bash
# 获取电机状态
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# 开启电机电源
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger

# 紧急停止
ros2 service call /hdr_ros2_driver/robot/post/emergency_stop std_srvs/srv/Trigger
```

#### 位置和工具管理

```bash
# 获取当前机器人位置
ros2 service call /hdr_ros2_driver/robot/get/po_cur hdr_msgs/srv/PoseCur

# 获取当前工具信息
ros2 service call /hdr_ros2_driver/robot/get/cur_tool std_srvs/srv/Trigger

# 获取可用工具列表
ros2 service call /hdr_ros2_driver/robot/get/tools std_srvs/srv/Trigger

# 获取特定工具信息
ros2 service call /hdr_ros2_driver/robot/get/tools_t hdr_msgs/srv/Number "{data: 0}"

# 设置工具编号
ros2 service call /hdr_ros2_driver/robot/post/tool_no hdr_msgs/srv/Number "{data: 0}"

# 设置坐标系
ros2 service call /hdr_ros2_driver/robot/post/crd_sys hdr_msgs/srv/Number "{data: 0}"
```

### 系统控制服务

#### 操作条件

```bash
# 获取操作条件
ros2 service call /hdr_ros2_driver/control/get/op_cnd std_srvs/srv/Trigger

# 设置操作条件
ros2 service call /hdr_ros2_driver/control/put/op_cnd hdr_msgs/srv/OpCnd "{playback_mode: 1, step_goback_max_spd: 130, ucrd_num: 2}"

# 获取用户坐标系编号
ros2 service call /hdr_ros2_driver/control/get/ucs_nos std_srvs/srv/Trigger
```
#### 数字 I/O

```bash
# 读取数字输入
ros2 service call /hdr_ros2_driver/control/get/ios/di hdr_msgs/srv/IoRequest "{type: 'di', blk_no: 1, sig_no: 1}"

# 读取数字输出
ros2 service call /hdr_ros2_driver/control/get/ios/do hdr_msgs/srv/IoRequest "{type: 'do', blk_no: 1, sig_no: 1}"

# 读取串行 I/O
ros2 service call /hdr_ros2_driver/control/get/ios/sio hdr_msgs/srv/IoRequest "{type: 'sio', blk_no: 1, sig_no: 1}"

# 设置数字 I/O
ros2 service call /hdr_ros2_driver/control/post/ios/dio hdr_msgs/srv/IoRequest "{type: 'do', blk_no: 1, sig_no: 1, val: 1}"
```