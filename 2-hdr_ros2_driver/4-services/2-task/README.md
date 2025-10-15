# Task Management Services

## Overview

Task and variable management related ROS2 services provided by `hdr_ros2_driver`.

## Task Management Services

### Variable Management

```bash
# Assign variable
ros2 service call /hdr_ros2_driver/task/post/assign_var hdr_msgs/srv/ProgramVar "{name: 'a', scope: 'local', expr: '14 + 2', save: 'true'}"

# Solve expression
ros2 service call /hdr_ros2_driver/task/post/solve_expr hdr_msgs/srv/ProgramVar "{name: 'a', scope: 'local'}"
```

### Motion Control

```bash
# Execute move command
ros2 service call /hdr_ros2_driver/task/post/execute_move hdr_msgs/srv/ExecuteMove "{task_no: 0, stmt: 'move SP,spd=1sec,accu=0,tool=1 [0, 90, 0, 0, 0, 0]'}"

# Release wait state
ros2 service call /hdr_ros2_driver/task/post/release_wait std_srvs/srv/Trigger

# Set program counter index
ros2 service call /hdr_ros2_driver/task/post/set_cur_pc_idx hdr_msgs/srv/Number "{data: 0}"
```