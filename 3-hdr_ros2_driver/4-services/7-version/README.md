# 3.4.7 Version Information Services

### Overview

Version information related ROS2 services provided by `hdr_ros2_driver`.

### Version Information Services

#### System Version Queries

```bash
# Get API version
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger

# Get system version
ros2 service call /hdr_ros2_driver/get/system_ver std_srvs/srv/Trigger
```
