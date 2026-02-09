# 3.4.5 콘솔 명령 서비스

### 개요

`hdr_ros2_driver`에서 제공하는 콘솔 명령 및 시스템 관리 관련 ROS2 서비스입니다.

### 콘솔 명령 서비스

#### 명령 실행

```bash
# 콘솔 명령 실행
ros2 service call /hdr_ros2_driver/console/post/execute_cmd hdr_msgs/srv/ExecuteCmd "{cmd_line: 'rl.stop'}"

# 로봇 작업 실행 제어 (시작/중지)
ros2 service call /hdr_ros2_driver/console/post/operation std_srvs/srv/SetBool "data: true"
```

### 시스템 정보 서비스

#### 날짜 및 시간

```bash
# 시스템 날짜 및 시간 가져오기
ros2 service call /hdr_ros2_driver/clock/get/date_time std_srvs/srv/Trigger

# 시스템 날짜 및 시간 설정
ros2 service call /hdr_ros2_driver/clock/put/date_time hdr_msgs/srv/DateTime "{year: 2025, month: 5, day: 13, hour: 14, minute: 30, second: 0}"
```

#### 로그 관리

```bash
# 로그 관리자 정보 가져오기
ros2 service call /hdr_ros2_driver/log/get/manager hdr_msgs/srv/LogManager "{n_item: 50, cat_p: 'E,W,N', id_min: 0, ts_min: '2025/05/01 00:00:00.000', ts_max: '2025/05/13 23:59:59.999'}"
```
