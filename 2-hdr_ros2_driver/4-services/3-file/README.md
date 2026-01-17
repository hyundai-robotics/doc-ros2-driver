# File Management Services

## Overview

File management related ROS2 services provided by `hdr_ros2_driver`.

## File Management Services

### File Query and Information

```bash
# Get file contents
ros2 service call /hdr_ros2_driver/file/get/files hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"

# Get file list in directory
ros2 service call /hdr_ros2_driver/file/get/file_list hdr_msgs/srv/FileList "{path: 'project/jobs', incl_file: true, incl_dir: false}"

# Get file information
ros2 service call /hdr_ros2_driver/file/get/file_info hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"

# Check file existence
ros2 service call /hdr_ros2_driver/file/get/file_exist hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"
```

### File Operations

```bash
# Upload file
ros2 service call /hdr_ros2_driver/file/post/files hdr_msgs/srv/FileSend "{target_file: 'project/jobs/test.job', source_file: '/home/test/test.job'}"

# Create directory
ros2 service call /hdr_ros2_driver/file/post/mkdir hdr_msgs/srv/FilePath "{path: 'project/jobs/special'}"

# Rename file
ros2 service call /hdr_ros2_driver/file/post/rename_file hdr_msgs/srv/FileRename "{pathname_from: 'project/jobs/0001.job', pathname_to: 'project/jobs/4321.job'}"

# Delete file
ros2 service call /hdr_ros2_driver/file/delete/files hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"
```