# 3.4 ROS2 驱动服务

### 概述

`hdr_ros2_driver` 提供多种 ROS2 服务用于与 HD 现代机器人 Hi6 控制器进行通信。

### 服务类别

| 类别 | 描述 |
|----------|-------------|
| **[控制服务](1-control/README.md)** | 机器人控制，电机电源，应急停止，坐标系统，I/O 管理 |
| **[任务管理](2-task/README.md)** | 变量赋值，运动执行，程序控制 |
| **[文件管理](3-file/README.md)** | 文件上传/下载，目录操作 |
| **[PLC 通信](4-plc/README.md)** | PLC 继电器值控制 |
| **[控制台命令](5-console/README.md)** | 控制台命令执行，系统时间，日志管理 |
| **[项目管理](6-project/README.md)** | 作业信息，作业删除/重载 |
| **[版本信息](7-version/README.md)** | API 版本，系统版本查询 |

### 基本用法

#### 检查服务列表
```bash
# 列出所有 HDR 驱动服务
ros2 service list | grep hdr_ros2_driver
```

#### 常见服务调用
```bash
# 检查 API 版本
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger

# 检查电机状态
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# 打开电机电源
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger
```