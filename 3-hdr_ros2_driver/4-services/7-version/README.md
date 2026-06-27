# 3.4.7 版本信息服务

### 概述

与 `hdr_ros2_driver` 提供的 ROS2 服务相关的版本信息。

### 版本信息服务

#### 系统版本查询

```bash
# 获取 API 版本
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger

# 获取系统版本
ros2 service call /hdr_ros2_driver/get/system_ver std_srvs/srv/Trigger
```