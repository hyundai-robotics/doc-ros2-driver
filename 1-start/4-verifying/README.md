# 설치 검증

본 가이드는 HD현대로보틱스 ROS2 드라이버가 올바르게 설치, 구성되고 작동할 준비가 되었는지 확인하는 포괄적인 검증 절차를 제공합니다.

### HDR 드라이버 실행 테스트

```bash
# HDR ROS2 드라이버 실행 (로봇이 REMOTE 모드에 있는지 확인)
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py \
  openapi_ip:=192.168.1.150 \
  openapi_port:=8888

```

## 하드웨어 인터페이스 검증

### ros2_control 통합 테스트

```bash
# 하드웨어 인터페이스 실행
ros2 launch hdr_hardware_interface ros2_control.launch.py \
  robot_model:=ha006b \
  openapi_ip:=192.168.1.150 \
  openapi_port:=8888

# 다른 터미널에서 controller 매니저 확인
ros2 control list_controllers

# 예상 출력:
# joint_state_broadcaster[joint_state_broadcaster/JointStateBroadcaster] active
# joint_trajectory_controller[joint_trajectory_controller/JointTrajectoryController] active
```

### 조인트 상태 발행 테스트

```bash
# 조인트 상태가 발행되고 있는지 확인
ros2 topic list | grep joint_states

# 조인트 상태 모니터링
ros2 topic echo /joint_states --once

# 발행 빈도 확인
ros2 topic hz /joint_states
```

### controller 로딩 테스트

```bash
# 조인트 궤적 controller 로드
ros2 control load_controller joint_trajectory_controller

# controller 구성 및 시작
ros2 control set_controller_state joint_trajectory_controller configure
ros2 control set_controller_state joint_trajectory_controller start

# controller가 활성 상태인지 확인
ros2 control list_controllers
```