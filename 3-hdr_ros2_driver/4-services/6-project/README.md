# 3.4.6 Project Management Services

### Overview

Project and job management related ROS2 services provided by `hdr_ros2_driver`.

### Project Management Services

#### Job Information

```bash
# Get job information
ros2 service call /hdr_ros2_driver/project/get/jobs_info std_srvs/srv/Trigger

# Get robot generation information
ros2 service call /hdr_ros2_driver/project/get/rgen std_srvs/srv/Trigger
```

#### Job Operations

```bash
# Delete job
ros2 service call /hdr_ros2_driver/project/post/delete_job hdr_msgs/srv/FilePath "{path: '0001.job'}"

# Reload updated jobs
ros2 service call /hdr_ros2_driver/project/post/reload_updated_jobs std_srvs/srv/Trigger
```
