# 3.4.5 控制台命令服务

### 概述

由 `hdr_ros2_driver` 提供的与控制台命令和系统管理相关的 ROS2 服务。

### 控制台命令服务

#### 命令执行

```bash
# 执行控制台命令
ros2 service call /hdr_ros2_driver/console/post/execute_cmd hdr_msgs/srv/ExecuteCmd "{cmd_line: 'rl.stop'}"

# 机器人任务执行控制（开始/停止）
ros2 service call /hdr_ros2_driver/console/post/operation std_srvs/srv/SetBool "data: true"
```

### 系统信息服务

#### 日期和时间

```bash
# 获取系统日期和时间
ros2 service call /hdr_ros2_driver/clock/get/date_time std_srvs/srv/Trigger

# 设置系统日期和时间
ros2 service call /hdr_ros2_driver/clock/put/date_time hdr_msgs/srv/DateTime "{year: 2025, month: 5, day: 13, hour: 14, minute: 30, second: 0}"
```

#### 日志管理

```bash
# 获取日志管理器信息
ros2 service call /hdr_ros2_driver/log/get/manager hdr_msgs/srv/LogManager "{n_item: 50, cat_p: 'E,W,N', id_min: 0, ts_min: '2025/05/01 00:00:00.000', ts_max: '2025/05/13 23:59:59.999'}"
```