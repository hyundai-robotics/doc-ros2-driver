# ros2_control 시스템 실행

## 개요

HD현대로보틱스 로봇을 위한 ros2_control 시스템의 기본 실행 방법을 설명합니다.

## 기본 실행

### ros2_control 실행
```bash
# 기본 실행
ros2 launch hdr_hardware_interface hdr_control.launch.py robot_model:=ha006b

# IP 주소 지정
ros2 launch hdr_hardware_interface hdr_control.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150

# 시뮬레이션 모드
ros2 launch hdr_hardware_interface hdr_control.launch.py \
    robot_model:=ha006b \
    use_sim_time:=true
```

## 제어기

### 제어기 상태 확인
```bash
# 제어기 목록 보기
ros2 control list_controllers

# 하드웨어 인터페이스 확인
ros2 control list_hardware_interfaces

# 조인트 상태 확인
ros2 topic echo /joint_states
```

### 제어기 활성화/비활성화
```bash
# 제어기 활성화
ros2 control switch_controllers --activate joint_trajectory_controller

# 제어기 비활성화
ros2 control switch_controllers --deactivate joint_trajectory_controller
```

## 기본 제어기 설정

ros2_control은 다음 제어기들을 제공합니다:

- **joint_state_broadcaster**: 조인트 상태 발행
- **joint_trajectory_controller**: 궤적 추종 제어

## 간단한 테스트

### 조인트 궤적 테스트
```bash
# 간단한 조인트 이동 테스트
ros2 action send_goal /joint_trajectory_controller/follow_joint_trajectory \
    control_msgs/action/FollowJointTrajectory \
    "{
      trajectory: {
        joint_names: ['j1', 'j2', 'j3', 'j4', 'j5', 'j6'],
        points: [
          {
            positions: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
            time_from_start: {sec: 2}
          }
        ]
      }
    }"
```

## 문제 해결

### 일반적인 문제

**제어기가 시작되지 않는 경우:**
- 로봇 제어기가 REMOTE 모드인지 확인
- 네트워크 연결 확인
- 로봇이 비상 정지 상태가 아닌지 확인

**조인트 상태가 발행되지 않는 경우:**
- 하드웨어 인터페이스 연결 상태 확인
- 로봇 제어기 상태 확인

**궤적 실행 실패:**
- 조인트 한계값 확인
- 목표 위치가 유효한지 확인
- 제어기 오류 메시지 확인


## 안전 주의사항

- 실제 로봇과 작업할 때는 항상 비상 정지 버튼을 접근 가능한 곳에 두세요
- 로봇이 예상치 못한 동작을 할 경우 즉시 비상 정지하세요
- 처음 사용할 때는 낮은 속도로 테스트하세요