# Console Command Services

## Overview

Console command and system management related ROS2 services provided by `hdr_ros2_driver`.

## Console Command Services

### Command Execution

```bash
# Execute console command
ros2 service call /hdr_ros2_driver/console/post/execute_cmd hdr_msgs/srv/ExecuteCmd "{cmd_line: 'rl.stop'}"

# Robot task execution control (start/stop)
ros2 service call /hdr_ros2_driver/console/post/operation std_srvs/srv/SetBool "data: true"
```

## System Information Services

### Date and Time

```bash
# Get system date and time
ros2 service call /hdr_ros2_driver/clock/get/date_time std_srvs/srv/Trigger

# Set system date and time
ros2 service call /hdr_ros2_driver/clock/put/date_time hdr_msgs/srv/DateTime "{year: 2025, month: 5, day: 13, hour: 14, minute: 30, second: 0}"
```

### Log Management

```bash
# Get log manager information
ros2 service call /hdr_ros2_driver/log/get/manager hdr_msgs/srv/LogManager "{n_item: 50, cat_p: 'E,W,N', id_min: 0, ts_min: '2025/05/01 00:00:00.000', ts_max: '2025/05/13 23:59:59.999'}"
```