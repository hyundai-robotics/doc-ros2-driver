# 3.4.6 项目管理服务

### 概述

由 `hdr_ros2_driver` 提供的与项目和作业管理相关的 ROS2 服务。

### 项目管理服务

#### 作业信息

```bash
# 获取作业信息
ros2 service call /hdr_ros2_driver/project/get/jobs_info std_srvs/srv/Trigger

# 获取机器人生成信息
ros2 service call /hdr_ros2_driver/project/get/rgen std_srvs/srv/Trigger
```

#### 作业操作

```bash
# 删除作业
ros2 service call /hdr_ros2_driver/project/post/delete_job hdr_msgs/srv/FilePath "{path: '0001.job'}"

# 重新加载更新的作业
ros2 service call /hdr_ros2_driver/project/post/reload_updated_jobs std_srvs/srv/Trigger
```