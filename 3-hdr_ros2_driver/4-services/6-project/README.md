# 3.4.6 项目管理服务

### 概述

由 `hdr_ros2_driver` 提供的项目和工作管理相关的 ROS2 服务。

### 项目管理服务

#### 工作信息

```bash
# 获取工作信息
ros2 service call /hdr_ros2_driver/project/get/jobs_info std_srvs/srv/Trigger

# 获取机器人生成信息
ros2 service call /hdr_ros2_driver/project/get/rgen std_srvs/srv/Trigger
```

#### 工作操作

```bash
# 删除工作
ros2 service call /hdr_ros2_driver/project/post/delete_job hdr_msgs/srv/FilePath "{path: '0001.job'}"

# 重新加载更新的工作
ros2 service call /hdr_ros2_driver/project/post/reload_updated_jobs std_srvs/srv/Trigger
```