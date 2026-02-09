# 3.4.2 작업 관리 서비스

### 개요

`hdr_ros2_driver`에서 제공하는 작업 및 변수 관리 관련 ROS2 서비스입니다.

### 작업 관리 서비스

#### 변수 관리

```bash
# 변수 할당
ros2 service call /hdr_ros2_driver/task/post/assign_var hdr_msgs/srv/ProgramVar "{name: 'a', scope: 'local', expr: '14 + 2', save: 'true'}"

# 표현식 해결
ros2 service call /hdr_ros2_driver/task/post/solve_expr hdr_msgs/srv/ProgramVar "{name: 'a', scope: 'local'}"
```

#### 동작 제어

```bash
# 동작 명령 실행
ros2 service call /hdr_ros2_driver/task/post/execute_move hdr_msgs/srv/ExecuteMove "{task_no: 0, stmt: 'move SP,spd=1sec,accu=0,tool=1 [0, 90, 0, 0, 0, 0]'}"

# 대기 상태 해제
ros2 service call /hdr_ros2_driver/task/post/release_wait std_srvs/srv/Trigger

# 프로그램 카운터 인덱스 설정
ros2 service call /hdr_ros2_driver/task/post/set_cur_pc_idx hdr_msgs/srv/Number "{data: 0}"
```
