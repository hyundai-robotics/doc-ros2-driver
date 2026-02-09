# 3.4.1 로봇 제어 서비스

### 개요

`hdr_ros2_driver`에서 제공하는 로봇 제어 관련 ROS2 서비스입니다.

### 로봇 제어 서비스

#### 모터 상태 및 제어

```bash
# 모터 상태 조회
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# 모터 전원 켜기
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger

# 비상 정지
ros2 service call /hdr_ros2_driver/robot/post/emergency_stop std_srvs/srv/Trigger
```

#### 위치 및 도구 관리

```bash
# 현재 로봇 위치 조회
ros2 service call /hdr_ros2_driver/robot/get/po_cur hdr_msgs/srv/PoseCur

# 현재 tool 정보 조회
ros2 service call /hdr_ros2_driver/robot/get/cur_tool std_srvs/srv/Trigger

# 사용 가능한 tool 목록 조회
ros2 service call /hdr_ros2_driver/robot/get/tools std_srvs/srv/Trigger

# 특정 tool 정보 조회
ros2 service call /hdr_ros2_driver/robot/get/tools_t hdr_msgs/srv/Number "{data: 0}"

# tool 번호 설정
ros2 service call /hdr_ros2_driver/robot/post/tool_no hdr_msgs/srv/Number "{data: 0}"

# 좌표계 설정
ros2 service call /hdr_ros2_driver/robot/post/crd_sys hdr_msgs/srv/Number "{data: 0}"
```

### 시스템 제어 서비스

#### 작동 조건

```bash
# 작동 조건 조회
ros2 service call /hdr_ros2_driver/control/get/op_cnd std_srvs/srv/Trigger

# 작동 조건 설정
ros2 service call /hdr_ros2_driver/control/put/op_cnd hdr_msgs/srv/OpCnd "{playback_mode: 1, step_goback_max_spd: 130, ucrd_num: 2}"

# 사용자 좌표계 번호 조회
ros2 service call /hdr_ros2_driver/control/get/ucs_nos std_srvs/srv/Trigger
```

#### 디지털 I/O

```bash
# 디지털 입력 읽기
ros2 service call /hdr_ros2_driver/control/get/ios/di hdr_msgs/srv/IoRequest "{type: 'di', blk_no: 1, sig_no: 1}"

# 디지털 출력 읽기
ros2 service call /hdr_ros2_driver/control/get/ios/do hdr_msgs/srv/IoRequest "{type: 'do', blk_no: 1, sig_no: 1}"

# 시리얼 I/O 읽기
ros2 service call /hdr_ros2_driver/control/get/ios/sio hdr_msgs/srv/IoRequest "{type: 'sio', blk_no: 1, sig_no: 1}"

# 디지털 I/O 설정
ros2 service call /hdr_ros2_driver/control/post/ios/dio hdr_msgs/srv/IoRequest "{type: 'do', blk_no: 1, sig_no: 1, val: 1}"
```
