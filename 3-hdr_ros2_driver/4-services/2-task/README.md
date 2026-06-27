# 3.4.2 任务管理服务

### 概述

由 `hdr_ros2_driver` 提供的与任务和变量管理相关的 ROS2 服务。

### 任务管理服务

#### 变量管理

```bash
# 指派变量
ros2 service call /hdr_ros2_driver/task/post/assign_var hdr_msgs/srv/ProgramVar "{name: 'a', scope: 'local', expr: '14 + 2', save: 'true'}"

# 解决表达式
ros2 service call /hdr_ros2_driver/task/post/solve_expr hdr_msgs/srv/ProgramVar "{name: 'a', scope: 'local'}"
```

#### 动作控制

```bash
# 执行移动命令
ros2 service call /hdr_ros2_driver/task/post/execute_move hdr_msgs/srv/ExecuteMove "{task_no: 0, stmt: 'move SP,spd=1sec,accu=0,tool=1 [0, 90, 0, 0, 0, 0]'}"

# 释放等待状态
ros2 service call /hdr_ros2_driver/task/post/release_wait std_srvs/srv/Trigger

# 设置程序计数器索引
ros2 service call /hdr_ros2_driver/task/post/set_cur_pc_idx hdr_msgs/srv/Number "{data: 0}"
```