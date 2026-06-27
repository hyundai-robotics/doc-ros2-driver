# 3.4.3 文件管理服务

### 概述

由 `hdr_ros2_driver` 提供的与文件管理相关的 ROS2 服务。

### 文件管理服务

#### 文件查询和信息

```bash
# 获取文件内容
ros2 service call /hdr_ros2_driver/file/get/files hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"

# 获取目录中的文件列表
ros2 service call /hdr_ros2_driver/file/get/file_list hdr_msgs/srv/FileList "{path: 'project/jobs', incl_file: true, incl_dir: false}"

# 获取文件信息
ros2 service call /hdr_ros2_driver/file/get/file_info hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"

# 检查文件是否存在
ros2 service call /hdr_ros2_driver/file/get/file_exist hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"
```

#### 文件操作

```bash
# 上传文件
ros2 service call /hdr_ros2_driver/file/post/files hdr_msgs/srv/FileSend "{target_file: 'project/jobs/test.job', source_file: '/home/test/test.job'}"

# 创建目录
ros2 service call /hdr_ros2_driver/file/post/mkdir hdr_msgs/srv/FilePath "{path: 'project/jobs/special'}"

# 重命名文件
ros2 service call /hdr_ros2_driver/file/post/rename_file hdr_msgs/srv/FileRename "{pathname_from: 'project/jobs/0001.job', pathname_to: 'project/jobs/4321.job'}"

# 删除文件
ros2 service call /hdr_ros2_driver/file/delete/files hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"
```